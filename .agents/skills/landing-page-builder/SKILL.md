---
name: landing-page-builder
description: Interview-driven workflow that turns a landing page idea into a complete content + design-direction + i18n/SEO/GEO brief. Use when the user wants to plan a new landing page from scratch, needs section-by-section copy drafted from their answers, wants a design direction chosen from emotional tone, or needs a multi-language SEO/GEO technical checklist before any code is written.
---

# Landing Page Builder

## Trigger

User asks to plan or build a landing page ("build me a landing page", "tạo landing page", "help me plan a landing page for..."), or invokes this skill directly.

## Mode

This is a two-phase workflow. This skill implements **Phase 1 only**.

1. **Plan Mode (this skill)** — interview the user, produce a single Markdown brief. Stop here. Do not write any application code or scaffold a project in this phase.
2. **Build Mode (separate, later step)** — scaffolding the actual Next.js + next-intl app from the approved brief's Technical Build Checklist. Not run by this skill — surface it as a Follow-Up once the brief is approved.

Never skip ahead to Build Mode inside this skill, even if the user seems eager — the brief must be produced and can be reviewed first.

## Process

Ask questions one at a time (or in small tightly related batches), in order. Never invent answers on the user's behalf — if something is unclear or unanswered, ask rather than assume. Skip questions that are genuinely not applicable given earlier answers (e.g. skip Pricing if the goal is a waitlist), but don't skip content questions just to save time.

### Step 1 — Topic & Goals

Ask for:
- Product/service name
- One-line description of what it does
- Primary goal of the page (signup, waitlist, sales, download, contact/lead-gen, other)
- Target audience
- Primary call-to-action (CTA) text/action
- Target locales/languages to support, and which one is the default

### Step 2 — Section-by-section content

Walk through standard landing page sections one at a time, asking for real content for each — only include sections relevant to the Step 1 goal:

- **Hero** — headline, subheadline, CTA text
- **Problem / value proposition**
- **Features / benefits** — ask how many the user wants, then ask for each one individually (title + description)
- **Social proof** — testimonials, logos, stats
- **Pricing** — only if the product has pricing tiers
- **FAQ** — question/answer pairs
- **Final CTA**
- **Footer** — links, legal, contact info

Capture the user's actual wording first — do not draft placeholder or invented copy while gathering. Once all relevant sections have raw answers, follow **[Copywriting Reference](references/copywriting.md)** to filter each section down to its core idea and tighten it into standard, persuasive landing-page copy. That process never invents facts — it only rewrites phrasing/structure — and it shows the user original vs. polished copy for confirmation before anything is treated as final. Use the confirmed, polished version in the brief's Section-by-section copy.

### Step 3 — Emotional tone → design direction

Ask what emotional tone(s) the page should evoke. Offer examples to anchor the answer: trustworthy/corporate, playful/energetic, luxurious/premium, raw/technical, minimal/calm, bold/rebellious. Also ask for any reference sites or brands they admire (optional), and their industry/category (this affects which aesthetics read as credible vs. off-brand).

**Consult `.agents/skills/design-aesthetics/SKILL.md`** — it's a maintained catalog of current design aesthetics (neo-brutalism, editorial minimalism, agency-grade polish, kinetic motion, grainy gradients, glassmorphism, Y2K/retro-futurism, full brand identity, etc.), each with concrete visual characteristics and the industries/tones it fits. Match the user's stated tone/industry/references against that catalog rather than inventing aesthetic descriptions from scratch. That skill also documents which design skill(s) in this repo execute each aesthetic, including blends when one aesthetic needs more than one skill.

**Then brainstorm motion direction the same way — grounded, not decorative.** Don't pick a motion effect off a shelf. Look back at what the product actually *is* (Step 1) and what its sections actually describe (Step 2): does it have physical components (→ an exploded-view/scrollytelling reveal could make sense), a multi-step process (→ a sequential pipeline/flow animation), a before/after transformation (→ a morph/transition), or nothing structurally distinctive (→ motion should stay restrained and support reading, not perform). Generate 2-3 concepts *specific to this product's actual mechanic or content structure*, reject any that are generic defaults (fade-up-on-scroll, generic particle backgrounds, directionless parallax) unless nothing more specific fits, and if the confirmed aesthetic direction is time-sensitive (kinetic/motion-heavy styles date quickly), use WebSearch to sanity-check the concept against recent Awwwards/Codrops case studies before presenting it.

Present the design direction and motion direction together as one recommendation, with rationale that names the specific aesthetic(s) from the catalog and the specific motion concept(s) and why each fits this product/audience — not just a tone-to-skill mapping. Then explicitly ask the user to confirm both or pick a different direction. Do not finalize the brief until the user has confirmed.

### Step 4 — i18n / SEO / GEO requirements

Ask for:
- Locales to support and URL strategy (subpath like `/en`, `/vi` vs subdomain)
- Target keywords per locale (optional — mention `/seo-audit` is available for deeper keyword research)
- Structured data needs (Organization, Product, FAQ schema)
- GEO needs — whether they want a `llms.txt` summary and answer-style content blocks written for AI answer engines, not just traditional search crawlers

### Step 5 — Product imagery

