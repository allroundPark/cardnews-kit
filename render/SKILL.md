---
name: render
description: Render HTML templates to PNG via Playwright. Auto-runs /lint first. Generates compare.html for browser review of all slides.
---

# render

Render HTML templates to PNG via Playwright.

## Flow

1. **Lint gate** — Auto-call `/lint`. Must pass with zero failures. No override available.
2. **Locate templates** — Find all HTML templates for the current post (ordered by slide number).
3. **Launch Playwright** — Open headless Chromium.
4. **Render each slide**:
   - Navigate to the template via `file://` URL
   - Wait for fonts to load (`document.fonts.ready`)
   - Screenshot at canvas dimensions multiplied by `device_scale_factor` (from DESIGN.md)
5. **Generate compare.html** — Create a grid view of all rendered slides for side-by-side review.
6. **Browser preview** — Open compare.html in the browser via the browse skill. User reviews all slides together.
7. **User confirmation** — User approves the renders or requests changes.
8. **Save** — Write final PNGs to the output directory.

## Key Settings (from DESIGN.md)

- **Canvas size** — e.g., 1080x1350 (4:5 Instagram portrait)
- **device_scale_factor** — e.g., 2 for retina-quality output
- **Font wait strategy** — `document.fonts.ready` promise before screenshot

## Output

- PNG files per slide in the output directory
- `compare.html` for visual review

## Post-render Verification

After rendering, read the actual PNG files to verify:
- Text is legible (not clipped, not overflowing)
- Contrast is sufficient (text against background)
- Font rendering is correct (no fallback boxes for Korean characters)
- Layout matches the intended design

Do not assume the HTML looks correct — always check the rendered output. HTML rendering and Playwright screenshot rendering can differ.
