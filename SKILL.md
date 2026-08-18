---
name: list-my-startup
description: Given a product or startup's website URL, research its positioning and then create or refresh brand-compliant listings across startup, software, AI-tool, and review directories - the person logs in or signs up whenever a site requires it, and Claude fills every field. Use when someone wants to list/submit their startup or product to directories, get directory backlinks, or promote a launch across many sites.
---

# List My Startup on Directories

Given **one website URL**, this skill (1) researches the product and writes a reusable **positioning brief**, then (2) works through online directories - startup directories, software/AI-tool directories, review sites, launch platforms - creating or refreshing a **brand-compliant listing on each**. The person logs in or signs up whenever a site requires it; Claude does everything else (writing copy to length, filling every field, uploading the logo/screenshots, submitting) and keeps a resumable tracker CSV.

## When to use
Trigger when someone wants to "list my startup/product on directories", "submit us to directories", "get directory backlinks", "promote our launch everywhere", "put us on AlternativeTo / Product Hunt / G2 / etc.", or refresh existing directory listings with new messaging.

## Golden rules (read first)
- **Never create accounts, enter passwords, or complete CAPTCHAs / bot-checks / "what is 2+3" puzzles / email-verification links.** When a site needs any of these, stop and ask the person to do that one step, then continue. This is a hard line - the whole tag-team model depends on it.
- - **Never accept a paid tier, and never accept a "reciprocal backlink / footer badge" requirement**, unless the person explicitly opts in. Skip paid-only sites (e.g. a directory that has moved to a paid-launch model) and record why.
  - - **Never create a duplicate, and never overwrite a *different* product's existing listing.** Before adding, check whether the product is already listed. Watch for vendor accounts that already hold a *different* product (see "Product vs organization" below).
    - - **Everything is brand-compliant and factual.** All copy comes from the positioning brief. Never invent facts, pricing numbers, user counts, ratings, founding year, HQ, or team. Leave unknowns blank.
      - - **Create and maintain the tracker CSV from the very first step** (directory_tracker.csv) and update each row's status immediately after every site, so the run is resumable and never repeats work.
        - - **Set honest expectations.** The free-directory landscape is full of dead, paywalled, badge-gated, login-gated, and one-product-per-vendor sites. Aim for a strong core of high-value listings, not a big count of scraps - unless the person explicitly asks to exhaust the entire list.
         
          - ## Decision defaults (resolve these the way below; only ask when truly ambiguous)
          - These are the calls the skill must make on its own. The person can override any of them.
         
          - - **Product vs organization (important).** List the *product* (e.g. "Clad9") as its **own separate entry** on product/tool/software/AI directories and review sites - never as a feature of, or an edit to, the person's company/organization. Use the **organization** identity (the company, e.g. "Hadaa, Inc.") **only** on true organization/company-profile platforms (LinkedIn Company Page, Crunchbase org, Wellfound company, F6S "Company or Organization", an "About the org" page). On product-listing forms that ask "what company sells this software?", the org is the correct answer while the product stays the listing. Note: many vendor networks (Capterra / G2 Digital Markets, GoodFirms free tiers) allow one product per vendor account - if that slot already holds a *different* product, do NOT overwrite it; a separate product needs a new-product request or a paid tier. Flag it and move on.
            - - **Confirmation model.** Default: tag-team - before any irreversible public submit, show the person what's about to post and get a yes. But if the person grants **blanket pre-approval to publish**, submit each listing without pausing per-site.
              - - **Pricing.** Default to the real model (freemium / free / usage-based / one-time / commercial) with **no invented numbers**. If a required pricing field blocks submission, choose **"Free"/$0** or the platform's **"I don't have public pricing"** option; never fabricate a paid price. (Some platforms won't accept a $0 plan - then use their no-public-pricing option or leave the listing as a draft and tell the person.)
                - - **Missing company facts** (founded year, HQ city, legal name, founder surname, socials). Leave blank. If a **required** field forces an unknown, use the most reasonable *verified* value or ask. Note: some sites (e.g. StartupBlink) require an HQ **location** to place the entry on a map - get the city from the person before adding.
                  - - **Launch platforms & timing.** Scheduling is the person's call. If they authorize "as soon as possible", pick the **earliest** available date and proceed (Product Hunt lets you reschedule freely). A Hacker News **"Show HN"** is a one-time post, not a profile - post it when they say (immediately if asked); it pairs well with the Product Hunt launch day.
                   
                    - ## Phase 1 - Research & positioning brief
                    - Study the product before writing a single listing. Sources: the homepage, product/pricing/about pages, the blog, and any "best / compare / alternatives" article. Use web search + page fetch; if a page is client-rendered and fetch returns an empty shell, open it in the browser and read the rendered text.
                   
