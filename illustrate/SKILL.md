---
name: ck-illustrate
description: Generate AI illustrations with style locking. Supports reference image injection, prompt iteration, and PURE STYLE TRANSFER for portraits. Preview candidates in browser.
---

# illustrate

Generate AI illustrations with style locking.

## Prerequisite

`DESIGN.md` must exist in the project root. The style tokens (palette, mood keywords, reference image paths) drive all prompt construction.

## Modes

### Guided mode (default)

Invoked with `/illustrate`.

1. **Read context** — Parse DESIGN.md for style tokens (palette, mood, reference images) and the story spec for scene descriptions.
2. **Propose prompts** — Draft prompts for each image needed (hook illustration, portraits, data visualization backgrounds, etc.). Show the user what will be generated.
3. **Generate images** — Send prompts + reference images to the configured image model.
4. **Preview** — Open candidates in the browser side-by-side via the browse skill for comparison.
5. **Iterate** — User requests adjustments ("more muted", "closer crop", "warmer palette", etc.). Re-generate with modified prompts.
6. **Save** — Approved images saved to `assets/images/`.

### Quick mode

Invoked with `/illustrate --quick`.

- Auto-generates all images from the story spec.
- Opens a preview grid in the browser.
- User batch-approves or flags specific images for re-generation.

## Key Techniques

### Style locking

Prompt text alone does not maintain style consistency across images. Always inject 2-3 reference images via multimodal input alongside the text prompt. The model uses these as style anchors.

### PURE STYLE TRANSFER (portraits of real people)

For real-person portraits:
- Feed an official photo of the person + a style reference image.
- The model redraws the person's likeness in your project's illustration style.
- This preserves identity while maintaining stylistic coherence.

### Dual-age reference (historical figures)

For historical figures where age matters:
- Inject both a young and old photo together.
- The model finds the bone-structure intersection, producing a recognizable portrait regardless of which era you're depicting.

### Negative prompts

Always include what NOT to do. Adapt to your project's style — common negatives include:
- No black outlines
- No cartoon/cel-shading
- No photorealism
- No flat-poster aesthetic

### Reference contamination warning

File names can be misleading. Before injecting a reference image, visually verify it actually matches your target style. A file named `serio_style_01.png` might not actually represent the Serio aesthetic.

## Output

Generated images saved to `assets/images/`, named by slide role and version (e.g., `hook_v1.png`, `portrait_munger_v2.png`).
