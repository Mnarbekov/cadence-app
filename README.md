# Cadence

A small phone app for home training: open it, see today's plan, do the session, log what happened. The next plan reflects what I actually did.

This repo is a demo-safe version. It explains how the app works and includes example data files, but no real training logs or health information.

## Why I built it

I train at home, and most fitness apps are either too heavy or built for the gym. I wanted something simple I would genuinely open every day: a clear plan for today, an easy way to log it, and a loop that adjusts to real life instead of a rigid program I'd quietly abandon.

Cadence is that app. It works together with an AI coaching step: the coach sets the plan, I do the training, Cadence captures what happened, and the next plan can use that record.

## What it does

- Shows today's plan the moment I open the app.
- Lets me log a session in a few taps.
- Keeps a simple history of what I've done.
- Feeds each session back so the next plan fits real life.
- Stays focused on a few activities I actually do: weights, walking, cycling, and ice baths.

## Screenshots and workflow

![Cadence phone screen showing today's session and quick logging](assets/screenshots/cadence-phone-session.png)

The phone session and quick-log screen, using demo content.

![The Cadence training loop, from plan to session to next plan](assets/diagrams/cadence-loop.png)

The loop: plan the week, train, capture the session, adjust the next plan.

## What's in this repo

- `examples/` — example program, session log, check-in, and quick-log files that show how Cadence stores a day's training (all made up).
- `examples/SCHEMA.md` — a plain description of what each record contains.
- `docs/architecture.md` — a short walkthrough of how the phone app and the coaching step fit together.

## Privacy

This is a demo-safe version. My real training logs, notes, and health context stay private and are not in this repo. The example records are invented.

## Built with AI assistance

I'm not a software developer. I decided what the app should do, how the daily loop should feel, and what to leave out, then used AI tools to help build it. The point is a practical tool I actually use, built by guiding AI rather than coding it all myself.

## Related

- Portfolio: https://www.mikhailnarbekov.com
- Medium story: [I used AI to build a training app I would actually use](https://medium.com/@mikhail.narbekov/i-used-ai-to-build-a-training-app-i-would-actually-use-30df337b2d9d)
- GitHub: https://github.com/Mnarbekov