name: list-my-startup
description: Given a product or startup's website URL, research its positioning and then create or refresh brand-compliant listings across startup, software, AI-tool, and review directories - the person logs in or signs up whenever a site requires it, and Claude fills every field. Use when someone wants to list/submit their startup or product to directories, get directory backlinks, or promote a launch across many sites.
---

# List My Startup on Directories

Given **one website URL**, this skill (1) researches the product and writes a reusable **positioning brief**, then (2) works through online directories - startup directories, software/AI-tool directories, review sites, launch platforms - creating or refreshing a **brand-compliant listing on each**. The person logs in or signs up whenever a site requires it; Claude does everything else (writing copy to length, filling every field, uploading the logo/screenshots, submitting) and keeps a resumable tracker CSV.

## When to use
Trigger when someone wants to "list my startup/product on directories", "submit us to directories", "get directory backlinks", "promote our launch everywhere", "put us on AlternativeTo / Product Hunt / G2 / etc.", or refresh existing directory listings with new messaging.

## Golden rules (read first)
- **Never create accounts, enter passwords, or complete CAPTCHAs / bot-checks / "what is 2+3" puzzles / email-verification links.** When a site needs any of these, stop and ask the person to do that one step, then continue. This is a hard line - the whole tag-team model depends on it.
- **Never accept a paid tier, and never accept a "reciprocal backlink / footer badge" requirement**, unless the person explicitly opts in. Skip paid-only sites (e.g. a directory that has moved to a paid-launch model) and record why.
- **Never create a duplicate, and never overwrite a *different* product's existing listing.** Before adding, check whether the product is already listed. Watch for vendor accounts that already hold a *different* product (see "Product vs organization" below).
- **Everything is brand-compliant and factual.** All copy comes from the positioning brief. Never invent facts, pricing numbers, user counts, ratings, founding year, HQ, or team. Leave unknowns blank.
- **Create and maintain the tracker CSV from the very first step** (directory_tracker.csv) and update each row's status immediately after every site, so the run is resumable and never repeats work.
- **Set honest expectations.** The free-directory landscape is full of dead, paywalled, badge-gated, login-gated, and one-product-per-vendor sites. Aim for a strong core of high-value listings, not a big count of scraps - unless the person explicitly asks to exhaust the entire list.

## Decision defaults (resolve these the way below; only ask when truly ambiguous)
These are the calls the skill must make on its own. The person can override any of them.

