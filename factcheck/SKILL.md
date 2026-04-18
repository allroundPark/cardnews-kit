---
name: factcheck
description: Verify numeric claims in story specs against primary sources. Grades each claim as ✅ (verified), ✅* (secondary consensus), ⚠️ (slightly off), or ❌ (wrong).
---

# factcheck

Verify numeric claims in story specs against primary sources.

## Flow

1. **Extract claims** — Read the story spec and extract all numeric claims: percentages, dates, prices, names, quotes, index levels, return figures, and biographical facts.
2. **Verify each claim** against sources in priority order:
   - **Data APIs** — Adapter-dependent (FMP, Yahoo Finance, etc.). Use the project's configured data adapter.
   - **Web search** — For non-data claims (historical facts, quotes, biographical details).
   - **Primary source tracing** — Follow citations back to the original book, speech, filing, or dataset.
3. **Grade each claim**:

   | Grade | Meaning |
   |-------|---------|
   | ✅ | Verified via direct primary source access |
   | ✅* | Secondary source consensus — multiple reliable secondary sources agree, but primary book/video/filing not directly accessed |
   | ⚠️ | Direction correct, magnitude slightly off — suggest specific correction |
   | ❌ | Factually wrong — must fix before publish |

4. **Generate verification report** — Table format with: claim text, source checked, grade, and notes.
5. **Suggest corrections** — For every ⚠️ and ❌, provide the correct value with its source.

## Output

Verification report appended to the story spec file, in a `## Verification Checklist` section.

## Hard Rules

- **Never guess or fill numbers from memory.** If the data API is unavailable, fall back to web search. If web search is ambiguous, flag ⚠️ rather than asserting a value.
- **Anti-pattern: subagent self-promotion.** A research subagent may claim ✅ when it only accessed secondary sources. Always ask: "Did I actually read the primary source?" If not, the grade is ✅* at best.
- **Aggregate numbers hide timing.** Annual or semi-annual net-buy/sell figures conceal intra-period timing. Do not use aggregate numbers to assert specific behavioral claims. Flag with a note about timing ambiguity.
