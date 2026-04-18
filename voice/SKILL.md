---
name: ck-voice
description: Define editorial voice, forbidden terms, tone rules, and story arc templates. Produces EDITORIAL.md.
---

# voice — Editorial Voice Definition

Defines how the account speaks, what it never says, and the structural rhythm of its posts. The output is `EDITORIAL.md`, the authoritative reference for all copy generation.

## Flow

### Step 1: Voice Questions (4-5 questions, one at a time)

Ask these sequentially. **Wait for the answer before asking the next question.**

1. **"How do you talk to your readers?"**
   Offer options alongside freeform:
   - Friend — casual, first-person, conversational
   - Teacher — explanatory, structured, clear
   - Journalist — neutral, fact-forward, observational
   - Essayist — reflective, opinionated, literary
   - Or describe your own tone

2. **"Any words or phrases you'll never use?"**
   Prompt for forbidden terms. Examples to seed the conversation:
   - Hype language (e.g., "explosive growth", "must-buy")
   - Clickbait patterns (e.g., "you won't believe", "secret trick")
   - Jargon the audience won't know
   - Competitor-associated phrases

3. **"How many slides per post typically?"**
   Offer ranges:
   - 3-5 (short, punchy)
   - 6-8 (standard narrative arc)
   - 9-10 (deep dive)
   - Variable (depends on topic)

4. **"How do you close a post?"**
   Offer options:
   - Question — leave the reader thinking
   - Summary — recap the key point
   - CTA — direct action (save, share, comment)
   - Reflection — open-ended musing
   - Quote — end with someone else's words

5. (Optional) **"What's the emotional arc you want readers to feel?"**
   - Curiosity → understanding → conviction
   - Surprise → context → reflection
   - Tension → reveal → calm
   - Or describe your own

### Step 1b: Caption Style Questions (4 questions, one at a time)

After the voice questions, ask these sequentially. **Wait for the answer before asking the next question.**

6. **"Caption first-line style?"**
   Offer options:
   - Number anchor — lead with a specific stat or data point
   - Scene description — set a visual or narrative scene
   - Question — open with a question to the reader
   - One-line declaration — bold single-sentence statement

7. **"Caption closing?"**
   Offer options:
   - Save CTA — end with a save/share call-to-action
   - Reflection — close with an open-ended thought
   - None — no explicit closing, let the content stand

8. **"Use hashtags?"**
   Offer options:
   - Yes — include hashtags (ask: how many? 3-5 / 5-10 / 10+)
   - No — no hashtags

9. **"Source citation style?"**
   Offer options:
   - Detailed — full source names, dates, page numbers in caption footer
   - Brief — short source references (e.g., "Source: FMP, 2024")
   - None — no citations in caption (sources live only in README)

### Step 2: Cross-Reference with Benchmark
If `BENCHMARK.md` exists, surface the story arc patterns extracted from references:

"Your benchmarks show that [reference account] uses this rhythm: [hook on slide 1 → context on 2-3 → turn on 5 → close with question on 7]. Keep this, or modify?"

The user confirms, adjusts, or rejects the benchmark arc.

### Step 3: Synthesize Arc Template
Combine the user's answers with any adopted benchmark patterns into a story arc template:

- **Hook** (slide 1) — what grabs attention, constraints on length/tone
- **Context** (slides 2-3) — setup, background, framing
- **Development** (slides 4-6) — detail, evidence, narrative build
- **Turn** (slide N-2) — twist, surprise, reframe
- **Close** (final slide) — chosen closing style from Step 1

### Step 4: Generate EDITORIAL.md
Produce `EDITORIAL.md` containing:

- **Voice profile** — tone descriptor, POV (first/second/third), formality level
- **Forbidden terms** — explicit list of words and phrases that must never appear in copy
- **Slide count guidance** — target range, when to go shorter or longer
- **Story arc template** — slide-by-slide role assignments with constraints
- **Closing style** — chosen close pattern with examples
- **Continuity rules** — terms introduced on slide N must pay off on slide N+1 (not left dangling)
- **Caption style** — first-line style, closing pattern, hashtag policy, source citation style
- **Quality checklist** — pre-publish checks for voice consistency

## Rules

- **One question at a time.** Do not batch questions.
- **Offer concrete options.** Every question should have selectable choices plus a freeform option. Do not leave the user staring at a blank prompt.
- **Reference benchmarks when available.** The user already showed what they like. Use that data to accelerate the conversation.
- **Forbidden terms are non-negotiable once set.** They go into `EDITORIAL.md` and are enforced by downstream skills (lint, editorial-check).

## Output
`EDITORIAL.md` — placed in the project root. Referenced by `story`, `lint`, `editorial-check`, and all copy-generation skills. The **Caption Style** section is specifically referenced by `/ck-publish` when drafting Instagram captions.
