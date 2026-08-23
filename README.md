# Vital Gradient — Website

A specialist healthcare brand studio. We turn the service a patient *needs* into the brand
they *choose*. Single-page marketing site for a studio serving the US, UK, Gulf, and Australia.

**Live preview:** https://claude.ai/code/artifact/beff5b3f-4c69-45e9-8e50-c58362551f78

## What's here

- `index.html` — the entire site. Self-contained: HTML, CSS, and vanilla JS in one file,
  no build step, no dependencies. Fonts load from Google Fonts.

## Design direction — "The Living Gradient"

The identity is built around the brand's own name. *Vital* is the pulse (a quiet EKG accent);
*Gradient* is the thesis, made literal: the transition from a service patients **need** to a
brand they **choose** — warm meeting clinical. The signature is a slow, living gradient field
(coral warming into teal) behind the hero and reused across the site.

| Role | Value |
|------|-------|
| Display | Fraunces (warm high-contrast serif, italic for emphasis) |
| Body / UI | Space Grotesk |
| Data / labels | Space Mono |
| Ground (dark) | Clinical ink `#0B1513` |
| Ground (light) | Bone `#F2F3F1` |
| Signature gradient | Living coral `#FF6A55` → vital teal `#12897A` |

Cinematic dark hero + dark punctuation bands, light editorial body. Full light **and** dark
themes (toggle in the nav; respects OS preference). Grain texture throughout. All motion
respects `prefers-reduced-motion`.

### Sections
Hero (living gradient field) → services marquee → belief/manifesto → services (editorial rows)
→ markets (dark band) → selected work (numbered case studies) → impact stats → process →
packages → chart notes → contact → footer.

### Motion
Ambient morphing gradient blobs, page-load reveal sequence, scroll-triggered reveals,
count-up case/impact stats, a marquee, and hover micro-interactions.

## Swapping in real images & video

Coded visuals ship first so the site looks finished immediately. To drop in real media, search
`index.html` for `MEDIA SLOT` — each marks exactly what to replace:

1. **Hero video** — an ambient loop behind the gradient field (`.hero`, above `.hero-veil`):
   ```html
   <video class="hero-video" autoplay muted loop playsinline poster="assets/hero-poster.jpg"
     style="position:absolute;inset:0;z-index:0;width:100%;height:100%;object-fit:cover;opacity:.4;mix-blend-mode:luminosity;">
     <source src="assets/hero.mp4" type="video/mp4">
   </video>
   ```
2. **Case-study media** (`.case-media .art`) — replace each `.art` div with an `<img>` or short
   muted `<video>`; the badge overlay stays on top.

Put real assets in an `assets/` folder next to `index.html`. Case-study figures are currently
representative — swap in real numbers as engagements close.

## Deploy

Static hosting — GitHub Pages, Netlify, Vercel, or any web server. No build required.
Point your host at `index.html`.
