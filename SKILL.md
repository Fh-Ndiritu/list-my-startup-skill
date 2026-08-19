---
name: list-my-startup
description: Given a product or startup's website URL, research its positioning and then create or refresh brand-compliant listings across startup, software, AI-tool, and review directories - the person logs in or signs up whenever a site requires it, and Claude fills every field. Use when someone wants to list/submit their startup or product to directories, get directory backlinks, or promote a launch across many sites.
---

# List My Startup on Directories

Given **one website URL**, this skill (1) researches the product and writes a reusable **positioning brief**, then (2) works through online directories - startup directories, software/AI-tool directories, review sites, launch platforms - creating or refreshing a **brand-compliant listing on each**. The person logs in or signs up whenever a site requires it; Claude does everything else (writing copy to length, filling every field, uploading the logo/screenshots, submitting) and keeps a resumable tracker CSV.

This skill is **self-improving and community-run**: it ships with a shared `directories.csv` registry that records which directories are worth doing, which to refresh, and which to skip (and why). Every run reads that registry so it never re-attempts a known dead end, and every run **contributes what it learned back via a pull request** so the registry gets better each time anyone runs it.

## When to use
Trigger when someone wants to "list my startup/product on directories", "submit us to directories", "get directory backlinks", "promote our launch everywhere", "put us on AlternativeTo / Product Hunt / G2 / etc.", or refresh existing directory listings with new messaging.

## Golden rules (read first)
- **Never create accounts, enter passwords, or complete CAPTCHAs / bot-checks / "what is 2+3" puzzles / email-verification links.** When a site needs any of these, stop and ask the person to do that one step, then continue. This is a hard line - the whole tag-team model depends on it.
- **Never accept a paid tier, and never accept a "reciprocal backlink / footer badge" requirement**, unless the person explicitly opts in. Skip paid-only sites (e.g. a directory that has moved to a paid-launch model) and record why.
- **Never fake community engagement.** Some "free" launch platforms only confirm a submission after you upvote/comment on / review N other products, or after you embed their badge. Do not game these - submit what you can, flag the gate, and let the person decide.
- **Never create a duplicate, and never overwrite a *different* product's existing listing.** Before adding, check whether the product is already listed. Watch for vendor accounts that already hold a *different* product (see "Product vs organization" below).
- **Everything is brand-compliant and factual.** All copy comes from the positioning brief. Never invent facts, pricing numbers, user counts, ratings, founding year, HQ, or team. Leave unknowns blank.
- **Consult the registry first, and never re-attempt a known dead end.** Read the bundled `directories.csv` before targeting. Its `Recommendation` column is the memory of past runs - honour it: do the `Do (...)` / `Refresh` / `Claim` ones, treat `High value` / `Blocked` / `Optional` as their notes describe, and **do not reopen any row whose recommendation starts with `Skip:`** (record it as skipped-per-registry instead).
- **Create and maintain the run tracker CSV from the very first step** (`directory_tracker.csv`) and update each row's status immediately after every site, so the run is resumable and never repeats work.
- **Contribute findings back at the end of the run** by opening a pull request that updates `directories.csv` (see Phase 5). This is what makes the skill improve for everyone.
- **Set honest expectations.** The free-directory landscape is full of dead, paywalled, badge-gated, engagement-walled, login-gated, and one-product-per-vendor sites. Aim for a strong core of high-value listings, not a big count of scraps - unless the person explicitly asks to exhaust the entire list.

## Decision defaults (resolve these the way below; only ask when truly ambiguous)
These are the calls the skill must make on its own. The person can override any of them.

