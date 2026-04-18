# cardnews-kit

**Build editorial carousels with AI — from benchmarking to publish.**

Proven with a real Instagram account. Finance, design, food, architecture, travel — change the topic, keep the pipeline.

---

## Made with cardnews-kit

> _Your link here_ — [instagram.com/your_account](https://instagram.com/your_account)

---

## Quick Start

```bash
# 1. Clone the kit
git clone https://github.com/your-org/cardnews-kit.git
cd cardnews-kit

# 2. Install dependencies
./setup

# 3. Onboard — define your account identity
/onboard

# 4. Create your first carousel
/story
```

---

## Skills

### Phase 1 — Onboard

Run these once to set up your project's creative identity.

| Skill | Description |
|---|---|
| `/onboard` | Interactive setup — mission, audience, topic, output directory |
| `/benchmark` | Analyze 5-10 reference accounts, extract patterns that work |
| `/design-system` | Define colors, typography, layout grid, and visual tokens |
| `/voice` | Set editorial tone, forbidden terms, and copy guidelines |

### Phase 2 — Produce

Run this loop for every post. All production skills support `--quick` mode for faster iteration.

| Skill | Description |
|---|---|
| `/story` | Research topic, write narrative arc, structure slides |
| `/factcheck` | Verify numbers, dates, and claims against primary sources |
| `/illustrate` | Generate AI illustrations matching your design system |
| `/lint` | Check slides against design system and editorial voice |
| `/render` | Render HTML templates to 1080x1350 PNGs via Playwright |
| `/publish` | Bundle slides + caption + metadata for upload |
| `/review` | Pre-publish review — full editorial and visual check |

---

## Philosophy

cardnews-kit is built on three beliefs: your taste is the product, content is the root, and making closes the gap.

Read the full philosophy in [ETHOS.md](ETHOS.md).

---

## Tool-Agnostic

The kit is process, not stack. Image generation, data APIs, and publishing targets are handled through adapters in `adapters/reference/`. Swap Gemini for DALL-E, FMP for Yahoo Finance, or Instagram for Threads — the pipeline stays the same.

---

## License

[MIT](LICENSE)
