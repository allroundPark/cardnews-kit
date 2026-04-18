---
name: onboard
description: Guided onboarding for new cardnews projects. Creates PHILOSOPHY.md, runs benchmark, design-system, and voice setup. Run this first.
---

# onboard — First-Run Project Setup

The onboarding skill walks a new user through the full project setup, from articulating their content philosophy to generating all configuration files. This is the entry point for any new cardnews project.

## Flow

### Phase 0: Present the Kit's Ethos
- Show `ETHOS.md` ("This kit was built on these beliefs")
- Let the user read and absorb before asking anything
- This sets the tone: the kit has opinions, and the user's answers will shape how those opinions manifest

### Phase 1: Philosophy Questions (5-7 questions, one at a time)

Ask these questions sequentially. **Wait for the user's answer before proceeding to the next question.** Do not batch them.

1. "Why are you making content?" — motivation, purpose, what gap they see
2. "Who do you want to reach?" — audience definition, specificity matters
3. "What will you never do?" — anti-goals, forbidden patterns, ethical lines
4. "What's your unique perspective or taste?" — what makes their lens different
5. "What does success look like for you?" — metrics, feelings, milestones

Optional follow-ups (ask if answers are thin):
6. "What content do you admire? What do you hate?"
7. "If your account were a person, how would they talk?"

### Phase 2: Generate PHILOSOPHY.md
- Synthesize the answers into a structured `PHILOSOPHY.md`
- Present it to the user for confirmation
- User must explicitly approve before proceeding

### Phase 3: Run Downstream Skills
Call each skill in sequence:
1. `/benchmark` — analyze reference accounts and extract patterns
2. `/design-system` — generate design tokens from references
3. `/voice` — define editorial voice and story arc templates

### Phase 4: Synthesize CLAUDE.md
- Auto-generate the project's `CLAUDE.md` by combining:
  - PHILOSOPHY.md (user's intent and constraints)
  - BENCHMARK.md (reference patterns and adopted rhythms)
  - DESIGN.md (visual system tokens)
  - EDITORIAL.md (voice rules and story arc templates)
- This becomes the authoritative project context file

### Phase 5: Commit and Close
- Commit all generated files
- Print: "Onboarding complete. Run `/story` to create your first post."

## Rules

- **One question at a time.** Never present multiple questions in a single message. Wait for the answer.
- **Present ETHOS first.** The user should understand the kit's beliefs before articulating their own.
- **Use selection prompts where possible.** For questions with common answers (e.g., audience type, success metrics), offer selectable options alongside a freeform option.
- **Respect existing state.** If the user already has `PHILOSOPHY.md`, ask: "Want to redo onboarding from scratch, or skip to a specific phase?" Offer phase selection.
- **Do not rush.** The onboarding conversation shapes everything downstream. Quality of answers matters more than speed.