- **Product vs organization (important).** List the *product* (e.g. "Clad9") as its **own separate entry** on product/tool/software/AI directories and review sites - never as a feature of, or an edit to, the person's company/organization. Use the **organization** identity (the company, e.g. "Hadaa, Inc.") **only** on true organization/company-profile platforms (LinkedIn Company Page, Crunchbase org, Wellfound company, F6S "Company or Organization", an "About the org" page). On product-listing forms that ask "what company sells this software?", the org is the correct answer while the product stays the listing. On multi-project platforms (e.g. Peerlist) always **add a new project** rather than editing the org's other products. Note: many vendor networks (Capterra / G2 Digital Markets, GoodFirms free tiers) allow one product per vendor account - if that slot already holds a *different* product, do NOT overwrite it; a separate product needs a new-product request or a paid tier. Flag it and move on.
- **Confirmation model.** Default: tag-team - before any irreversible public submit, show the person what's about to post and get a yes. But if the person grants **blanket pre-approval to publish**, submit each listing without pausing per-site.
- **Pricing.** Default to the real model (freemium / free / usage-based / one-time / commercial) with **no invented numbers**. If a required pricing field blocks submission, choose **"Free"/$0** or the platform's **"I don't have public pricing"** option; never fabricate a paid price. (Some platforms won't accept a $0 plan - then use their no-public-pricing option or leave the listing as a draft and tell the person.)
- **Missing company facts** (founded year, HQ city, legal name, founder surname, socials). Leave blank. If a **required** field forces an unknown, use the most reasonable *verified* value or ask. Note: some sites require an HQ **location** (StartupBlink) or a personal **country of residence** (MicroLaunch) - these are personal/unpublished, so ask the person; don't guess.
- **Launch platforms & timing.** Scheduling is the person's call. If they authorize "as soon as possible", pick the **earliest** available slot and proceed (Product Hunt and Peerlist let you reschedule freely; some Launchpads only open on a fixed weekday, so schedule the next one). A Hacker News **"Show HN"** is a one-time post, not a profile - post it when they say (immediately if asked); it pairs well with the launch day.

## Phase 1 - Research & positioning brief
Study the product before writing a single listing. Sources: the homepage, product/pricing/about pages, the blog, and any "best / compare / alternatives" article. Use web search + page fetch; if a page is client-rendered and fetch returns an empty shell, open it in the browser and read the rendered text.

Write a **positioning brief** (positioning_brief.md) covering: one-sentence positioning (a defensible *fact*, not an adjective); the problem it names and who it's for (a swappable paragraph per audience); what it does (mechanism, inputs to outputs, the key numbers); why it wins (3-5 pillars, each a mechanism + number); the wedge/moat; competitors and an honest factual contrast; the proof stack (label the company's own stats as its own claims); pricing (exact model; note anything to never say); self-beliefs/guardrails (words/claims to avoid, category boundaries); and **ready copy blocks at several lengths** - tagline (~60 and ~120 chars), short (~250 chars), medium (~100 words), long boilerplate (~1000 chars), a markdown profile/README version, plus a tags/keywords list, category picks, and a one-line audience. Confirm anything genuinely ambiguous before mass-submitting.

## Phase 2 - Assets (collect once, reuse everywhere)
- **Logo**: a square PNG (~512px and ~192px copies). If no logo file is provided and a site needs one, fetch the site's own **apple-touch-icon.png** (usually a clean square). Best trick: open the icon URL directly in a browser tab, enlarge the image to fill the viewport on a white background (a one-line DOM tweak), then screenshot it - this yields a crisp square logo you can upload to any real file input, and it sidesteps the cross-origin canvas problem (sites that serve no CORS headers taint a canvas export and fail). Reuse that one logo image everywhere.
- **Screenshots**: if a site requires a screenshot/gallery image and none are supplied, **capture the product's own website** in the browser (hero, "how it works", features) and upload those. This is a legitimate, on-brand image source. Note the browser screenshot tool caps at ~1568px wide - if a site demands a larger minimum (e.g. 1920x1080), the person must supply real high-res screenshots.
- **Native OS file pickers can't be automated.** If a site's upload button opens the operating-system file dialog (no reachable file input in the DOM), hand that one step to the person.
- **Company facts**: legal name, founded year, HQ city, contact email, phone, and social URLs - only if verifiable.

## Phase 3 - Directory targeting (registry-driven)
Start from the bundled **directories.csv** - it is the memory of every past run. Each row carries a `Recommendation`: `Do (public form)` / `Do (login)` (a clean listing is achievable), `Refresh` (usually already listed - edit, don't duplicate), `Claim` (an auto-generated page to claim), `High value` / `Optional` (per the notes), `Blocked` (gated - revisit with a work email/business account), `Via <X>` (syndicated - don't submit separately), or `Skip: <reason>` (paid / badge / engagement-wall / dead / broken - **do not reopen**). Some rows are `Conditional: <gate>` - attempt only if the gate (login, HQ city, opt-in badge) is acceptable.

