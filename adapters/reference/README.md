# Reference Adapter — Playwright + Gemini + FMP

This is a working example of tool integration used by the
[@변하지않는것](https://instagram.com/___) project.

**cardnews-kit is tool-agnostic.** These adapters are examples, not requirements.
Swap any component for your preferred alternative.

## Stack

| Capability | Tool | Alternatives |
|---|---|---|
| Render | Playwright (Chromium) | Puppeteer, Selenium, Figma API |
| Image generation | Gemini 3 Pro Image | DALL-E, Midjourney, Flux, Stable Diffusion |
| Data verification | FMP (Financial Modeling Prep) | Yahoo Finance, Alpha Vantage, manual research |

## Files

| File | Purpose |
|---|---|
| `render.py` | Playwright HTML → PNG render script |
| `generate_images.py` | Gemini image generation with style reference injection |
| `factcheck.py` | FMP API data verification helper |

## Setup

```bash
# Playwright (installed by ./setup at repo root)
pip install playwright
playwright install chromium

# Gemini (optional — for /illustrate)
pip install google-genai
export GEMINI_API_KEY="your-key"

# FMP (optional — for /factcheck with financial data)
# Get free key at https://financialmodelingprep.com
```

## Notes

- Playwright is the only **core** dependency (needed for `/benchmark`, `/render`, and `browse`)
- Image generation and data APIs are adapter-level — the skills work without them,
  you just do those steps manually
