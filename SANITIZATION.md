# Cadence App — Sanitization Checklist

Use this checklist before publishing anything from this showcase. The goal is to prove the product thinking and AI-assisted builder workflow without exposing private life, health, account, or operational details.

## Public positioning rule

- [ ] First-person voice: "I designed", "I guided", "I tested".
- [ ] Honest AI-assisted framing: I own the problem, judgement, testing, and usefulness criteria; AI/tooling assists implementation and iteration.
- [ ] Idea-first explanation: focus on the workflow, product decisions, architecture pattern, and privacy boundary.
- [ ] No claim that the app was coded unaided.

## Never publish

- [ ] Private source code copied wholesale from production or personal repos.
- [ ] Real personal, family, health, finance, journal, schedule, message, or activity-log data.
- [ ] Health and training inputs used by the coaching loop, including wearable data, blood markers, body metrics, or personal health history. Public demo material must replace all of these with clearly synthetic values.
- [ ] Names, emails, account IDs, browser profiles, notifications, or identifiable screenshots.
- [ ] Credentials, API keys, tokens, cookies, `.env` files, local config, tenant/app IDs, or service secrets.
- [ ] Live service URLs, deployment URLs, workflow run links, or private operational endpoints.
- [ ] Local filesystem paths, cloud-storage paths, database filenames, export filenames, raw logs, or diagnostic artifacts.
- [ ] Prompts or AI transcripts that reveal private context.

## Screenshot safety

- [ ] Use demo data generated specifically for the showcase.
- [ ] Check that no browser/app chrome shows accounts, tabs, bookmarks, folders, notifications, or local paths.
- [ ] Replace private names and dates with generic labels.
- [ ] Save only final public-safe screenshots under `assets/screenshots/`.
- [ ] Add alt text that describes the workflow without private details.

## Diagram safety

- [ ] Use generic labels for private infrastructure and storage.
- [ ] Do not reveal exact folder structures, account providers, resource names, endpoints, or automation details.
- [ ] Show the privacy boundary as a feature, not an afterthought.

## Example-data safety

- [ ] Prefer simplified fixtures.
- [ ] Remove secrets, endpoints, private paths, real identifiers, and real timestamps.
- [ ] Use synthetic activity names and synthetic values.
- [ ] Do not copy full private source files.

## Safety search terms

Run a quick text search for obvious leaks, including:

- local drive patterns, user-folder names, and private project-root names;
- cloud-storage provider paths and provider-specific sync folders;
- `secret`, `token`, `api_key`, `apikey`, `password`, `credential`, `.env`, `client_id`, `tenant`;
- private names, emails, live URLs, and deployment hostnames.

A search hit is not automatically a blocker, but every hit must be checked before release.

## Public package checklist

- [ ] Check `README.md`, `docs/case-study.md`, and `docs/architecture.md` for private details.
- [ ] Confirm all examples and screenshots use demo data only.
- [ ] Confirm the project is framed as AI-assisted builder work.
- [ ] Confirm public-facing files contain no unresolved editorial questions.
- [ ] Confirm the package contains only intended showcase files.

## Current public package state

This package contains synthetic examples and two approved public-safe visual assets:

- `assets/screenshots/cadence-phone-session.png`
- `assets/diagrams/cadence-loop.png`

It does not contain private source code, local paths, credentials, real activity data, or snippet files.
