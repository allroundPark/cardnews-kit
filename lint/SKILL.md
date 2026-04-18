---
name: ck-lint
description: Quality gate for carousel templates. Checks color tokens, font usage, layout consistency, editorial rules, and Y-grid alignment. Called automatically by /render.
---

# lint

Quality gate for carousel templates.

## Invocation

- `/ck-lint` — standalone check
- Auto-called by `/ck-render` before any rendering begins

## Checks

All checks are driven by DESIGN.md and EDITORIAL.md tokens.

| Category | What it checks |
|---|---|
| Color | Background hex matches DESIGN.md tokens. Flag non-standard color values. |
| Font | Only approved fonts in `font-family` declarations. `@font-face` paths valid and relative. |
| Layout | Canvas dimensions match spec (e.g., 1080x1350). Padding values consistent across slides. |
| Typography | Y-grid alignment across similar slides — padding, font-size, min-height, margins must be consistent for same-role slides. |
| Editorial | Forbidden words from EDITORIAL.md. Uncited numbers (any numeric claim without a source). Missing source attributions. |
| Assets | Referenced images exist at their paths. Resolution adequate for the canvas size. |
| Consistency | Slide numbering sequential. Corner logo/watermark present on all slides that require it. |

## Output

Pass/fail report with:
- File path and line number for each issue
- Category of the violation
- Specific fix suggestion

Example:
```
FAIL  templates/03_detail_a.html:42  [Color]
      Background #F5F0E8 not in DESIGN.md palette. Did you mean #EDE3D2 (cream-paper)?

FAIL  templates/05_twist.html:18  [Editorial]
      Forbidden word "급등" found. Rephrase without sensational market language.

PASS  templates/01_hook.html  [All checks passed]
```

## Integration with /ck-render

`/ck-render` calls `/ck-lint` as its first step. If lint fails, rendering is blocked. There is no `--skip-lint` flag — the quality gate is non-negotiable.

## Implementation

Use grep/search on template HTML files. Extract CSS values and compare against DESIGN.md tokens. Parse text content and check against EDITORIAL.md forbidden word lists.
