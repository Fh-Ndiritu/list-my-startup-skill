# list-my-startup

A **Claude Cowork skill** that takes a single product/startup URL, researches its positioning — what it does, features, differentiators, competitors, proof points, pricing, self-beliefs — then creates or refreshes brand-compliant listings across startup, software, AI-tool, and review directories.

You log in or sign up whenever a site requires it; Claude does everything else — writing copy to each field's length, filling forms, uploading the logo and screenshots, submitting, and keeping a resumable tracker.

## What it does
1. **Research** — studies the site (and competitors) and writes a reusable `positioning_brief.md` with copy blocks at every length directories ask for.
2. **Assets** — collects the logo (two sizes), a few screenshots, and company facts.
3. **Target & triage** — builds a directory tracker and fast-skips dead / paid / badge-gated / embedded-form / already-listed sites.
4. **Submit (tag-team)** — opens each directory, hands login / signup / verification / CAPTCHA to you, then fills every field and submits.

## Guardrails
- Never creates accounts, enters passwords, or solves CAPTCHAs — you do those.
- Never accepts paid tiers or reciprocal-badge ("put our link on your site") requirements unless you opt in.
- Never duplicates an existing listing — it refreshes it instead.
- All copy is brand-compliant and drawn from the positioning brief.

## Install
Drop [`SKILL.md`](SKILL.md) into your Claude Cowork skills (or save it as a skill). Then just say: *"list my startup on directories — here's the URL."*

## What you get
- `positioning_brief.md` — the source of truth for all copy.
- `directory_tracker.csv` — every directory with status and date; resumable across sessions.

MIT licensed.
