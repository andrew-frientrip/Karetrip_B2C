# Karetrip — Taiwan Lead Conversion Landing

Multilingual (繁體中文 / English / العربية / Bahasa Indonesia) responsive landing page that converts the leads we captured at the Taiwan K-Tourism Roadshow into Karetrip bookings.

## Stack

Pure static HTML/CSS/JS in a single `index.html`. No build step, no framework. Deploys as-is to any static host.

## Run locally

Double-click `index.html` or open it via any local server, e.g.:

```bash
npx serve .
```

Open <http://localhost:3000>.

## Deploy

### Vercel (recommended)

```bash
npm i -g vercel
vercel --prod
```

Or import the repo on <https://vercel.com/new>.

### GitHub Pages / Netlify / Cloudflare Pages

Any static host works — no build command needed. Set the publish directory to the repo root.

## Project layout

```
.
├── index.html                       # single-file app (HTML + inline CSS + inline JS)
├── assets/
│   ├── i_logo_karetrip_light.png    # logo on dark backgrounds
│   ├── i_logo_karetrip_dark.png     # logo on light backgrounds
│   ├── hero_1080.mp4                # hero video, desktop
│   ├── hero_720.mp4                 # hero video, mobile
│   ├── hero_poster.jpg              # poster frame fallback
│   ├── products_manifest.js         # auto-generated thumb/gallery URLs
│   └── products/
│       └── {NN_name}/
│           ├── thumb.jpg            # card + first slide
│           └── gallery/             # additional detail-modal slides
│               └── {1,2,3...}.jpg
└── vercel.json                      # cache headers
```

## Updating product photos

The raw photos and build scripts are kept locally (gitignored). To refresh:

1. Drop a new image into `raw_photos/{NN_name}/thumbnail.{jpg,png,webp}` or `gallery/{1,2,...}.{ext}`.
2. Run `python3 scripts/build_assets.py` to compress and regenerate `assets/products/` and `assets/products_manifest.js`.
3. Commit and push — Vercel redeploys automatically.

## Form submission

The application form posts to EmailJS. Edit these three constants near the bottom of `index.html` with the IDs from your EmailJS account:

```js
const SERVICE_ID  = 'YOUR_SERVICE_ID';
const TEMPLATE_ID = 'YOUR_TEMPLATE_ID';
const PUBLIC_KEY  = 'YOUR_PUBLIC_KEY';
```

While these are placeholders, submissions are logged to the browser console (not delivered).

## Languages

UI is switchable from the header. Language data lives in the `I18N` object inside `index.html`.

| Code | Display |
|------|---------|
| `zh` | 繁體中文 (default) |
| `en` | English |
| `ar` | العربية |
| `id` | Bahasa Indonesia |

---

© Frientrip Co., Ltd. Business Reg. No. 261-81-04385.
