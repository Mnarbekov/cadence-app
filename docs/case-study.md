# Cadence App — Case Study

## Problem

I need to stay healthy. That part is not optional. Cardio and weights are part of having energy for family and work.

But gyms never worked for me. I tried more than once. The commute, the fixed timetable, and the question of what to do each session made it hard to sustain.

The model that made more sense was a small home setup and a coach in my phone. To make that work, I needed a simple system: receive a plan, do the session, capture what happened, and carry that context into the next plan.

Most fitness apps are built around streaks, dashboards, and pressure. That was not what I wanted. I wanted a private, low-friction capture surface that supports a coaching loop.

## Why it mattered

Without a system, the loop breaks:

- the plan exists in one place and the session notes in another;
- effort, misses, and adjustments are forgotten before they can help the next decision;
- too many fields make the app something I avoid;
- private health and training details become hard to separate from public proof-of-work.

The product constraint was simple: make the useful action easier than skipping it.

## Product principles

1. **The app is the channel, not the coach.** It captures useful truth; the Health Coach AI Agent handles the assessment loop.
2. **Fast capture beats complete capture.** If a field does not help the next decision, it does not belong in the first version.
3. **Old-but-honest beats blank.** Cached content with a freshness signal is better than an empty screen.
4. **Private by default.** Public materials use synthetic examples only.
5. **No vanity metrics.** The point is continuity, not streak pressure.

## Solution

Cadence is built around a four-step loop:

1. **The Health Coach AI Agent prepares a plan** from the training context I choose to provide.
2. **I open Today** to see the current plan.
3. **I log the session**: completion, effort, notes, and anything that changed.
4. **The Health Coach AI Agent assesses the record** and writes back the next plan.

![Cadence phone session](../assets/screenshots/cadence-phone-session.png)

The app has four main surfaces:

- **Today:** current plan, notes, and freshness state.
- **Log:** quick capture for the session or activity.
- **History:** prior records without exposing raw private context in this showcase.
- **Settings:** account, cache, and operational controls away from the main loop.

Behind the scenes, small structured records are the handoff between the phone and the assessment step. The phone writes predictable records. The coaching loop reads them later and writes back the next plan.

## Where AI helped

AI tools helped me move from product intent to a working system faster by assisting with:

- turning workflow decisions into screens and data contracts;
- exploring implementation options;
- debugging mobile storage, caching, and sync edge cases;
- writing documentation and sanitization rules;
- challenging whether a feature helped the loop or added noise.

The human part stayed explicit: I chose the problem, judged the trade-offs, tested whether the workflow felt usable, and set the privacy boundary.

## Outcome

Safe-to-share outcomes:

- a working product pattern with a narrow, repeatable loop;
- synthetic example records for programs, logs, check-ins, and quick logs;
- an offline/local-first architecture shape that avoids blank-state failure;
- a public packaging approach that explains the project without exposing private data;
- evidence of AI-assisted builder skill: problem framing, product shaping, technical orchestration, testing, and refinement.

Private usage data, health details, and operational records are intentionally excluded from this showcase.

## What it proves

This project demonstrates that I can:

- identify a real-life workflow problem worth solving;
- reduce it to a focused product loop instead of overbuilding;
- guide AI-assisted implementation across app, data, and documentation layers;
- reason about privacy before publishing proof-of-work;
- turn a personal tool into a public-safe case study.

## Public privacy approach

Cadence handles personal training context, so the public version is deliberately separated from the private working system. The showcase explains the product pattern, AI-assisted workflow, and decision-making without exposing real activity records, health details, private notes, account details, or operational paths.

That privacy boundary is part of the product thinking, not a cleanup step at the end. The public materials use synthetic examples so the case study can be useful without turning personal context into portfolio content.
