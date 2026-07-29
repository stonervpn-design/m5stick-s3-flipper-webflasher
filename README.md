# Web Flasher — Flipper M5Stick S3 (Public)

One-click browser flasher for the public build, using [ESP Web Tools](https://esphome.github.io/esp-web-tools/).

## Files
- `index.html` — the flash page
- `manifest.json` — points ESP Web Tools at the bin (offset `0x0`, ESP32-S3)
- `Flipper-m5stick_s3-public-merged.bin` — the full-flash image

## Hosting (must be HTTPS — Web Serial won't run over plain http)

**GitHub Pages**
1. Push this `webflash/` folder to a repo.
2. Settings → Pages → deploy from branch, point at the folder (or move the 3 files to the repo root / `docs/`).
3. Open the published `https://…/index.html` in Chrome or Edge.

**Netlify / Cloudflare Pages / Vercel**
- Drag-and-drop this folder, or connect the repo. Any static host with HTTPS works.

**Local test**
```
cd webflash
python -m http.server 8000
```
Then open `http://localhost:8000/` (localhost is treated as secure, so Web Serial works).

## Notes
- Requires desktop **Chrome** or **Edge** (Web Serial). Firefox/Safari and phones are unsupported — the page shows a manual `esptool` fallback.
- The bin is a merged image with flash mode/size/freq baked in, so it flashes at a single offset `0x0`.
- To ship a new build, just replace the `.bin` (keep the filename) and bump `version` in `manifest.json`.
