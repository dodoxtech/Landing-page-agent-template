# Product Imagery Reference

Used by `landing-page-builder` when the user has real product photos to feature (as opposed to skills that generate reference imagery from scratch, like `imagegen-frontend-web`). Covers how many photos are needed, how they should be shot/framed, how people should appear relative to the product, and file naming.

## How many photos

Scope the shot list to the sections actually used in the brief (Step 2), not a fixed number:

| Section | Photos needed |
|---|---|
| Hero | 1 primary shot, optionally 2-3 variants (e.g. wide vs. tight crop) to pick from |
| Features | 1 per feature *only if* the feature is visual/physical enough to show; skip for purely software/abstract features |
| Social proof | 1 headshot per testimonial (if using named quotes), or logo files for companies |
| Footer / About | Optional — team or office photo, only if the brand tone calls for it (see Step 3 design direction) |

A typical page needs **3-6 photos total**: 1 hero + 2-3 supporting + optional social proof headshots. More than that usually means some are decorative rather than load-bearing — check each one earns its place before asking the user to shoot/upload it.

## Framing and angle

- **Product-only shots (hero, feature close-ups)**: 3/4 angle to show depth and material, or a clean flat-lay/straight-on shot for flat objects and screenshots. Leave 40-60% negative space on one side of the frame — that's where the headline/CTA overlays in code. Product should fill the remaining 40-60%, not float lost in empty space.
- **Lifestyle / people-using-product shots**: eye-level or slightly above the subject — avoid shooting down (reads as condescending) or sharply up (reads as artificially aspirational unless that's the intentional tone). The person's gaze or body should angle *toward* the product or toward where the CTA/text will sit — this leads the viewer's eye in the same direction, a well-established visual-flow technique.
- **Never make a person's face the dominant focal point when the product is the message.** The person should be secondary — interacting with the product, not staring straight at the camera in a stock-photo grin. If the brief's goal is trust/relatability (see Step 3), a candid, mid-action moment reads as more credible than a posed smile.
- **Feature close-ups**: consistent lighting angle and color temperature across every feature shot, so the set reads as one cohesive shoot even if photos were taken separately.
- **Social proof headshots**: same crop shape (circle or rounded-square) and consistent lighting/white balance across all of them — a row of mismatched headshots undercuts credibility more than having none.
- **Representation**: if lifestyle photos include people, check they roughly match the target audience described in Step 1 (age range, context of use) — a mismatch reads as inauthentic.

## Text in images

Don't burn translatable text (headlines, CTAs, captions) into the image itself — it breaks i18n (Step 4) since the image would need a separate version per locale. Keep text as HTML/CSS overlay on top of the image, and reserve baked-in text only for genuinely decorative or brand-mark elements (e.g. a logo watermark).

## File naming

Use `section-purpose-variant.ext`, lowercase, hyphen-separated, no spaces or locale text baked into the name unless the *asset itself* differs per locale (rare — usually only OG images with baked-in text need locale suffixes):

```
hero-main.jpg
hero-main-mobile.jpg
feature-01-detail.jpg
feature-02-detail.jpg
social-proof-jane-doe.jpg
og-image.jpg
og-image-vi.jpg        (only if OG image has locale-specific baked-in text)
```

## When AI generation or editing is needed

- **Missing shot for a section**: if the user has no real photo for a section that needs one, generate a reference image via `imagegen-frontend-web` instead of leaving a placeholder.
- **Enhancing real photos**: real uploads can be color-graded to match the confirmed design direction (Step 3), have backgrounds cleaned up, or be upscaled if low-resolution — but this is an **enhance, don't replace** operation: the actual product and any person's identity must stay recognizable and accurate. AI must never alter the product's real appearance, add features it doesn't have, or fabricate a different person.
- **Always confirm before and after** any AI edit that materially changes how the photo looks (background swap, heavy color grade, generative fill) — since it directly affects how the real product is represented, this can't be finalized without the user seeing and approving the result.
