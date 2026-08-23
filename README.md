# Vital Gradient — Website

The pulse behind healthcare brands. A single-page marketing site for a healthcare-focused
creative agency (social, campaigns, and websites) serving the US, UK, Gulf, and Australia.

**Live preview:** https://claude.ai/code/artifact/beff5b3f-4c69-45e9-8e50-c58362551f78

## What's here

- `index.html` — the entire site. Self-contained: HTML, CSS, and vanilla JS in one file,
  no build step, no dependencies. Fonts load from Google Fonts.

## Design system

| Role | Value |
|------|-------|
| Display | Lora (serif, italic for emphasis) |
| Body | Nunito |
| Data / labels | IBM Plex Mono |
| Ground | Porcelain `#F6F4EF` (light) · Ink `#0E1B33` (dark) |
| Accent | Pulse blue `#224597` / `#2E5BD6` |
| Secondary | Sage `#5E8577` |

Full light **and** dark themes are built in (toggle in the nav; respects OS preference).
All motion respects `prefers-reduced-motion`.

## Signature

A live **vital-signs monitor** in the hero — an animated EKG trace with drifting readouts —
reused as a connective motif (mini-EKGs on case cards, a flatline that resolves at the
contact section).

## Swapping in real images & video

The site ships with self-contained, coded visuals so it looks finished immediately. To drop
in real media, search `index.html` for `MEDIA SLOT` — each marks exactly what to replace:

1. **Hero video** (`.monitor-media`) — add an ambient loop behind the EKG trace:
   ```html
   <video class="hero-video" autoplay muted loop playsinline poster="assets/hero-poster.jpg"
          style="position:absolute;inset:0;width:100%;height:100%;object-fit:cover;opacity:.5;">
     <source src="assets/hero.mp4" type="video/mp4">
   </video>
   ```
2. **Founder / team photo** (`.photo-frame`) — replace the `.ph-art` block with
   `<img src="assets/founder.jpg" alt="Ajay Krishnan R, Founder">`.
3. **Case-study images** (`.case-media .art`) — replace each `.art` div with an `<img>` or
   short `<video>`; the badge and mini-EKG overlay stay on top.

Put real assets in an `assets/` folder next to `index.html`. Case-study figures are currently
representative — swap in real numbers as engagements close.

## Deploy

Static hosting — GitHub Pages, Netlify, Vercel, or any web server. No build required.
Point your host at `index.html`.
