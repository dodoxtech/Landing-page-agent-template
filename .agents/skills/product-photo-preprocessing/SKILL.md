---
name: product-photo-preprocessing
description: Preprocesses a user's uploaded product photos before they go into a landing page — assesses what's usable, decides which sections still need a shot, fills gaps with AI-generated imagery, enhances real photos to match the confirmed design direction, and renames everything to a consistent file scheme. Use when the user has uploaded real product/lifestyle photos for a landing page and needs them turned into a ready-to-use image set.
---

# Product Photo Preprocessing

## Trigger

User uploads real product or lifestyle photos for a landing page and needs them assessed, cleaned up, gap-filled, and organized before they're placed into sections. Typically called from `landing-page-builder` once section content (Step 2) and design direction (Step 3) are confirmed, since both are needed inputs here.

## Inputs

- The uploaded photo files
- The confirmed section list from the brief (which sections need imagery, per [Product Imagery Reference](../landing-page-builder/references/product-imagery.md#how-many-photos))
- The confirmed design direction from Step 3 (tone + aesthetic), so enhancement matches it rather than guessing a look

If the brief/design direction isn't confirmed yet, ask for them rather than assuming — enhancement decisions depend on both.

## Process

### 1. Inventory and assess
Read every uploaded photo. For each, note: resolution/usable quality, what it shows (product-only vs. lifestyle-with-person), and which section it's a candidate for. Flag any that are too low-resolution, poorly lit, or off-brief to use as-is.

### 2. Match photos to sections
Using the "How many photos" table in [Product Imagery Reference](../landing-page-builder/references/product-imagery.md), assign each usable photo to a section. Check framing against that reference's angle/composition rules (negative space for hero, gaze direction for lifestyle shots, consistent lighting across feature shots and headshots). Flag mismatches instead of forcing a bad-fit photo into a section.

### 3. Identify gaps
List sections that need a photo but have no usable upload. For each gap, ask the user: "generate one" or "skip this section." Don't silently drop a section's imagery without flagging it.

### 4. Fill gaps with generation
For confirmed gaps, invoke `imagegen-frontend-web` (or `imagegen-frontend-mobile` if the section is a device-mockup context) to generate a reference image matching the confirmed design direction and the section's role. This is new imagery, not an edit of a real photo — no product-identity constraint applies here since nothing real exists yet to misrepresent.

### 5. Enhance real photos
For usable real photos that need to match the confirmed design direction (color grade, background cleanup, upscaling), apply an **enhance, don't replace** pass: adjust lighting/color/background treatment, but never alter the actual product's appearance, add features it doesn't have, or change a real person's identity. Show before/after for any edit that materially changes how the photo looks, and get explicit confirmation before finalizing — this can't be automated past that checkpoint since it affects how a real product is represented.

### 6. Rename and finalize
Rename every final file (real or generated) per the naming scheme in [Product Imagery Reference](../landing-page-builder/references/product-imagery.md#file-naming) (`section-purpose-variant.ext`). Confirm no translatable text is baked into any image per that reference's "Text in images" rule.

## Output

A confirmed image manifest: final filename, source (real upload vs. AI-generated vs. real+enhanced), and target section for each image. Hand this list back to the caller (e.g. `landing-page-builder`) to reference in the brief and later in the build task for that section — this skill does not scaffold code itself.

## Links
- Reference: [Product Imagery Reference](../landing-page-builder/references/product-imagery.md)
- Used by: `landing-page-builder`
- Delegates to: `imagegen-frontend-web`, `imagegen-frontend-mobile`
