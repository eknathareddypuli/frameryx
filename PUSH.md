# Deploy Frameryx

The repo already exists at **github.com/eknathareddypuli/frameryx**. You're updating it.

## 1. Replace files and deploy
From this folder, copy the built file to root (GitHub Pages serves the repo root):

```bash
python3 build.py                     # regenerate dist/index.html from src/
cp dist/index.html ./index.html      # root file Pages serves
git add -A
git commit -m "Rebrand to Frameryx; add Channel Analyzer (breakout, patterns, projections, steal-this brief) + dual-key API"
git push
```

## 2. GitHub Pages
Settings → Pages → Source: Deploy from a branch → `main` → `/ (root)` → Save.
(`.nojekyll` and `CNAME` are already at root. CNAME = `frameryx.eknathalabs.com`.)

## 3. DNS
At your DNS provider, add a CNAME record:
- Host: `frameryx`
- Value: `eknathareddypuli.github.io`

Then Settings → Pages → Custom domain: `frameryx.eknathalabs.com` → Enforce HTTPS.

## 4. (Optional) Enable the no-setup shared key
To make the Channel Analyzer work for visitors without their own key, create a
**referrer-locked** key (see README → "Creating the restricted bundled key"),
paste it into `BUNDLED_KEY` in `src/ytanalytics.js`, then `python3 build.py`,
`cp dist/index.html ./index.html`, commit and push.

Without it, the analyzer simply prompts users to add their own free key in
Settings — nothing breaks.

## Editing later
Edit files in `src/`, then:
```bash
python3 build.py && cp dist/index.html ./index.html
git commit -am "update" && git push
```
