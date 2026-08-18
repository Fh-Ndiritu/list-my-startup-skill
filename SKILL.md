---
name: list-my-startup
description: Given a product or startup's website URL, research its positioning (what it does, features, differentiators, competitors, proof points, pricing, self-beliefs) and then create or refresh brand-compliant listings across startup, software, AI-tool, and review directories - the person logs in or signs up whenever a site requires it, and Claude fills every field. Use when someone wants to list/submit their startup or product to directories, get directory backlinks, or promote a launch across many sites.
---

# List My Startup on Directories

Given **one website URL**, this skill (1) researches the product and writes a reusable **positioning brief**, then (2) works through online directories — startup directories, software/AI-tool directories, review sites, launch platforms — creating or refreshing a **brand-compliant listing on each**. The person logs in or signs up whenever a site requires it; Claude does everything else (writing copy to length, filling every field, uploading the logo/screenshots, submitting) and keeps a resumable tracker.

## When to use
Trigger when someone wants to "list my startup/product on directories", "submit us to directories", "get directory backlinks", "promote our launch everywhere", "put us on AlternativeTo / Product Hunt / G2 / etc.", or refresh existing directory listings with new messaging.

## Golden rules (read first)
- **Never create accounts, enter passwords, or complete CAPTCHAs / bot-checks / "what is 2+3" puzzles / email-verification links.** When a site needs any of these, stop and ask the person to do that one step, then continue. This is a hard line — the whole tag-team model depends on it.
- **Never accept a paid tier, and never accept a "reciprocal backlink / footer badge" requirement**, unless the person explicitly opts in. Many "free" listings require putting the directory's badge/link on the user's own site — skip those and record why.
- **Never create a duplicate.** Before adding, check whether the product is already listed (search the directory; watch for "website/name already exists" errors). If it exists, **refresh the existing listing** instead of making a second one.
- **Everything is brand-compliant.** All copy comes from the positioning brief. Follow its guardrails exactly (e.g. never invent pricing, never present the company's own stats as third-party-verified, stay in-category).
- **Log every site** to the tracker immediately so the run is resumable and never repeats work.
- **Set honest expectations.** The free-directory landscape is full of dead, paywalled, badge-gated, and embedded-form sites, and popular products are often already listed. Aim for a strong core of high-value listings, not a big count of low-quality scraps. Refreshing one high-authority listing (fix a stale domain, correct the description and pricing) often beats ten new scraps.

## Phase 1 — Research & positioning brief
Study the product before writing a single listing. Sources: the homepage, product/pricing/about pages, the blog, and any "best / compare / alternatives" article the site publishes. Use web search + page fetch; if a page is client-rendered and fetch returns an empty shell, open it in the browser and read the rendered text.

Write a **positioning brief** (`positioning_brief.md`) covering:
- **One-sentence positioning** — the sharpest claim the product can defend with a *fact*, not an adjective.
- **The problem it names** and **who it's for** (each distinct audience, with a swappable paragraph per audience).
- **What it does** — mechanism, inputs → outputs, speed, the key numbers.
- **Why it wins** — 3–5 pillars, each a *mechanism + number* (never "innovative / seamless / cutting-edge").
- **The wedge / moat** — the one thing competitors can't copy; lead with it everywhere.
- **Competitors** and the honest, factual contrast (never empty bashing).
- **Proof stack** — users, rating, countries, etc., with an attribution caveat: label the company's own stats as its own claims.
- **Pricing** — exact model and numbers; note anything to never say.
- **Self-beliefs / guardrails** — words and claims to avoid, category boundaries, promo rules.
- **Ready copy blocks at several lengths** (directory fields vary wildly):
  - Tagline / one-liner (~60 and ~120 chars)
  - Short (~50 words / ~250 chars)
  - Medium (~100 words)
  - Long boilerplate (~150 words / ~1000 chars)
  - A profile-README / rich-text version (markdown)
  - Tags/keywords list, category picks, one-line audience.

If anything is ambiguous (which of two stats is correct, exact founding year, canonical domain), confirm with the person before mass-submitting.

## Phase 2 — Assets (collect once, reuse everywhere)
- **Logo**: a square PNG. Keep a large (~512px) and a small (~192px) copy — some sites cap dimensions at 500px or file size at 2MB. Compress if needed.
- **Screenshots**: 2–4 real product screenshots/renders, each compressed under ~2MB.
- **Company facts**: legal name, founded year, HQ city, contact email, phone, and social URLs (LinkedIn, YouTube, Facebook, X, TikTok).

## Phase 3 — Directory targeting
Maintain a **tracker CSV** (`directory_tracker.csv`), one row per directory. Columns:
`Site, Category, Homepage, Submit/Edit URL, Status, Listing Live, Backlink, Login Required, Reciprocal Link Req, Paid, Profile Editable, Priority, Notes, Last Updated`

Categories to consider: launch platforms (Product Hunt-style), AI-tool directories, software/SaaS review sites (Capterra/GetApp/G2/GoodFirms/SourceForge), general startup directories (Crunchbase/Wellfound/F6S/StartupBlink), B2B review networks, and any niche directory for the product's vertical. Note: some networks syndicate one submission to several sites (e.g. a single G2/Digital-Markets form → Capterra + GetApp + Software Advice).

**Fast triage per candidate** — navigate, glance, decide, move on:
- Dead / 404 / redirects to a paid site → **Skip**, note it.
- Paid-only, or free tier needs a reciprocal badge → **Skip** (unless opted in).
- Embedded third-party form (Tally/Airtable/Typeform in a cross-origin iframe) → usually **not programmatically fillable**; have the person fill it, else skip.
- Community "pay with engagement" walls (must upvote/review N other products first) → **Skip** (don't fake engagement).
- Already lists the product → **Refresh**, don't duplicate.
- Public native form (no login) → do it now.
- Native form behind login/signup → tag-team (Phase 4).

## Phase 4 — Submission loop (tag-team model)
For each viable directory:
1. Open the submit / claim / edit URL.
2. If it needs login, signup, email verification, or a CAPTCHA → **say the word**: tell the person exactly what to do ("please log in / sign up / click the verification link / solve the check"), wait for confirmation, then continue. Never do it yourself.
3. Fill every field from the positioning brief, trimming copy to each field's character limit. Pick the **most specific** category; set pricing to the real model (usage-based / one-time / freemium / commercial); choose platforms honestly (for a web app: Online / SaaS / Web-based).
4. Upload the logo and one or two screenshots.
5. Add socials and the website URL — use the **canonical domain**, and fix stale old domains if you find them.
6. Submit / save; confirm the success state (a "thanks / submitted / your page is live" message, or the edit going into a moderation queue).
7. Update the tracker row (Status, Last Updated, notes) immediately.

Batch independent browser actions where possible. After a wrong-tier or blocked step, debug or report — don't silently retry.

## Browser-automation playbook (hard-won)
- **Text inputs**: set the value, then verify the on-screen char counter changed. If a React field ignores a programmatic set, click in and type real keystrokes.
- **Autocomplete / combobox fields** (city, industry, markets, tags, category): type a query, wait for the dropdown, then **click the matching option** — don't type-and-move-on; the value won't bind. Pressing Enter usually does not create the tag.
- **Native `<select>`**: set the value via script and dispatch a `change` event (options often aren't reachable by coordinate-clicks).
- **Hidden file inputs** (logo/screenshot behind a styled "Upload" button, dropzone, or Cloudinary/Uploadcare widget): reveal the `input[type=file]` via script (force it visible/positioned), then upload to it directly. Never click the upload button — it opens an OS file picker you can't operate.
- **Rich-text / code editors (CodeMirror / ProseMirror)**: don't type multi-line markdown — the editor auto-continues bullet lists and progressively indents, mangling it. Instead focus the editable node, select-all, and insert the whole block in one shot (e.g. `document.execCommand('insertText', false, text)`), then confirm with Preview.
- **Cross-origin embedded forms**: coordinate-typing usually won't reach them; hand to the person or skip.
- **Company-profile pages with a strength meter**: fill logo, tagline, description, markets, socials, stage — they often auto-save on blur; verify on the public page afterward.
- **Duplicate guards**: on "name/website already exists", pivot to finding and **editing** the existing item (look for "Contribute / Suggest an edit / Claim this page").
- **Cookie / consent banners**: choose the most privacy-preserving option available; if the only choice is Accept, accept to proceed.

## Deliverables
- `positioning_brief.md` — the source of truth for all copy.
- `copy_pack.md` (optional) — per-platform paste-ready copy at each length.
- `directory_tracker.csv` — every directory with status and date; resumable across sessions.

Share these files and give a short, honest summary: how many listings are **live**, **submitted / in review**, or **refreshed**; which are **blocked and need the person's action** (login, verification, paid); and which were **skipped and why**.
