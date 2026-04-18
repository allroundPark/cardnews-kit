---
name: benchmark
description: Analyze reference accounts and extract visual patterns, content strategies, and story arc rhythms. Produces BENCHMARK.md.
---

# benchmark — Reference Account Analysis

Analyzes accounts and content the user admires to extract actionable patterns for their own project. The output is `BENCHMARK.md`, which downstream skills (`design-system`, `voice`) reference.

## Flow

### Step 1: Collect References
Ask: "Do you have reference accounts or content you admire?"

Accept any of these input types:
- **Instagram account URLs** — e.g., `https://instagram.com/some_account`
- **Website URLs** — blog, newsletter, or portfolio pages
- **Image files** — screenshots, mood boards, saved posts
- **Keywords** — "minimal finance", "editorial magazine", "retro illustration"

If the user provides nothing, suggest browsing popular accounts in their stated niche (from PHILOSOPHY.md if available).

### Step 2: Browse and Extract
For each reference, use Playwright (via `browse` skill) to navigate and analyze:

**Visual patterns:**
- Dominant color palette (extract hex values)
- Typography direction (serif, sans-serif, handwritten, mixed)
- Layout structure (grid, freeform, magazine, card)
- Image style (photography, illustration, mixed media, text-only)
- Canvas ratio and slide dimensions

**Content patterns:**
- Post frequency and consistency
- Slide count per post (range and mode)
- Topic categories and recurring themes
- Caption style (length, tone, hashtag usage)

**Story arc / rhythm** (analyze the slide sequence within posts):
- Where does the hook land? (slide 1 always? or delayed?)
- Where is the turn or twist?
- How do they close? (CTA, question, summary, quote)
- Is there a consistent arc template across posts?

### Step 3: Present Analysis
Show the analysis with screenshots in the browser. For each reference:
- Key screenshots annotated with extracted patterns
- Summary of visual system
- Summary of story arc rhythm

### Step 4: Confirm Preferences
For each extracted pattern, ask the user:
- "This account uses [X] flow rhythm. Do you like this? Want to adopt or modify?"
- "Their color palette is [X]. Attractive to you, or different direction?"
- "They close with [X]. Does that match your style?"

The user confirms, modifies, or rejects each pattern.

### Step 5: Generate BENCHMARK.md
Produce `BENCHMARK.md` containing:
- **References analyzed** — list of accounts/sources with URLs
- **Visual patterns extracted** — colors, typography, layout, image style
- **Content patterns** — frequency, slide count, topics
- **Story arc patterns** — hook/turn/close structure (user-confirmed)
- **Adoption vs. differentiation notes** — what the user wants to keep, what they want to do differently

## Output
`BENCHMARK.md` — placed in the project root. Referenced by `design-system` and `voice` skills.
