# How it works

Cadence is a phone-first app built around a simple loop: show today's plan, capture what happened, and feed that into the next plan.

```text
[Phone app]
  - Today: see the current plan
  - Log: record the session in a few taps
  - History: look back at past sessions
        |
        v
[Saved records]
  - one small file per session, plan, or quick log
  - kept on the device first, then synced privately
        |
        v
[AI coaching step]
  - reads the recent sessions
  - applies training judgement
  - writes back the next plan
```

## The main screens

- **Today** — the current plan and notes, ready the moment the app opens.
- **Log** — quick capture for a session or a single activity.
- **History** — a simple list of what's been done.

## A few design choices

1. **The app captures; the coaching step thinks.** The phone keeps things simple and records what happened. The planning happens in a separate step, not in real time.
2. **Fast to log beats complete.** If a field doesn't help the next plan, it doesn't belong in the first version.
3. **Old-but-clear beats blank.** If a sync is slow, the app shows the last known plan with a note about how fresh it is, rather than an empty screen.
4. **A few activities, done well.** Cadence focuses on weights, walking, cycling, and ice baths — the things that actually feed the loop.

## The example records

The `examples/` folder shows the small files Cadence saves — programs, session logs, check-ins, and quick logs. They're all made up, and `examples/SCHEMA.md` explains what each one contains.
