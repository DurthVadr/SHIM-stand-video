# SHIM Stand Video

A single self-contained HTML file that, opened in Chrome at 1920×1080 and
screen-recorded, produces a ~55-second looping marketing video for the
[SHIM.tech](https://getshim.tech) booth at CVC Otel Bosphorus, Istanbul,
8 May 2026.

The video is the booth's silent attractor — runs muted on a laptop on the
table, designed to stop a passer-by in 2–3 seconds and communicate the SHIM
B2B AI Gateway value across three audience segments (CFO, engineer, investor)
in one loop.

## What you see

| Scene | Time | Beat |
| --- | --- | --- |
| 1 — Cost savings | 0–8s | `$0 → $16,247` counter, cache-hit gauge to 38% |
| 2 — Control tower | 8–22s | live KPIs, request stream, PII Koruma panel, donut, latency sparkline |
| PII — How it works | 22–36s | redaction diff: original payload → masked payload sent to provider |
| 3 — Universal API | 36–50s | one cURL with `<MODEL>` cycling between OpenAI/Anthropic/Google, three provider responses streaming in parallel |
| End card | 50–55s | wordmark, `getshim.tech`, QR code |

All metrics, organisation names, payloads, and PII values are simulated
client-side from a seeded RNG. There is no network traffic, no telemetry, no
external data — only Tailwind CSS and Google Fonts via CDN.

## Run it

```bash
git clone https://github.com/DurthVadr/SHIM-stand-video.git
cd SHIM-stand-video
open index.html         # double-click in Finder also works
```

For best results record at exactly **1920×1080** in OBS / QuickTime / CapCut.
The stage scales to fit any viewport but is calibrated to a 16:9 frame at
that resolution.

## File layout

- `index.html` — the entire video. Inline CSS, inline vanilla JS, no build
  step. Tailwind is loaded from CDN (production warning is expected and
  harmless).
- `LICENSE` — MIT.

## Customise

Most things you'll want to tweak are concentrated near the top of the
`<script>` block:

- `LOOP_DURATION` and the `T_*` scene boundaries
- `MODELS`, `PROVIDERS`, `ORG_POOL` for routing demo data
- `RESP_A` / `RESP_B` / `RESP_C` for the three streamed responses
- `PII_INIT_COUNTS` for the PII Koruma panel seed values
- `KPI_INIT` for the five top-bar tiles' starting numbers

Brand colour palette is in the `:root` / `tailwind.config` block at the top
of `<style>`. The accent cyan (`#5ce1e6`) is the SHIM signature colour.

## Trademarks

The OpenAI rosette, Anthropic `A`, and Google `G` icons are embedded as
inline SVG paths and are trademarks of their respective owners — used here
for nominative reference only. They are not covered by the MIT license.

## Built for

CVC Otel Bosphorus · Istanbul · 8 May 2026.
