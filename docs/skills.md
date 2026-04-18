# cardnews-kit — Skills Philosophy & Workflow

## Core Idea

cardnews-kit turns a proven editorial carousel workflow into reusable Claude Code skills.
The process was extracted from a real Instagram account with 13 published posts across
investment philosophy — but the skills are topic-agnostic.

Finance, design, food, architecture, travel, education — change the topic,
keep the pipeline.

## Two Phases

### Phase 1: Onboard (once per project)

Set up your creative identity. This happens once when you start a new content project.

```
/onboard
  ├── ETHOS presentation ("here's what this kit believes")
  ├── Philosophy questions → PHILOSOPHY.md
  ├── /benchmark → BENCHMARK.md
  │     └── Reference account analysis
  │     └── Story arc/rhythm extraction
  │     └── User confirms preferred flow
  ├── /design-system → DESIGN.md
  │     └── Reference → auto-extract tokens
  │     └── Shotgun: 2-3 variations in browser
  │     └── User picks, optionally customizes
  ├── /voice → EDITORIAL.md
  │     └── Tone, forbidden terms, arc template
  └── CLAUDE.md auto-synthesized
```

After onboarding, your project has 5 foundational documents that every
production skill reads.

### Phase 2: Produce (each post)

Create content. This is the repeatable cycle for every post.

```
/story → /factcheck → /illustrate → /lint → /render → /publish
```

Each skill reads your onboarding documents (DESIGN.md, EDITORIAL.md, etc.)
and applies your established rules automatically.

## Skill Interaction Modes

**Guided (default):** Step-by-step questions with choices. Best for:
- First-time users learning the process
- Complex posts requiring research
- Posts where you want to explore options

**Quick (`--quick`):** One-shot execution from minimal input. Best for:
- Experienced users who know their workflow
- Simple posts with clear topics
- Batch production

Example: `/story --quick "Cisco 20-year chart — the price of being #1"`

## Key Design Principles

### Extract, Don't Interrogate

When a user benchmarks an account, they already like that account's visual style
and content rhythm. `/design-system` extracts tokens from references first,
then asks if the user wants to modify — instead of starting with blank-slate questions.

### Quality Gate is Non-Negotiable

`/lint` runs automatically before every render. There is no `--skip-lint` flag.
This exists because real production revealed:
- Color hex drift across posts (4 different "cream" values in one project)
- Font fallback failures (Korean text rendering as boxes)
- Y-grid misalignment between similar slides

### Source Grading, Not Source Trusting

`/factcheck` uses a 4-tier system because AI research agents tend to
self-promote secondary sources as primary:
- ✅ Direct primary source accessed
- ✅* Secondary consensus (multiple reliable sources agree, but primary not accessed)
- ⚠️ Direction right, magnitude off
- ❌ Wrong

The anti-pattern: "Multiple websites cite the same number, so it must be primary."
No — trace to the actual book page, video timestamp, or official document.

### Your Taste, Not AI's Taste

`/illustrate` generates candidates. You pick. The skill never auto-selects
the "best" image — because "best" is a taste judgment that belongs to you.

Style locking (reference image injection) exists precisely so the AI reproduces
YOUR aesthetic, not its default aesthetic.

## Browser as First-Class Citizen

Multiple skills use Playwright's browser for visual review:

| Skill | Browser use |
|---|---|
| `/benchmark` | Browse reference account feeds |
| `/design-system` | Shotgun comparison of design variations |
| `/illustrate` | Side-by-side image candidate preview |
| `/render` | Compare.html grid of all slides |

This is why Playwright is a core dependency, not an adapter.

## What Onboarding Produces

```
my-project/
├── PHILOSOPHY.md    ← Your content philosophy
├── BENCHMARK.md     ← Reference analysis + arc patterns
├── DESIGN.md        ← Design tokens (colors, fonts, layout)
├── EDITORIAL.md     ← Voice rules, forbidden terms, arc templates
└── CLAUDE.md        ← Auto-synthesized master instructions
```

## What Each Post Produces

```
my-project/
├── stories/NNN_slug.md           ← Content spec (/story)
├── assets/images/NNN_*           ← Illustrations (/illustrate)
├── templates/NNN_*.html          ← Slide templates (/render input)
└── publish/NNN_slug/
    ├── NN_role.png               ← Final slides (/render)
    ├── caption.txt               ← Instagram caption (/publish)
    ├── README.md                 ← Upload guide (/publish)
    └── src/                      ← Template snapshot (/publish)
```