- **Product vs organization (important).** List the *product* (e.g. "Clad9") as its **own separate entry** on product/tool/software/AI directories and review sites - never as a feature of, or an edit to, the person's company/organization. Use the **organization** identity (the company, e.g. "Hadaa, Inc.") **only** on true organization/company-profile platforms (LinkedIn Company Page, Crunchbase org, Wellfound company, F6S "Company or Organization", an "About the org" page). On product-listing forms that ask "what company sells this software?", the org is the correct answer while the product stays the listing. Note: many vendor networks (Capterra / G2 Digital Markets, GoodFirms free tiers) allow one product per vendor account - if that slot already holds a *different* product, do NOT overwrite it; a separate product needs a new-product request or a paid tier. Flag it and move on.
- **Confirmation model.** Default: tag-team - before any irreversible public submit, show the person what's about to post and get a yes. But if the person grants **blanket pre-approval to publish**, submit each listing without pausing per-site.
- **Pricing.** Default to the real model (freemium / free / usage-based / one-time / commercial) with **no invented numbers**. If a required pricing field blocks submission, choose **"Free"/$0** or the platform's **"I don't have public pricing"** option; never fabricate a paid price. (Some platforms won't accept a $0 plan - then use their no-public-pricing option or leave the listing as a draft and tell the person.)
- **Missing company facts** (founded year, HQ city, legal name, founder surname, socials). Leave blank. If a **required** field forces an unknown, use the most reasonable *verified* value or ask. Note: some sites (e.g. StartupBlink) require an HQ **location** to place the entry on a map - get the city from the person before adding.
- **Launch platforms & timing.** Scheduling is the person's call. If they authorize "as soon as possible", pick the **earliest** available date and proceed (Product Hunt lets you reschedule freely). A Hacker News **"Show HN"** is a one-time post, not a profile - post it when they say (immediately if asked); it pairs well with the Product Hunt launch day.

## Phase 1 - Research & positioning brief
Study the product before writing a single listing. Sources: the homepage, product/pricing/about pages, the blog, and any "best / compare / alternatives" article. Use web search + page fetch; if a page is client-rendered and fetch returns an empty shell, open it in the browser and read the rendered text.

Write a **positioning brief** (positioning_brief.md) covering: one-sentence positioning (a defensible *fact*, not an adjective); the problem it names and who it's for (a swappable paragraph per audience); what it does (mechanism, inputs to outputs, the key numbers); why it wins (3-5 pillars, each a mechanism + number); the wedge/moat; competitors and an honest factual contrast; the proof stack (label the company's own stats as its own claims); pricing (exact model; note anything to never say); self-beliefs/guardrails (words/claims to avoid, category boundaries); and **ready copy blocks at several lengths** - tagline (~60 and ~120 chars), short (~250 chars), medium (~100 words), long boilerplate (~1000 chars), a markdown profile/README version, plus a tags/keywords list, category picks, and a one-line audience. Confirm anything genuinely ambiguous before mass-submitting.

## Phase 2 - Assets (collect once, reuse everywhere)
- **Logo**: a square PNG (~512px and ~192px copies). If no logo file is provided and a site needs one, fetch the site's own apple-touch-icon.png (usually square) via the browser and upscale it on a canvas to >=200px, then upload it to a real file input. (Cross-origin canvas export only works if the site serves CORS headers; otherwise hand the file step to the person.)
- **Screenshots**: if a site requires a screenshot/gallery image and none are supplied, **capture the product's own website** in the browser (hero, "how it works", features) and upload those. This is a legitimate, on-brand image source. Note the browser screenshot tool caps at ~1568px wide - if a site demands a larger minimum (e.g. 1920x1080), the person must supply real high-res screenshots.
- **Native OS file pickers can't be automated.** If a site's upload button opens the operating-system file dialog (no reachable file input in the DOM), hand that one step to the person.
- **Company facts**: legal name, founded year, HQ city, contact email, phone, and social URLs - only if verifiable.

## Phase 3 - Directory targeting
Start from the bundled directories.csv if present. Work the ones that fit the product; skip the rest. A vetted starting set:
- **Create a listing (log in, then fill every field):** Product Hunt, Indie Hackers, Crunchbase, Wellfound, F6S, Startup Buffer, Uneed, aitools.inc, DealMyApp, GoodFirms, GitHub (org + profile-README), LinkedIn Company Page, Softonic Publishing Center (web apps are accepted; "free to publish"; developer portal needs its own sign-in).
- **Public form, no login:** FutureTools, SourceForge (also syndicates to Slashdot), Launching Next, Startup Buffer.
- **One submission syndicates to several:** the Capterra / Gartner-Digital-Markets / G2-Digital-Markets get-listed flow publishes to Capterra + GetApp + Software Advice - submit once (subject to the one-product-per-vendor rule above).
- **Refresh, don't duplicate (usually already listed):** AlternativeTo (also: after adding, link several competitor apps as "alternatives" to boost discoverability), StartupBlink.
- **High value but gated - revisit with a work email / business account:** G2, Gartner/G2 Digital Markets, Trustpilot (per-domain; builds value from real reviews - low value for a brand-new product with zero reviews; never fabricate reviews).
- **One-time launch posts (time with the launch):** Hacker News "Show HN".

