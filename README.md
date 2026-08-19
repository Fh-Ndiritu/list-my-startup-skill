# list-my-startup

A Claude Cowork skill that takes a single product/startup URL, researches its positioning - what it does, features, differentiators, competitors, proof points, pricing, self-beliefs - then creates or refreshes brand-compliant listings across startup, software, AI-tool, and review directories.

You log in or sign up whenever a site requires it; Claude does everything else - writing copy to each field's length, filling forms, uploading the logo and screenshots, submitting, and keeping a resumable tracker.

**It gets smarter every time anyone runs it.** The skill ships with a shared registry (`directories.csv`) of which directories are worth doing, which to refresh, and which to skip - with a reason on each. Every run reads it (so it never wastes a turn on a known dead end) and every run opens a pull request to update it with what it learned. Run after run, the community's collective experience compounds.

## What it does

- **Research** - studies the site (and competitors) and writes a reusable `positioning_brief.md` with copy blocks at every length directories ask for.
- **Assets** - collects the logo (square, reusable) and a few screenshots. Handy trick: it pulls the site's own `apple-touch-icon` and turns it into a clean square logo, so it can fill logo fields without you.
- **Target & triage (registry-driven)** - reads `directories.csv`, works the proven ones first, refreshes what's already listed, skips the known dead ends, and builds a per-run tracker.
- **Submit (tag-team)** - opens each directory, hands login / signup / verification / CAPTCHA to you, then fills every field and submits.
- **Contribute back** - at the end of a run it opens a PR updating the registry, so the next person inherits the improvement.

## The self-improving registry

`directories.csv` is the memory of every past run. Each directory carries a `Recommendation`:

- **`Do (public form)` / `Do (login)`** - a clean listing is achievable (e.g. FutureTools, SourceForge, SaaSHub, Product Hunt, Indie Hackers, Crunchbase, Peerlist, MicroLaunch).
- **`Refresh` / `Claim`** - it's usually already listed or auto-generated; edit or claim it rather than duplicate (e.g. AlternativeTo, StartupBlink, Softonic).
- **`High value` / `Blocked` / `Optional`** - worth it but gated: needs a work email, a business account, or a specific fit (e.g. G2, Gartner/Capterra syndication, Trustpilot).
- **`Conditional: <gate>`** - a free path exists but it's gated by a login, an HQ city, your country, or an opt-in badge (e.g. Tiny Startups).
- **`Skip: <reason>`** - a dead end nobody should retry: paid-only, reciprocal-badge, engagement-wall, dead, or flagged (e.g. BetaList - now paid, There's An AI For That, Fazier, Twelve Tools, StartupBase, Dang.ai).

Because the skill reads this before it starts, it **never wastes a turn re-attempting a known dead end**, and it **prioritizes the directories that have paid off before**.

## The community loop (auto-PR after every run)

When a run finishes, the skill reconciles what it saw against `directories.csv` and **opens a pull request** against this repo:

- new directories that worked -> added with the right recommendation
- directories that turned out gated -> flipped to `Conditional` / `Skip` with the reason
- directories that went dead / paywalled / were flagged -> flipped to `Skip`
- recommendations that changed since last time -> updated, with a `(verified <month>)` note

It opens the PR (via your logged-in GitHub session in the browser) and leaves it for review - it never merges, never force-pushes, and never touches `main` directly. Merge the good ones, and everyone's next run is a little smarter.

## Guardrails

- Never creates accounts, enters passwords, or solves CAPTCHAs - you do those.
- Never accepts paid tiers, reciprocal-badge ("put our link on your site") requirements, or fakes community engagement to unlock a listing - unless you opt in.
- Never duplicates an existing listing - it refreshes it instead - and never overwrites a *different* product held by the same vendor account.
- All copy is brand-compliant and drawn from the positioning brief; it never invents pricing, user counts, ratings, founding year, or HQ.

## Install

Drop `SKILL.md` (and `directories.csv`) into your Claude Cowork skills, or save it as a skill. Then just say: *"list my startup on directories - here's the URL."*

## What you get

- `positioning_brief.md` - the source of truth for all copy.
- `directory_tracker.csv` - this run's log; every directory with status and date; resumable across sessions.
- `directories.csv` - the shared registry (recommendation per directory), updated and contributed back via a PR.

MIT licensed. PRs that improve the registry are the whole point - send them.
