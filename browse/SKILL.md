---
name: browse
description: Browser infrastructure for visual preview. Opens HTML in Playwright for comparison, review, and analysis. Used by design-system (shotgun), illustrate (preview), render (compare), and benchmark (feed analysis).
---

# browse — Shared Browser Infrastructure

This is **not a user-facing skill**. It is shared infrastructure that other skills call when they need to show something visually.

## Capabilities

- **Open local HTML files** in a headless Playwright (Chromium) browser
- **Take screenshots** at specified viewport sizes (default: 1080x1350 for cardnews, adjustable)
- **Side-by-side comparison grids** — render multiple HTML files or design variants into a single comparison view
- **Responsive preview** — render the same HTML at multiple viewport widths to check layout breakpoints

## How Other Skills Use This

Other skills generate HTML (a comparison board, a slide preview, a feed mockup) and then request browser preview through this infrastructure.

| Caller Skill | What It Sends | What It Gets Back |
|---|---|---|
| `design-system` | 2-3 design variation HTML files | Side-by-side comparison grid screenshot |
| `benchmark` | Instagram feed page URL | Screenshots + extracted visual patterns |
| `render` | Slide HTML templates | 1080x1350 PNG screenshots per slide |
| `illustrate` | Preview HTML with embedded images | Visual preview for user confirmation |

## Implementation Notes

- Uses Playwright with Chromium (`device_scale_factor=2` for retina-quality output)
- Waits for `document.fonts.ready` before screenshotting to prevent font-loading races
- Comparison grids are generated as a temporary HTML page that arranges variants side-by-side, then screenshotted as a single image
- All browser operations are headless by default — output is always a screenshot or extracted data, never a live window
- Temporary HTML files are written to a scratch directory and cleaned up after use