Work the `Do`/`Refresh`/`Claim` set first, then `Conditional`/`Blocked` where the gate is acceptable, and never spend a turn on a `Skip:` row. Add fresh candidates you discover along the way. A vetted starting set (all captured in directories.csv):
- **Public form, no login (fastest wins):** FutureTools, SourceForge (syndicates to Slashdot), Launching Next, Startup Buffer.
- **Create a listing (log in, then fill every field):** Product Hunt, SaaSHub, Indie Hackers, Crunchbase, Wellfound, F6S, Uneed, aitools.inc, DealMyApp, GoodFirms, Softonic Publishing Center (web apps accepted), GitHub (org + profile-README), LinkedIn Company Page, MicroLaunch (Tally form; needs the person's country), Peerlist (one-time verification, then add a **separate** project + schedule a Monday launch).
- **One submission syndicates to several:** the Capterra / Gartner-Digital-Markets get-listed flow publishes to Capterra + GetApp + Software Advice - submit once (subject to the one-product-per-vendor rule above).
- **Refresh, don't duplicate (usually already listed):** AlternativeTo (also link competitor apps as "alternatives" to boost discovery), StartupBlink.
- **High value but gated - revisit with a work email / business account:** G2, Gartner/G2 Digital Markets, Trustpilot (per-domain; low value for a brand-new product with zero reviews; never fabricate reviews).
- **One-time launch posts (time with the launch):** Hacker News "Show HN".
- **Known Skip (don't reopen):** BetaList (publish is now paid-only), There's An AI For That / Futurepedia / Toolify / topai.tools (paid), Fazier & Twelve Tools & submitaitools.org & toolpilot.ai (reciprocal badge), StartupBase (engagement wall), Dang.ai (flagged as a dangerous/low-reputation link), plus the many dead/404 AI directories the registry already lists.

**Maintain directory_tracker.csv (this run) from the start.** One row per directory. Columns: Site, Category, Homepage, Submit/Edit URL, Status, Listing Live, Backlink, Login Required, Reciprocal Link Req, Paid, Profile Editable, Priority, Notes, Last Updated. Statuses to use: **Live**, **Submitted (in review)**, **Blocked - needs user login/decision/data (with the reason)**, **Skipped - reason**, **Deferred**. Update the row immediately after each site.

**Fast triage per candidate:** dead/404/redirects-to-paid -> Skip; paid-only or reciprocal-badge or engagement-wall -> Skip (unless opted in); embedded cross-origin form (Tally/Airtable/Typeform in an iframe) -> usually not fillable, hand to the person (a *standalone* tally.so/r/ form is fine to fill); community "pay with engagement" walls -> Skip (don't fake engagement); already lists the product -> Refresh; public form -> do it now; behind login -> tag-team.

## Phase 4 - Submission loop (tag-team model)
For each viable directory: open the submit/claim/edit URL; if it needs login/signup/verification/CAPTCHA, **say the word** (tell the person exactly what to do, wait, continue); fill every field from the positioning brief, trimming to each field's char limit; pick the **most specific** category; set pricing to the real model; choose platforms honestly (web app -> Online / SaaS / Web-based); upload the logo and one or two screenshots; add socials + the **canonical** website URL; submit/save; confirm the success state; **update the tracker row immediately**.​

**Batch login handoff.** When many sites need login, open them as **tabs in batches (e.g. 10 at a time)** so the person can sign into each, then go back and fill every one. This is far faster than one-at-a-time.

## Phase 5 - Contribute findings back (open a PR) - the self-improving loop
After the run, reconcile what you learned against the bundled directories.csv and **open a pull request** so the next person (anyone, anywhere) inherits the improvement.

1. **Diff the run against the registry.** For every directory touched this run, decide the delta:
   - A directory that **worked** and isn't in the registry -> add a row with the right `Recommendation` and a dated note.
   - A directory that **turned out gated** (newly paywalled, now demands a badge/engagement/verification, one-product-per-vendor) -> flip it to `Skip: <reason>` or `Conditional: <gate>` with the reason.
   - A directory that is **dead / 404 / security-flagged** -> flip to `Skip: <reason>` so nobody wastes a turn on it again.
   - A recommendation that **changed** since last time (e.g. a free site went paid, or a blocked one now works with a login) -> update the row and add a `(verified <month>)` note.
2. **Open the PR** against the community repo (`Fh-Ndiritu/list-my-startup-skill`, or the repo the skill was installed from). The person is logged into GitHub in the browser; do it via the web UI: create a new branch, edit `directories.csv` (and SKILL.md / README.md if the workflow itself changed), commit, and open the pull request. Title it e.g. `registry: <N> updates from a <product> run (<month>)` and in the body list each add/flip with its one-line reason. **Never force-push, never touch `main` directly, never merge - open the PR and leave it for review.**
3. **Editor gotcha.** GitHub's in-browser code editor auto-indents and can mangle pasted lists (it has corrupted this very file before - double `- - ` bullets). Set file contents by focusing the editor, selecting all (clear it), then `document.execCommand('insertText', false, content)` with the content in a plain template literal - this inserts verbatim without auto-continuation. Verify the diff renders before opening the PR.
4. **Respect the guardrails even here:** opening a PR is fine, but do not merge it, do not change licensing, and do not commit anything the person hasn't seen.

## Browser-automation playbook (hard-won)
- **Text inputs**: set the value, then verify the on-screen char counter changed. If a React/Ember field ignores a programmatic set (validation still says "required"), click in and type real keystrokes. Watch length limits - a too-long autofilled tagline (e.g. >60 chars) will silently block submit.
- **AI autofill**: several platforms (BetaList, StartupBase, Peerlist, MicroLaunch) offer "autofill from URL". Use it, then **review** - fix an over-long tagline, drop an inaccurate auto-tag (e.g. "Virtual Reality" for a virtual *try-on* app), and confirm the auto-pulled logo/screenshots.
- **Autocomplete / combobox** (city, industry, tags, category): type, wait for the dropdown, then **click** the matching option - don't type-and-move-on; Enter usually won't bind the tag. If the exact category is missing, pick the closest real one (an AI wardrobe app -> "AI & Assistants" when there's no "Fashion").
- **Native select**: set the value via the form-input tool (which dispatches change), not coordinate clicks.
- **Rich-text editors (CodeMirror/ProseMirror/contenteditable)**: a programmatic value-set usually returns empty - instead click into the editor and type real keystrokes, or use execCommand('insertText', ...); plain paragraphs are fine (avoid multi-line markdown that auto-continues bullets).
- **Standalone Tally forms** persist a draft in localStorage - reopening the form after a browser restart restores your typed fields and uploads. Good to know if tabs close mid-run.
- **Hidden file inputs**: reveal or target the file input and upload directly (screenshot -> upload works). If there is **no** file input in the DOM (a styled button that opens the OS picker), you cannot automate it - hand it to the person.
- **Cloudflare / bot interstitials**: wait for auto-pass; if it presents a checkbox/puzzle, that's a bot-check - hand it to the person.
- **OAuth "choose an account" / consent screens**: never pick an account or grant consent - that's the person's login step.
- **Duplicate/exists guards**: on "name/website already exists", the item is created - pivot to finding and **editing** it rather than making a second one.
- **Cookie/consent banners**: choose the most privacy-preserving option; if the only choice is Accept, accept to proceed.

## Deliverables
- positioning_brief.md - the source of truth for all copy.
- directory_tracker.csv - this run's log; **created at the start and updated continuously**; every directory with status and date; resumable across sessions.
- directories.csv - the shared **registry** (Recommendation per directory), updated and **contributed back via a PR** at the end of the run.
- (optional) copy_pack.md - per-platform paste-ready copy at each length.

Finish with a short, honest summary: how many listings are **live**, **submitted / in review**, or **refreshed**; which are **blocked and need the person's action** (login, verification, a decision like product-vs-org, missing data like HQ city or country, or a paid/new-account requirement); which were **skipped and why**; and a note that a **PR with the registry updates** has been opened for review.
