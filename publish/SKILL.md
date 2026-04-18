---
name: ck-publish
description: Create the final publish bundle — Instagram caption, README with upload checklist, and organized file structure.
---

# publish

Create the final publish bundle for Instagram.

## Flow

1. **Verify prerequisites** — Read the story spec. Confirm rendered PNGs exist for all slides.
2. **Generate caption draft**:
   - **Hook line** — Priority order: number/data hook (strongest) > scene hook > signature hook > question hook (weakest).
   - **Body** — Narrative summary of the carousel story. Concise, readable on mobile.
   - **Source footer** — Citations for all data claims shown in the carousel.
   - **Disclaimer** — Standard investment disclaimer line.
   - **Hashtags** — 5-7 relevant hashtags.
3. **Present caption with hook options** — Show 2-3 hook variations ranked by strength. User picks or edits.
4. **Generate README.md**:
   - Upload order (slide sequence with file names)
   - Source list (all references used)
   - Pre-publish checklist (final checks before posting)
5. **Bundle into publish directory**:

```
publish/NNN_slug/
├── NN_role.png      (slides, numbered sequentially)
├── caption.txt      (Instagram body text)
├── README.md        (upload guide + sources + checklist)
└── src/             (template + script snapshot for reproducibility)
```

6. **Commit** — Create a git commit with a descriptive message referencing the post number and slug.

## Caption Structure

```
[Hook — 1-3 lines, strong opener]
─────────────────────
[Narrative body]
─────────────────────
[P.S. if applicable]
🔖 Save for later.
💬 Share with someone who needs this.
─────────────────────
📎 Sources
⚠️ Disclaimer
#hashtags
```

## Output

Complete publish-ready bundle in `publish/NNN_slug/` with all files needed to post directly to Instagram.
