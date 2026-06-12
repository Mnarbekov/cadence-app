# Cadence App — Architecture Notes

## Architecture summary

Cadence is a phone-first PWA for a simple coaching loop: show the current plan, capture what happened, keep useful local context, and support a later AI-assisted assessment step.

The architecture separates three concerns:

1. the phone app captures and displays the latest safe context;
2. structured private storage holds small records;
3. the Health Coach AI Agent assesses records later and prepares the next plan or note.

The public examples use synthetic fixtures instead of private records.

## System shape

![Cadence coaching loop diagram](../assets/diagrams/cadence-loop.png)

```text
[Phone PWA]
  |-- Today: read current plan / note / freshness state
  |-- Log: write session or quick activity records
  |-- History: inspect prior records
  |-- Settings: account/cache controls
        |
        v
[Local cache]
  |-- last-known-good plan/note
  |-- recent records for fast display
  |-- freshness metadata
        |
        v
[Private structured document store]
  |-- validated JSON-style records
  |-- predictable one-record-per-event shape
  |-- append-style records where practical
        |
        v
[Health Coach AI Agent]
  |-- receives selected training context
  |-- reads structured session records
  |-- applies coaching judgement and training principles
  |-- writes back next plan/note for the phone to display
```

## Key design decisions

### 1. Phone app as capture surface

The phone app is intentionally not the intelligence layer. It focuses on showing today's context and recording what happened with minimal friction.

### 2. Async loop instead of real-time coaching

The assessment happens later. That makes the workflow realistic: activity can be captured quickly in the moment, then assessed when there is time to think. It also keeps the AI-assisted step auditable rather than hidden inside an automatic black box.

### 3. Local cache and freshness signals

The app should not fail into a blank screen just because sync is slow or unavailable. It can show last-known-good content with an explicit freshness message. Degraded but honest is better than silently empty.

### 4. Structured records, not raw diary dumps

The app writes small structured records for the workflow it owns. Sensitive context that does not belong in the public showcase stays out of demo fixtures.

### 5. Privacy boundary designed up front

The public repository explains the pattern, not the private implementation. Screenshots, diagrams, and fixtures are synthetic or redacted.

## Components

| Component | Role | Public showcase treatment |
|---|---|---|
| Phone PWA | Daily capture and history surface | Describe screens and workflow; use demo screenshots only |
| Local cache | Keeps the app useful when network/sync is unavailable | Explain last-known-good and freshness; no real cached records |
| Structured document layer | Stores small validated records for handoff | Use synthetic JSON examples only |
| AI-assisted coaching loop | Reads selected training context and session records; returns next plan | Describe as private coaching loop; do not expose prompts, logs, personal data, or real health inputs |
| Data contracts | Keep phone writes predictable and auditable | Show simplified schemas or synthetic examples only |
| Public showcase package | Communicates proof-of-work safely | Include README, case study, architecture notes, examples, approved assets, and sanitization checklist |

## Data and privacy boundary

The public package describes the pattern without exposing the private working system. It excludes real activity logs, notes, check-ins, schedules, health records, account details, local paths, source files, private prompts, and operational endpoints.

Safe public substitutes:

- synthetic activity records and synthetic values;
- diagrams with generic labels like `Private document store` and `Coaching loop`;
- screenshots generated from demo fixtures only.

## Technology notes for public framing

The implementation can be described at a high level as a modern browser PWA with typed components, local browser storage, schema validation, private file sync, and an AI-assisted coaching workflow.

The public framing stays high level and avoids live service URLs, private app registrations, exact account details, operational paths, or private prompts.
