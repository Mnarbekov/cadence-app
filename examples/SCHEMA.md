> **All values in this directory are entirely fabricated for demonstration purposes.  
> No real user activity, biometric data, or personal history is present anywhere in these files.  
> Generated 2026-06-07. User identifier: `demo-user`.**

---

# Cadence App — Example Data Schema

Cadence stores its data as JSON files across four folders. Each file is named by date (and session ID where applicable). Below is a public-safe description of each file type and its key fields, adapted from the working schema while using synthetic names and values where needed.

---

## 1. `programs/YYYY-MM-DD.json` — Daily Training Program

Written by the Health Coach AI Agent before each session. The phone reads this on the `/today` screen.

| Field | Type | Description |
|---|---|---|
| `schema` | string | Discriminator literal: `"cadence.program/v1"` |
| `date` | string (date) | Local calendar date (Australia/Sydney timezone) |
| `session.type` | enum | Session category: `upper-push`, `upper-pull`, `lower`, `cycling`, `walk`, `rest`, `reroute`, `free` |
| `session.target_session_rpe` | int 1–10 | Coach's target exertion level for the session |
| `session.warmup` | string | Optional warmup routine slug (e.g. `back-safe-12-short`) |
| `session.movements[]` | array | Prescribed movements (omitted on walk/cycling/rest days) |
| `session.movements[].name` | string | Movement name (e.g. `"Goblet Squat"`) |
| `session.movements[].sets` | int | Number of prescribed sets |
| `session.movements[].target_reps` | string or int | Rep target, e.g. `"8-10"` or `12` |
| `session.movements[].target_load_kg` | number | Target weight in kilograms |
| `session.movements[].is_back_loaded` | boolean | Flags axial/spinal-loaded movements for coaching cues |
| `session.coach_notes` | string | Free-text coaching notes shown before the session begins |

**Example files:** `programs/2026-04-15.json` (lower-body weights), `programs/2026-04-17.json` (walk + ice bath recovery day)

---

## 2. `logs/YYYY-MM-DD.json` — Session Execution Log

Written by the user on the phone after completing a session. Records what was actually done.

| Field | Type | Description |
|---|---|---|
| `schema` | string | `"cadence.log/v1"` |
| `session_id` | string (8-char hex) | Unique session identifier; links to the paired check-in |
| `captured_at` | string (datetime UTC) | UTC timestamp of the post-session reflection save |
| `program_ref` | string or null | Path of the program file this log responds to, or `null` for free sessions |
| `movements[]` | array | Movements actually performed (empty array on walk/cycling days) |
| `movements[].name` | string | Movement name |
| `movements[].sets[]` | array | Each executed set |
| `movements[].sets[].weight_kg` | number | Load used (0 = bodyweight) |
| `movements[].sets[].reps` | int | Reps completed |
| `movements[].sets[].rpe` | int 1–10 | Perceived exertion for that set |
| `movements[].sets[].pain_flag` | object or null | `{region, severity, note}` if pain noted; `null` otherwise. `severity` is `green`/`amber`/`red` |
| `session_rpe` | int 1–10 | Overall session RPE self-rating |
| `note` | string | Free reflection note |
| `duration_min` | int | Session duration in minutes |
| `app_version` | string | App build version that wrote this file |

**Example files:** `logs/2026-04-15.json` (lower-body weights executed), `logs/2026-04-17.json` (walk session; ice bath logged separately as a quick-log)

---

## 3. `checkins/YYYY-MM-DD.json` — Pre-Session Check-In

Written at the start of a session ("Begin" tap on the phone). Captures subjective readiness before training.

| Field | Type | Description |
|---|---|---|
| `schema` | string | `"cadence.checkin/v1"` |
| `session_id` | string (8-char hex) | Must match the paired session log's `session_id` |
| `captured_at` | string (datetime UTC) | UTC timestamp of the Begin tap |
| `sleep.hours` | number | Hours of sleep (manual entry; 2 decimal places) |
| `sleep.quality` | int 1–5 | Sleep quality rating |
| `sleep.source` | enum | `"manual"` (v1); `"apple-health"` reserved for v2 |
| `mood` | int 1–5 | Pre-session mood (1 = rough, 5 = great) |
| `soreness` | string[] | Body-region slugs with soreness (e.g. `"right-quad"`, `"lower-back"`). Empty array = none |
| `readiness` | int 1–10 | Self-rated physical readiness to train |
| `app_version` | string | App build version |

**Example file:** `checkins/2026-04-16.json`

---

## 4. `quicklogs/YYYY-MM-DD.json` — Quick Log (Cardio / Recovery)

Ad-hoc entries for activities outside the structured program: ice bath, cycling, walking.

| Field | Type | Description |
|---|---|---|
| `schema` | string | `"cadence.quicklog/v1"` |
| `captured_at` | string (datetime UTC) | UTC timestamp when logged |
| `kind` | enum | `"ice-bath"`, `"cycling"`, `"walking"`, `"other"` |
| `duration_min` | int | Duration in minutes |
| `metadata.temp_c` | int | Ice-bath water temperature in °C (ice-bath only) |
| `metadata.indoor` | boolean | Indoor trainer vs outdoor (cycling only) |
| `metadata.avg_hr_bpm` | int | Average heart rate from watch (cycling) |
| `metadata.intent` | enum | `"passive"` or `"intentional"` (walking only) |
| `metadata.label` | string | Required free-text label when `kind = "other"` |
| `rpe` | int 1–10 | Optional perceived exertion (cycling, other) |
| `note` | string | Optional free note |
| `app_version` | string | App build version |

**Example file:** `quicklogs/2026-04-18.json` (35 min indoor cycling, Zone 2)

---

## Tracked activity types

Cadence tracks exactly four activity types:

| Activity | Primary file type | Notes |
|---|---|---|
| **Weights** | `programs/` + `logs/` | Session type `upper-push`, `upper-pull`, or `lower`; movements carry set/rep/load detail |
| **Walking** | `programs/` + `logs/` or `quicklogs/` | Intentional walks may be prescribed or free-logged |
| **Cycling** | `programs/` + `logs/` or `quicklogs/` | Indoor or outdoor; heart rate optional |
| **Ice Bath** | `quicklogs/` | Duration + temperature; no movement structure needed |

---

## Disclaimer

> All JSON files in this `examples/` directory are **entirely fabricated synthetic data**.  
> Values were invented to illustrate schema shape and realistic field ranges.  
> No real user biometric data, training history, weight values, or timestamps are present.  
> The `_disclaimer` field in every JSON file restates this at machine-readable level.  
> Schema notes are adapted from the working app and rewritten for public-safe demonstration.