Ask whether the user has real product/lifestyle photos to upload, or needs imagery generated from scratch. If they have real photos, invoke `product-photo-preprocessing` (see `.agents/skills/product-photo-preprocessing/SKILL.md`) — it assesses the uploads against [Product Imagery Reference](references/product-imagery.md), matches them to sections, flags gaps, fills gaps via `imagegen-frontend-web`/`imagegen-frontend-mobile`, and produces a confirmed, renamed image manifest. If the user has no real photos at all, skip straight to generation via `imagegen-frontend-web`/`imagegen-frontend-mobile` for whichever sections need imagery.

## Output

Write one file: `docs/03-Specs/Landing Page Brief - <Product Name>.md`. Use frontmatter matching `docs/Templates/Spec Template.md`'s conventions:

```yaml
---
title: Landing Page Brief - <Product Name>
tags: [spec, landing-page]
status: draft
created: <today's date, YYYY-MM-DD>
---
```

Body sections, in order:

1. **Goals & Audience** — from Step 1
2. **Section-by-section copy** — from Step 2, the confirmed polished copy (post `landing-page-copywriting`), not the raw transcript
3. **Design Direction** — the confirmed tone, the trending aesthetic(s) it draws from, the confirmed design skill(s) and rationale, and the confirmed motion concept(s) with the product-specific rationale behind them, from Step 3
4. **i18n / SEO / GEO Technical Build Checklist** — concrete and stack-specific (Next.js App Router + next-intl):
   - `app/[locale]/` route structure with one folder per locale
   - `next-intl` config and message catalogs per locale
   - Per-locale `generateMetadata` (title, description, canonical)
   - OpenGraph and Twitter card metadata
   - JSON-LD structured data (`Organization`, `Product`, and/or `FAQPage` depending on the brief)
   - `sitemap.ts` and `robots.ts`
   - Root `llms.txt` summarizing the product for AI crawlers/answer engines (GEO)
   - `hreflang` tags via next-intl's locale routing
   - Per-locale keyword targets, if provided in Step 4
   - Fully responsive layout: mobile-first CSS, tested breakpoints for mobile, tablet, and desktop, no fixed-width sections, touch-friendly tap targets and nav (e.g. mobile hamburger/drawer) on small screens
   - Post-deploy monitoring: GA4 (event/conversion tracking — page_view, CTA clicks, form submits, scroll depth) and Microsoft Clarity (heatmaps + session replay), both loaded via `next/script` in the root layout, gated behind a cookie-consent check if targeting GDPR regions
5. **Image manifest** — from Step 5's confirmed output: final filename, source (real/generated/enhanced), and target section for each image
6. **Follow-ups**:
   - Link back to `[[Specs MOC]]`
   - Note which design skill(s) to invoke next
   - Note that `/seo-audit` can be run for deeper keyword research once the brief is approved

After writing the brief, update `docs/03-Specs/Specs MOC.md` to add a link to the new brief, per the convention already documented in the repo's `CLAUDE.md`.

## Task Breakdown

Once the brief is written and the user confirms it, break it down into small, concrete task notes so a build step — run by any capable model, including a fast model like Sonnet — can execute each one quickly without re-deriving decisions or re-reading the whole brief. Each task must be unambiguous and self-contained: exact file paths/routes, exact component names, exact copy pulled from the brief (quoted in full, not referenced), exact locale list, exact responsive breakpoints — no open judgment calls left for the executor.

Create one task note per item using `docs/Templates/Task Template.md`, saved to `docs/05-Tasks/Todo/`, in this build order:

1. **Project scaffold** — Next.js App Router init, `next-intl` config, `app/[locale]/` routing skeleton
2. **SEO/GEO base** — `generateMetadata`, `sitemap.ts`, `robots.ts`, `llms.txt`, JSON-LD components
3. **Analytics & monitoring setup** — add GA4 (event tracking for page_view, each CTA click, form submits, scroll depth) and Microsoft Clarity (heatmaps + session replay) via `next/script` in the root layout; wire a cookie-consent gate if targeting GDPR regions
4. **Design system setup** — apply the confirmed design skill's tokens (typography/color/spacing) and implement the confirmed motion concept(s) from the brief
5. **One task per landing page section** (Hero, Problem, Features, Social proof, Pricing, FAQ, Final CTA, Footer) — each task's Description quotes the exact copy from the brief, names the exact image filename(s) from the Image manifest for that section, and states the responsive behavior expected at mobile/tablet/desktop
6. **i18n content wiring** — message catalogs per locale, populated with the translated copy
7. **QA pass** — responsive check across breakpoints, structured data validation, SEO/GEO checklist verification, and confirm GA4/Clarity are firing correctly

Each task note links back to `[[Tasks MOC]]` and to the brief note by name.

## Follow-Up

Once the brief is approved and task notes are created, these steps happen outside this skill:

- Invoke the confirmed design skill(s) from Step 3 while building the UI.
- Optionally run `/seo-audit` for deeper keyword research.
- Work through the task notes in `docs/05-Tasks/Todo/` in order, moving each to `docs/05-Tasks/Done/` as it's completed, to scaffold and build the Next.js + next-intl app.