**Maintain directory_tracker.csv from the start.** One row per directory. Columns: Site, Category, Homepage, Submit/Edit URL, Status, Listing Live, Backlink, Login Required, Reciprocal Link Req, Paid, Profile Editable, Priority, Notes, Last Updated. Statuses to use: **Live**, **Submitted (in review)**, **Blocked - needs user login/decision/data (with the reason)**, **Skipped - reason**, **Deferred**. Update the row immediately after each site.

**Fast triage per candidate:** dead/404/redirects-to-paid -> Skip; paid-only or reciprocal-badge -> Skip (unless opted in); embedded cross-origin form (Tally/Airtable/Typeform in an iframe) -> usually not fillable, hand to the person; community "pay with engagement" walls -> Skip (don't fake engagement); already lists the product -> Refresh; public form -> do it now; behind login -> tag-team.

## Phase 4 - Submission loop (tag-team model)
For each viable directory: open the submit/claim/edit URL; if it needs login/signup/verification/CAPTCHA, **say the word** (tell the person exactly what to do, wait, continue); fill every field from the positioning brief, trimming to each field's char limit; pick the **most specific** category; set pricing to the real model; choose platforms honestly (web app -> Online / SaaS / Web-based); upload the logo and one or two screenshots; add socials + the **canonical** website URL; submit/save; confirm the success state; **update the tracker row immediately**.

**Batch login handoff.** When many sites need login, open them as **tabs in batches (e.g. 10 at a time)** so the person can sign into each, then go back and fill every one. This is far faster than one-at-a-time.

## Browser-automation playbook (hard-won)
- **Text inputs**: set the value, then verify the on-screen char counter changed. If a React/Ember field ignores a programmatic set (validation still says "required"), click in and type real keystrokes.
- **Autocomplete / combobox** (city, industry, tags, category): type, wait for the dropdown, then **click** the matching option - don't type-and-move-on; Enter usually won't bind the tag.
- **Native select**: set the value via the form-input tool (which dispatches change), not coordinate clicks.
- **Rich-text editors (CodeMirror/ProseMirror/contenteditable)**: a programmatic value-set usually returns empty - instead click into the editor and type real keystrokes; plain paragraphs are fine (avoid multi-line markdown that auto-continues bullets).
- **Hidden file inputs**: reveal or target the file input and upload directly. If there is **no** file input in the DOM (a styled button that opens the OS picker), you cannot automate it - hand it to the person.
- **Fetch the site's own assets when a real file input exists**: load the product's apple-touch-icon/logo or capture a page screenshot in the browser and upload it programmatically (subject to the CORS + resolution caveats in Phase 2).
- **Cloudflare / bot interstitials**: wait for auto-pass; if it presents a checkbox/puzzle, that's a bot-check - hand it to the person.
- **OAuth "choose an account" / consent screens**: never pick an account or grant consent - that's the person's login step.
- **Duplicate/exists guards**: on "name/website already exists", the item is created - pivot to finding and **editing** it rather than making a second one.
- **Cookie/consent banners**: choose the most privacy-preserving option; if the only choice is Accept, accept to proceed.

## Deliverables
- positioning_brief.md - the source of truth for all copy.
- directory_tracker.csv - **created at the start and updated continuously**; every directory with status and date; resumable across sessions.
- (optional) copy_pack.md - per-platform paste-ready copy at each length.

Finish with a short, honest summary: how many listings are **live**, **submitted / in review**, or **refreshed**; which are **blocked and need the person's action** (login, verification, a decision like product-vs-org, missing data like HQ city, or a paid/new-account requirement); and which were **skipped and why**.
