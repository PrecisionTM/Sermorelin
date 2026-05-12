# Vercel Sermorelin — Deployment Guide

## ✅ Files to upload to GitHub

```
vercel-sermorelin/
├─ index.html               ← Sermorelin landing page (all CSS + JS inline)
├─ vercel.json              ← { "cleanUrls": true }
├─ DEPLOY.md                ← This file
├─ download                 ← Blank file (required by repo convention)
└─ images/
   ├─ hero-bg.jpg           ← Hero background (couple running, sage green)
   ├─ science-visual.jpg    ← Science/mechanism section visual
   ├─ pharmacy-prorx.svg    ← ProRx 503A pharmacy logo (SVG)
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
      ├─ lecom.svg           ← Dr. Palumbo, Dr. Chandler (Lake Erie COM)
      ├─ utmb-health.svg     ← Angela Kifer-Thomas (UTMB)
      ├─ cu-colorado.svg     ← Dr. Patel (Univ. of Colorado)
      ├─ ponce.svg           ← Dr. Colón-Molero (Ponce Health Sciences)
      ├─ vanderbilt.svg      ← Samuel Palmer (Vanderbilt)
      ├─ tel-aviv.svg        ← Dr. Akler (Tel Aviv University)
      ├─ texas-tech.svg      ← Brett Whaley (Texas Tech)
      ├─ cleveland-state.svg ← Michael Gype (Cleveland State)
      ├─ maryville.svg       ← Brittany Umana (Maryville University)
      └─ kentucky.svg        ← Dr. Ahmed (University of Kentucky)
```

---

## 🖼️ Logo Filter Notes

All logos in `images/logos/` are SVG placeholder stubs with transparent backgrounds.
CSS filter chain applied globally:

```css
.doctor-card__inst img {
  filter: brightness(0) saturate(100%) invert(32%) sepia(22%) saturate(520%)
          hue-rotate(75deg) brightness(88%) contrast(92%);
}
```

This renders each SVG in brand sage green (`#4a6741` approx).

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

| Button | URL |
|---|---|
| Primary CTA (all) | `https://precisiontelemed.com/start-anti-aging-program-sermorelin/` |
| Tirzepatide cross-sell | `https://precisiontelemed.com/compounded-tirzepatide/` |

---

## ✅ Convention Compliance (conventions.md)

- [x] No `vh`, `dvh`, or `svh` units in section heights
- [x] Hero uses `min-height: clamp(560px, 60vw, 860px)` with `height: auto`
- [x] Hero image uses `object-fit: cover`
- [x] All `position: absolute` layers inside parent with explicit non-viewport height
- [x] Brand tokens match conventions.md (`--color-bg: #fdfbf7`, `--color-primary: #788C75`, etc.)
- [x] `--section-gap: clamp(3rem, 6vw, 5rem)` applied
- [x] All image paths are relative (`images/...`)
- [x] `vercel.json` uses `cleanUrls: true` only — no rewrites
- [x] `download` blank file present
- [x] No stale or zero-byte files
