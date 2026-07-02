---
name: design-aesthetics
description: Catalog of design aesthetics (50+ named visual styles, from classical/ornate to internet-native trends) with concrete visual characteristics (color, type, layout, motion, texture), the moods/industries each fits, and which design skill(s) in this repo best execute each one. Reference this before recommending a design direction — don't invent aesthetic descriptions from scratch or rely on a stale mental list of trends.
---

# Design Aesthetics Catalog

A reference catalog other skills (especially `landing-page-builder`) consult when they need to recommend a design direction. This skill does not run an interview and does not produce output files — it's a lookup.

## How to use this catalog

1. Given a stated emotional tone, industry, and any reference brands, scan the tables below for the closest-matching aesthetic(s). Aesthetics are grouped by family to make scanning faster.
2. Read the matched aesthetic's characteristics to ground the recommendation in specifics (name the actual visual traits), not just a vibe word.
3. Use the "Repo skill(s)" column to know what to invoke for execution. Many of these 50 styles are illustration/branding aesthetics rather than web-UI systems — where no repo skill directly covers one, the table says so and points to `frontend-design` (general grounding) plus `imagegen-frontend-web` (generate reference imagery before implementing custom CSS/illustration).
4. Styles can be blended (e.g. "Vaporwave x Gothic," "Luxury Typography meets Aurora") — naming the blend explicitly to the user and to whichever skill executes it produces sharper results than a single vague mood word.
5. **This list can go stale.** If the user names a reference or trend not covered here, or the industry calls for something clearly not represented, use WebSearch to check what's currently trending before falling back to a generic pick. If you confirm a new aesthetic is genuinely trending and recurring, add a row to the appropriate table below so the catalog stays current.

## Catalog

### Classical & Ornate

| Aesthetic | Visual characteristics | Fits when... | Repo skill(s) |
|---|---|---|---|
| **Neoclassical** | Serif fonts, columns, laurel wreaths, marble textures, gold accents, symmetry, muted palettes | Formal, timeless, noble; luxury brands, heritage, academic | `high-end-visual-design` |
| **Baroque** | Ornate flourishes, deep shadows, gold leaf, mythological motifs, rich textures, high contrast | Regal, dramatic, celebratory; premium packaging, lavish editorial | `high-end-visual-design`, blended with reference imagery via `imagegen-frontend-web` |
| **Filigree** | Delicate metallic linework, lacy embellishments, monogram fonts | Old-world luxury, ceremonial, heritage branding | `high-end-visual-design` |
| **Acanthus** | Leaf/vine motifs, symmetrical curves, stone textures, natural gold/green | Regal but organic; premium, classical branding | `high-end-visual-design` |
| **Victorian** | Ornate serif type, damask patterns, deep reds/greens, gilded frames, heavy florals | Opulent, historical, romantic storytelling | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **Art Deco** | Gold accents, sunbursts, symmetry, angular shapes, jewel tones, flair sans-serifs | Glamorous, upscale, retro-modern | `high-end-visual-design` |
| **Art Nouveau** | Curving organic lines, floral motifs, hand-lettered type, earthy palettes | Romantic, poetic, artisan/natural cosmetics | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **Luxury Typography** | Refined serif letterforms, high letter-spacing, gold foil, monochrome, bespoke ligatures | Elegant, elite; fashion, beauty, high-end editorial | `high-end-visual-design` |

### Nature & Organic

| Aesthetic | Visual characteristics | Fits when... | Repo skill(s) |
|---|---|---|---|
| **Japandi** | Light woods, beige/gray palette, clean sans-serif, minimal icons, natural materials | Calm, intentional; lifestyle, home, wellness | `minimalist-ui` |
| **Wabi Sabi** | Earthy tones, rough/natural textures, asymmetry, minimal sans-serif | Humble, contemplative; wellness, tea, mindful products | `minimalist-ui` |
| **Farmhouse / Cottagecore** | Florals, gingham, wood textures, antique finishes, serif/hand-drawn type | Cozy, wholesome; lifestyle, recipe, rustic brands | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **Bohemian** | Rich textures, mandalas, jewel tones, ethnic prints, script fonts | Free-spirited; handmade, travel, artisanal | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **Shabby Chic** | Whitewashed/distressed textures, faded florals, cursive type, soft pastels | Romantic, cozy, nostalgic; weddings, vintage boutiques | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |

