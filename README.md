# Frameryx

**The premium YouTube growth studio that never sees your data.**

A fast, offline-first YouTube analytics and channel-analysis tool — title scoring, thumbnail grading, A/B testing, channel audits, money tools, language strategy, a full public-data **Channel Analyzer** and a prescriptive **Growth Plan** — free for every creator, in every niche. Everything runs in your browser. Nothing is uploaded.

Live at **[frameryx.eknathalabs.com](https://frameryx.eknathalabs.com)**

---

## Why it's different

Tools like vidIQ, TubeBuddy, ViewStats and Social Blade are powerful because of data they hold on *their* servers — and they charge for it. Frameryx takes the opposite bet: everything they paywall that can be computed from **public** YouTube data or from heuristics is here, free, and private. Your data stays in your browser; there's no backend.

| Capability | vidIQ / Social Blade / ViewStats | Frameryx |
|---|---|---|
| Title / thumbnail scoring | paid | **free, with reasoning** |
| A/B title & thumbnail testing | paid | **free** |
| Channel analyzer (any channel) | paid / account | **free** |
| Breakout score + upload patterns | paid | **free** |
| Future projections | paid | **free** |
| Prescriptive "what to do next" | $49/mo (OutlierKit) | **free (Growth Plan)** |
| Your data stays in your browser | no | **always** |
| No account / no extension | no | **always** |

What **no** tool can show for a channel you don't own: CTR, retention, watch-time and real earnings — those are private YouTube Studio data. Frameryx says so plainly instead of faking them.

---

## The tools (18)

**Pre-publish (no data needed):** Optimize (title scorer + thumbnail grader + hook builder), A/B Test, Research, Tag Suggestions, Best Time to Publish, Channel Optimization, Money Calculator, Watch-time → Money, Language Opportunity.

**Your data (Studio CSV):** Growth Plan (ranked next steps), Audit, Roast My Channel.

**Public data (API):** Channel Analyzer (breakout score, upload patterns, consistency, projections, title-pattern mining, tag extraction, velocity, posting heatmap, niche-saturation read, "steal this" content brief), Audit by URL, Compare.

**Explore:** Top Creators (top 50), By Niche (22 categories).

---

## The API key (Channel Analyzer / Compare / Audit-by-URL)

These features read the **public** YouTube Data API, which needs a key. Frameryx supports two paths:

1. **Bundled shared key (optional, no user setup).** Set `BUNDLED_KEY` in `src/ytanalytics.js` to a key you've **restricted in Google Cloud Console** to:
   - the **YouTube Data API v3** only, and
   - the HTTP referrer **`frameryx.eknathalabs.com/*`** only.

   A referrer-locked key only works when called from that domain, so copying it from page source is useless elsewhere. A per-visitor daily cap (`DAILY_CAP`, default 5) protects your quota. Leave `BUNDLED_KEY=''` to disable this path.

2. **Bring-your-own key (always available).** Any user can add their own free key in Settings (2-minute guided walkthrough built in). Their key overrides the bundled key and lifts the daily cap for them.

### Creating the restricted bundled key
1. [console.cloud.google.com](https://console.cloud.google.com) → create a project.
2. Enable **YouTube Data API v3**.
3. Credentials → Create credentials → **API key**.
4. Edit the key → **API restrictions** → restrict to *YouTube Data API v3*.
5. **Application restrictions** → *HTTP referrers* → add `frameryx.eknathalabs.com/*` (and `*.frameryx.eknathalabs.com/*`).
6. Paste it into `BUNDLED_KEY` in `src/ytanalytics.js`, rebuild, deploy.

---

## Build

Single-file, zero-dependency. Source lives in `src/`; `build.py` inlines everything into `dist/index.html`.

```bash
python3 build.py        # regenerates dist/index.html
cp dist/index.html ./index.html   # GitHub Pages serves root
```

Built with vanilla HTML/CSS/JS. Chart.js and PapaParse are vendored and inlined — no CDN, no network dependency.

---

Built by **EknathaLabs** with ❤ for Everyone.
