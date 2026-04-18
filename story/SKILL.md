---
name: story
description: Research angles and write content specs for carousel posts. Guided mode asks step-by-step; --quick generates a draft from a topic description.
---

# story

Research angles and write content specs for carousel posts.

## Prerequisite

If `PHILOSOPHY.md` does not exist in the project root, suggest running `/onboard` first. The philosophy file establishes the account's editorial identity, which is required to generate on-brand story specs.

## Modes

### Guided mode (default)

Invoked with `/story` (no arguments).

1. **Topic intake** — Ask: "What topic?" Accept open-ended input (a person, an event, a thesis, a question).
2. **Research + angle generation** — Combine web research with the user's domain knowledge. Present 3 angle candidates, each with a one-line pitch. Angles should differ in framing (e.g., biographical vs. structural vs. contrarian).
3. **User picks** — Once the user selects an angle, propose a twist or hidden angle that elevates the story beyond surface-level narrative.
4. **Slide arc proposal** — Propose a slide arc based on patterns in EDITORIAL.md (e.g., Hook - Context - Detail A - Detail B - Twist - Reveal - Quote - Takeaway). Explain what each slide accomplishes narratively.
5. **Full spec writing** — Write the complete spec with slide-by-slide copy direction, including:
   - Slide role (hook, context, detail, twist, reveal, quote, takeaway)
   - Headline text
   - Body copy direction (not final copy — direction for what to communicate)
   - Visual direction (illustration subject, mood, composition notes)
   - Data/claims with source attribution
6. **Unverified claim flagging** — Any numeric claim, date, percentage, or quote that cannot be immediately verified gets flagged with `⚠️ UNVERIFIED` for `/factcheck` to resolve later.

### Quick mode

Invoked with `/story --quick "topic description"`.

- Auto-generates a complete spec draft from the topic description.
- Skips the interactive angle-selection steps.
- User reviews and edits the output.
- Still flags unverified claims with `⚠️ UNVERIFIED`.

## Output

Story spec file written to `stories/NNN_slug.md`, where `NNN` is the next sequential number.

## References

- **EDITORIAL.md** — Story arc patterns, voice rules, forbidden terms, hook hierarchy.
- **DESIGN.md** — Slide count constraints, visual format requirements.
- **PHILOSOPHY.md** — Account identity and editorial stance (must exist before running).