### Retro-Futurism & Internet Nostalgia

| Aesthetic | Visual characteristics | Fits when... | Repo skill(s) |
|---|---|---|---|
| **Y2K** | Chrome textures, pixel fonts, metallic finishes, iridescent gradients, matrix grids | Futuristic-nostalgic, edgy; Gen-Z fashion, tech revival | `gpt-taste` |
| **Neo Frutiger Aero** | Aqua blues, glossy bubble gradients, rounded friendly sans-serif, transparent UI | Clean futuristic-nostalgic; fintech, Web3, playful tech | `high-end-visual-design` blended with `gpt-taste` |
| **Synthwave** | Grid horizons, VHS texture, neon gradients, 3D chrome type, purple/cyan palette | Retro-futuristic, vibrant; music, arcade, nostalgia apps | `gpt-taste` |
| **Vaporwave** | Pastel pink/purple, VHS glitch, classical statues, lo-fi textures | Ironic, dreamy nostalgia; indie music, zines, anti-establishment | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **Cybercore** | Neon, glitch effects, code patterns, green/black, tech symbology | Futuristic, dystopian; tech events, hacker/gaming culture | `industrial-brutalist-ui` |
| **Glassmorphism** | Frosted-glass translucency, background blur, soft borders, layered depth | Modern, sleek, "premium OS" feel; use sparingly, ages fast | `high-end-visual-design` |
| **Steampunk** | Copper tones, cogwheels, leather, serif type, steam/smoke motifs | Adventurous, vintage-futuristic; games, books, imaginative brands | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |

### Structural, Functional & Minimal

| Aesthetic | Visual characteristics | Fits when... | Repo skill(s) |
|---|---|---|---|
| **Bauhaus** | Grid systems, sans-serif, primary red/blue/yellow, basic geometric shapes | Rational, modernist; architecture, clean brand systems | `minimalist-ui` |
| **Brutalism** | Monospaced fonts, grayscale, harsh edges, solid blocks, unstyled default UI | Bold, disruptive, honest; artist portfolios, counterculture | `industrial-brutalist-ui` |
| **Neo-Brutalism** | Bold flat colors, large type, stark layouts, purposeful asymmetry, minimal chrome | Confident, bold, raw-yet-usable; dev/indie/creative agency sites | `industrial-brutalist-ui` |
| **Utilitarian** | Grid layout, industrial/monospace fonts, muted tones, no decoration | Practical, minimal, efficient; technical/utility interfaces | `industrial-brutalist-ui` or `minimalist-ui` |
| **Bento Box** | Rounded modular blocks, subtle shadows, labeled icons, micro-animations | Organized, friendly, clean; dashboards, portfolios, product pages | `gpt-taste` (gapless bento grids) |
| **Modular Typography** | Type broken into grids/building blocks, uniform spacing, variable layout | Structural, experimental; posters, branding systems | `design-taste-frontend` |
| **Mid-Century** | Clean lines, retro color, boomerang/mod patterns, sans-serif | Nostalgic-optimistic; furniture, lifestyle, editorial | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |

### Playful & Character-Driven

| Aesthetic | Visual characteristics | Fits when... | Repo skill(s) |
|---|---|---|---|
| **Anthropomorphic** | Human traits on objects/mascots, expressive icons, rounded friendly shapes | Fun, relatable; kids' products, gamified UX | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **Pixel Art** | Grid-based visuals, low-res icons, limited palette, 8-/16-bit look | Nostalgic, geeky; indie games, retro-themed brands | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **Kawaii** | Pastel colors, rounded icons, blushing/cute faces, handwritten type | Sweet, joyful; stationery, kids' products, whimsical brands | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **Coquette** | Baby pinks, pearls, ribbon motifs, dainty serif, heart shapes | Delicate, girly, nostalgic; beauty, fashion, romantic lifestyle | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **Memphis** | Squiggles, bright primaries, clashing colors, block shapes, cartoonish motifs | Youthful, quirky, anti-establishment; creative brands, events | `gpt-taste` |
| **Kitsch** | Clashing prints, outdated fonts, shiny plastic textures, ironic excess | Campy, fun, ironic; parody, Gen-Z fashion, nostalgic remixes | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **Pop Art** | Ben-Day dots, bold outlines, primary colors, comic/display fonts | Loud, fun, energetic; pop-culture campaigns, retail | `gpt-taste` |
| **Rebus** | Pictograms, visual puns, image-type hybrids, clean layout | Witty, playful, intellectual; puzzles, brand storytelling | `design-taste-frontend` |

