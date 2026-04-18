---
name: ck-design-system
description: Generate design tokens from reference accounts or images. Auto-extracts colors, fonts, layout — then lets you customize. Produces DESIGN.md.
---

# design-system — Visual Design Token Generator

Generates a complete design system from reference material. The key principle: **extract from references first, ask questions second.** Benchmarking implies layout preference — so the skill leads with auto-extraction and shotgun previews, not interrogation.

## Flow

### Step 1: Collect Reference Material
Ask: "Have an account or image you want to pull style from?"

Accept one of:
- **Instagram account URL** — analyze the feed grid via Playwright (browse skill)
- **Image file(s)** — direct visual analysis of uploaded screenshots, mood boards, or saved posts
- **"Use benchmark results"** — reference the existing `BENCHMARK.md` for extracted patterns
- **None** — fall back to keyword-based generation ("minimal", "retro", "magazine", "editorial")

### Step 2: Auto-Extract Design Tokens
From the reference material, extract:
- **Canvas ratio** — detect the dominant aspect ratio (4:5, 1:1, 9:16)
- **Color palette** — background, primary text, accent, secondary accent (hex values)
- **Font direction** — serif, sans-serif, handwritten, monospace, mixed
- **Layout structure** — grid type, margin ratios, image-to-text ratio, alignment patterns
- **Decorative elements** — borders, shadows, gradients, textures, logo placement

### Step 3: Shotgun Mode
Generate **2-3 design variations** based on the extracted tokens, each with a different emphasis:
- Variation A: Closest to the reference
- Variation B: Same palette, different layout
- Variation C: Same layout, shifted palette or typography

Render all variations as HTML and show them **side-by-side in the browser** via the `browse` skill's comparison grid.

### Step 4: User Picks
Present the comparison and ask: "Which direction feels right? Pick one, or describe what you'd combine."

The user selects a variation (or describes a hybrid).

### Step 5: Customization (only if requested)
Ask: "Want to customize anything?" Only if the user says yes, drill into specifics:

- **Canvas ratio** — 4:5 (Instagram portrait) / 1:1 (square) / 9:16 (story/reel)
- **Colors** — background, text, accent — offer color picker or hex input
- **Font mood** — clean / handwritten / classic / bold — or specific font name
- **Logo/watermark** — placement, size, opacity

If the user says no, proceed with the selected variation as-is.

### Step 6: Generate DESIGN.md
Produce `DESIGN.md` containing:
- **Canvas** — dimensions, aspect ratio, device scale factor
- **Color tokens** — named colors with hex values and usage rules
- **Typography** — font family, weight scale, size scale, line height rules
- **Layout** — margin/padding system, grid structure, image-to-text ratio
- **Decorative** — borders, shadows, textures, logo specs
- **Slide type templates** — token combinations for hook slides, content slides, quote slides, closing slides

## Key Principle

> Benchmarking implies layout preference. Extract, don't interrogate.

The user already showed you what they like (via references or benchmark). Your job is to distill that into tokens and show concrete variations — not to ask 20 questions about color theory. Questions come after the user has seen options, not before.

## Output
`DESIGN.md` — placed in the project root. Referenced by `render`, `illustrate`, and all template-generation skills.
