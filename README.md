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
| Primary — headings / display | **Lora** (serif, italic for emphasis) |
| Secondary — body / UI / buttons | **Nunito** |
| Minor — data / labels | Space Mono |
| Ground (dark) | Clinical ink `#0B1513` |
| Ground (light) | Bone `#F2F3F1` |
| Brand blue (logo) | `#244797` |
| Signature gradient | Brand blue `#244797` → azure `#2F6BD0` → sky `#46A6E6` |

The palette is tuned to the real logo, whose one fixed colour is `#244797`. The logo
(all formats — SVG/PNG/WebP/PDF/AI/EPS) lives in `assets/`; the page embeds the SVG
inline via the `--logo` CSS variable, and it appears in the nav and footer.

The live page loads Lora + Nunito from Google Fonts (identical to the SIL OFL files).
Your uploaded files are committed under `assets/fonts/` for self-hosting — to use them
instead of Google Fonts, drop the `<link>` in `<head>` and add:

```css
@font-face{font-family:'Lora';src:url('assets/fonts/Lora-Variable.ttf') format('truetype');font-weight:400 700;font-style:normal;font-display:swap;}
@font-face{font-family:'Lora';src:url('assets/fonts/Lora-Italic-Variable.ttf') format('truetype');font-weight:400 700;font-style:italic;font-display:swap;}
@font-face{font-family:'Nunito';src:url('assets/fonts/Nunito-Variable.ttf') format('truetype');font-weight:400 800;font-style:normal;font-display:swap;}
@font-face{font-family:'Nunito';src:url('assets/fonts/Nunito-Italic-Variable.ttf') format('truetype');font-weight:400 700;font-style:italic;font-display:swap;}
```

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

## Case-study imagery

The four case cards use hand-built **SVG scene illustrations** (in brand blue) that read as
real product UI — a social phone + growth chart, a lead-gen funnel + booking, a website
mockup + brand swatches, and an always-on content calendar. They're self-contained (no image
files) and scale crisply on every screen. Swap any for a real screenshot via the `MEDIA SLOT`
markers.

## Responsive coverage

Verified across desktop (Mac/Windows), iPad / Android tablets, and iPhone / Android phones:
fluid `clamp()` type, safe-area insets for notch/gesture bars, touch-device fallbacks for
hover-only cues, and dedicated breakpoints down to small phones. The body clips stray
horizontal overflow so there's never a sideways scroll.

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

Static site — no build step, no dependencies. Works on any static host.

### Vercel (recommended)
A `vercel.json` is included (clean URLs + long-cache headers for `assets/`, no-cache for
`index.html`). Two ways to ship:

- **From this repo:** in Vercel, "Add New → Project", import the GitHub repo, leave
  Framework Preset as **Other** and Build Command empty (Output Directory `.`), then Deploy.
- **From your machine:** install the CLI (`npm i -g vercel`), run `vercel` in this folder
  for a preview URL, then `vercel --prod` to go live.

No environment variables or build settings are needed.

### Anything else
GitHub Pages, Netlify (drag-and-drop the folder), Cloudflare Pages, or any web server —
just serve `index.html` from the root.
