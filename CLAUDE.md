# CLAUDE.md

Master instructions for Claude Code when working in a cardnews-kit project.

## Project

cardnews-kit is a Claude Code skill pack for building editorial Instagram carousels. It provides a repeatable pipeline from benchmarking and identity setup through story writing, illustration, rendering, and publishing.

## Critical: First-Time Setup

If `PHILOSOPHY.md` does not exist in the project root, the user has not onboarded yet. Suggest running `/ck-onboard` before any production skills. Onboarding is required — without it, skills like `/ck-lint` and `/ck-illustrate` have no design system or voice to reference.

## Available Skills

### Phase 1 — Onboard (run once)

| Skill | What it does |
|---|---|
| `/ck-onboard` | Interactive project setup: mission, audience, topic, directory structure |
| `/ck-benchmark` | Analyze reference accounts, extract visual and editorial patterns |
| `/ck-design-system` | Define colors, typography, layout grid, visual tokens → `DESIGN.md` |
| `/ck-voice` | Define editorial tone, forbidden terms, copy rules → `EDITORIAL.md` |

### Phase 2 — Produce (per post)

| Skill | What it does |
|---|---|
| `/ck-story` | Research and structure a carousel narrative arc |
| `/ck-factcheck` | Verify every number and claim against primary sources |
| `/ck-illustrate` | Generate AI illustrations matching the design system |
| `/ck-lint` | Validate slides against design system + editorial voice |
| `/ck-render` | Render HTML → 1080x1350 PNG via Playwright |
| `/ck-publish` | Bundle slides, caption, metadata for upload |
| `/review` | Pre-publish editorial and visual check |

All production skills support `--quick` mode for faster iteration.

## Onboarding Outputs

Running the Phase 1 skills produces these files in the user's project:

- `PHILOSOPHY.md` — Account mission, audience, topic, and creative direction
- `BENCHMARK.md` — Analysis of reference accounts and extracted patterns
- `DESIGN.md` — Design system: colors, typography, layout, visual tokens
- `EDITORIAL.md` — Editorial voice, tone, forbidden terms, copy guidelines
- `CLAUDE.md` — Project-specific Claude Code instructions (generated from kit templates)

## Dependencies

- **Core:** Playwright (Chromium) — required for rendering HTML slides to PNG
- **Adapters (optional):** Image generation (Gemini, DALL-E, etc.), data verification APIs (FMP, Yahoo Finance, etc.), publishing integrations

Install core dependencies with `./setup` in the kit root.

## Language

- Skill instructions and system files are written in English
- Content (slides, captions, copy) is written in the user's language
- Follow the user's language for conversation

## Philosophy

The kit's philosophy is documented in [ETHOS.md](ETHOS.md). Three core beliefs:

1. Your taste is the product
2. Content is the root
3. Making closes the gap

User projects express their own philosophy in `PHILOSOPHY.md`, generated during onboarding.

## Adapters

Adapters in `adapters/reference/` provide integration templates for swappable tools:

- Image generation (Gemini, DALL-E, Midjourney)
- Data/fact verification APIs
- Publishing targets (Instagram, Threads, blog platforms)

Adapters are optional — the core pipeline works without them.