### Dark & Moody

| Aesthetic | Visual characteristics | Fits when... | Repo skill(s) |
|---|---|---|---|
| **Tenebrism** | High-contrast chiaroscuro, black backgrounds, spotlighting | Intense, emotional, moody; cinematic/storytelling visuals | `high-end-visual-design` |
| **Gothic** | Blackletter fonts, stained-glass texture, stone motifs, deep purple/black | Dark, dramatic, historic; fantasy, alt fashion, music posters | `industrial-brutalist-ui` blended with reference imagery |
| **Dark Academia** | Candles, spellbooks, antique etchings, black/gold palette, serif calligraphy | Mysterious, scholarly; fantasy games, book brands | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |

### Street, Subculture & Regional

| Aesthetic | Visual characteristics | Fits when... | Repo skill(s) |
|---|---|---|---|
| **Graffiti** | Spray-paint texture, dripping letters, concrete backgrounds, neon, freestyle type | Urban, defiant, expressive; streetwear, music festivals | `gpt-taste` blended with reference imagery |
| **Mystical Western** | Tarot symbols, cacti, western serif, sun/moon motifs, leather textures | Mystical, rugged, folklore; crystal shops, tarot apps | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **South West / Wild West** | Terracotta, cacti, denim texture, cowboy motifs, serif western type | Rugged, adventurous, heritage; outdoor/ranch brands | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **Nautical** | Navy/white, anchors, rope, stripes, brass, serif or stencil type | Fresh, structured, maritime; seafood, coastal, summer brands | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |

### Artistic & Expressive

| Aesthetic | Visual characteristics | Fits when... | Repo skill(s) |
|---|---|---|---|
| **Aurora** | Iridescent gradients, blur/glow, translucent overlays, organic wave forms | Dreamy, futuristic; wellness apps, tech launches, spiritual themes | `high-end-visual-design` |
| **Ethereal** | Light pastels, gauzy overlays, minimal serif, low contrast, feathered shadows | Calm, mystical, romantic; spiritual, high fashion, mindfulness | `minimalist-ui` blended with `high-end-visual-design` |
| **Conceptual Sketch** | Pencil/ink lines, crosshatching, greyscale, annotations, sketch texture | Experimental, informal, idea-driven; portfolios, design journals | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **Pointillism** | Dot-cluster texture, optical color mixing, pastel/impressionist palette | Artistic, textured, tranquil; fine-art branding, editorials | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **Mixed Media** | Cutouts, overlays, analog+digital collage, paper textures | Eclectic, avant-garde; magazines, experimental branding | `design-taste-frontend` |
| **Surrealism** | Dreamlike collage, disjointed objects, melting forms, unexpected scale | Thought-provoking, unsettling; concept art, literary design | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |
| **Light Academia** | Creamy neutrals, serif type, books/sunlight imagery, linen texture | Scholarly, calm, refined; journals, study apps, aesthetic fashion | `minimalist-ui` |
| **Scrapbook** | Paper texture, washi tape, Polaroid frames, hand lettering, stickers | Sentimental, warm, nostalgic; journaling apps, memory branding | No direct repo skill — ground via `frontend-design` + `imagegen-frontend-web` |

## Source

Aesthetic names and characteristics adapted from Himanshu Bhardwaj, ["50 Design Styles Every Designer Should Know for Better Prompting"](https://uxplanet.org/50-design-styles-every-designer-should-know-for-better-prompting-56c09d55db62), UX Planet — condensed here for design-direction lookup, plus this repo's own pre-existing entries mapped to available skills.

## Links
- Used by: `landing-page-builder` (Step 3 — Emotional tone → design direction)
