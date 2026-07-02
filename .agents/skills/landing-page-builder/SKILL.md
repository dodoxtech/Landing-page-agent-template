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

Capture the user's actual wording. Do not draft placeholder or invented copy — this section of the brief must reflect what the user actually said.

### Step 3 — Emotional tone → design direction

Ask what emotional tone(s) the page should evoke. Offer examples to anchor the answer: trustworthy/corporate, playful/energetic, luxurious/premium, raw/technical, minimal/calm, bold/rebellious. Also ask for any reference sites or brands they admire (optional), and their industry/category (this affects which aesthetics read as credible vs. off-brand).

**Consult `.agents/skills/design-aesthetics/SKILL.md`** — it's a maintained catalog of current design aesthetics (neo-brutalism, editorial minimalism, agency-grade polish, kinetic motion, grainy gradients, glassmorphism, Y2K/retro-futurism, full brand identity, etc.), each with concrete visual characteristics and the industries/tones it fits. Match the user's stated tone/industry/references against that catalog rather than inventing aesthetic descriptions from scratch. That skill also documents which design skill(s) in this repo execute each aesthetic, including blends when one aesthetic needs more than one skill.

Present the recommendation with rationale that names the specific aesthetic(s) from the catalog it draws from and why they fit this product/audience — not just a tone-to-skill mapping. Then explicitly ask the user to confirm it or pick a different direction. Do not finalize the brief until the user has confirmed the design direction.

### Step 4 — i18n / SEO / GEO requirements

Ask for:
- Locales to support and URL strategy (subpath like `/en`, `/vi` vs subdomain)
- Target keywords per locale (optional — mention `/seo-audit` is available for deeper keyword research)
- Structured data needs (Organization, Product, FAQ schema)
- GEO needs — whether they want a `llms.txt` summary and answer-style content blocks written for AI answer engines, not just traditional search crawlers

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
2. **Section-by-section copy** — from Step 2, verbatim from the interview
3. **Design Direction** — the confirmed tone, the trending aesthetic(s) it draws from, and the confirmed design skill(s) and rationale from Step 3
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
5. **Follow-ups**:
   - Link back to `[[Specs MOC]]`
   - Note which design skill(s) to invoke next
   - Note that `/seo-audit` can be run for deeper keyword research once the brief is approved

After writing the brief, update `docs/03-Specs/Specs MOC.md` to add a link to the new brief, per the convention already documented in the repo's `CLAUDE.md`.

## Task Breakdown

Once the brief is written and the user confirms it, break it down into small, concrete task notes so a build step — run by any capable model, including a fast model like Sonnet — can execute each one quickly without re-deriving decisions or re-reading the whole brief. Each task must be unambiguous and self-contained: exact file paths/routes, exact component names, exact copy pulled from the brief (quoted in full, not referenced), exact locale list, exact responsive breakpoints — no open judgment calls left for the executor.

Create one task note per item using `docs/Templates/Task Template.md`, saved to `docs/05-Tasks/Todo/`, in this build order:

1. **Project scaffold** — Next.js App Router init, `next-intl` config, `app/[locale]/` routing skeleton
2. **SEO/GEO base** — `generateMetadata`, `sitemap.ts`, `robots.ts`, `llms.txt`, JSON-LD components
3. **Design system setup** — apply the confirmed design skill's tokens (typography/color/spacing/motion)
4. **One task per landing page section** (Hero, Problem, Features, Social proof, Pricing, FAQ, Final CTA, Footer) — each task's Description quotes the exact copy from the brief and states the responsive behavior expected at mobile/tablet/desktop
5. **i18n content wiring** — message catalogs per locale, populated with the translated copy
6. **QA pass** — responsive check across breakpoints, structured data validation, SEO/GEO checklist verification

Each task note links back to `[[Tasks MOC]]` and to the brief note by name.

## Follow-Up

Once the brief is approved and task notes are created, these steps happen outside this skill:

- Invoke the confirmed design skill(s) from Step 3 while building the UI.
- Optionally run `/seo-audit` for deeper keyword research.
- Work through the task notes in `docs/05-Tasks/Todo/` in order, moving each to `docs/05-Tasks/Done/` as it's completed, to scaffold and build the Next.js + next-intl app.
