# Vercel Sermorelin — Deployment Guide

## ✅ Files to upload to GitHub

```
vercel-sermorelin/
├─ index.html               ← Sermorelin landing page (entry point)
├─ vercel.json              ← Vercel config (cleanUrls: true)
├─ DEPLOY.md                ← This file
├─ download                 ← Blank file (required by repo)
└─ images/
   ├─ hero-bg.jpg           ← Couple running on forest trail (sunny, sage green clothes)
   ├─ pharmacy-prorx.jpg    ← ProRx 503B outsourcing facility
   ├─ patient-result-1.jpg  ← Male patient before/after
   ├─ patient-result-2.jpg  ← Female patient before/after
   ├─ testimonial-michael.jpg
   ├─ testimonial-angela.jpg
   ├─ testimonial-daniel.jpg
   ├─ testimonial-tanya.jpg
   ├─ testimonial-sandra.jpg
   ├─ testimonial-kevin.jpg
   ├─ doctors/
   │  ├─ dr-palumbo.jpg
   │  ├─ angela-kifer-thomas.jpg
   │  ├─ dr-patel.jpg
   │  ├─ dr-colon-molero.jpg
   │  ├─ samuel-palmer.jpg
   │  ├─ dr-akler.jpg
   │  ├─ brett-whaley.jpg
   │  ├─ michael-gype.jpg
   │  ├─ dr-chandler.jpg
   │  ├─ brittany-umana.jpg
   │  └─ dr-ahmed.jpg
   └─ logos/
      ├─ lecom.svg
      ├─ utmb-health.svg
      ├─ cu-colorado.svg
      ├─ ponce.svg
      ├─ vanderbilt.svg
      ├─ tel-aviv.svg
      ├─ texas-tech.svg
      ├─ cleveland-state.svg
      ├─ maryville.svg
      └─ kentucky.svg
```

---

## 🚀 Deploy to Vercel (step-by-step)

### 1 — Push to GitHub
```bash
git init
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/YOUR-ORG/sermorelin-landing.git
git push -u origin main
```

### 2 — Import in Vercel
1. Go to https://vercel.com/new
2. Click **Import Git Repository** → select your repo
3. **Framework Preset**: `Other`
4. **Root Directory**: *(leave blank)*
5. **Build Command**: *(leave blank)*
6. **Output Directory**: *(leave blank)*
7. **Install Command**: *(leave blank)*
8. Click **Deploy**

### 3 — Done ✅
Vercel detects `index.html` at the root and serves the static site directly. No build step required.

---

## ⚠️ What NOT to do

| Action | Why it breaks |
|---|---|
| Add a `build` script to package.json | Vercel runs it and fails |
| Use `"/(.*)"` rewrite in vercel.json | Intercepts ALL requests including CSS and images |
| Set Root Directory to a subfolder in Vercel | Vercel looks in the wrong place |
| Use absolute image paths (`/images/...`) | Breaks when served from a subfolder |
| Use `vh`, `dvh`, or `svh` in section heights | Breaks in auto-height iframes |

---

## 📞 CTA URLs
- Primary CTA: https://precisiontelemed.com/start-anti-aging-program-sermorelin/
- Tirzepatide cross-sell: https://precisiontelemed.com/compounded-tirzepatide/

---

## ✅ Convention Compliance (conventions.md)

- [x] No `vh`, `dvh`, or `svh` units in section heights
- [x] Hero uses `min-height: clamp(560px, 60vw, 860px)` with `height: auto`
- [x] Hero image uses `object-fit: cover`
- [x] All `position: absolute` layers inside parent with explicit non-viewport height
- [x] `--color-bg: #fdfbf7` and `--color-bg-alt: #f5f2ec` brand tokens applied
- [x] `--section-gap: clamp(3rem, 6vw, 5rem)` applied
- [x] `#page-wrap` wraps body content with `overflow-x: hidden`
- [x] All image paths are relative (`images/...`)
- [x] `vercel.json` uses `cleanUrls: true` only — no rewrites
- [x] Tirzepatide cross-sell CTA: https://precisiontelemed.com/compounded-tirzepatide/
- [x] science-visual.jpg saved locally (no external Unsplash URL)
