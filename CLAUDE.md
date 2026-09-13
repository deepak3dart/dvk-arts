# DVKarts Web — Project Context

Personal site for Deepak Vishwakarma (dvkarts.com), plus a standalone
SketchLog marketing page. Plain static HTML/CSS, no framework, no build
step — hosted on GitHub Pages.

## Structure — there are two separate sites, don't merge them

1. **`dvkarts.com`** — the main portfolio site. Multi-page:
   `index.html` (home), `works.html` (art portfolio, has a lightbox),
   `app.html` (SketchLog promo page, embedded within this site's own
   look), `contact.html`, `privacy.html` (SketchLog's actual privacy
   policy — canonical, don't duplicate this content elsewhere, link to
   it instead). Shared stylesheet: `style.css`.

2. **Standalone SketchLog site** (dark theme, separate from the above)
   — `app.html` + `stylenew.css` in its own folder/repo. This is a full
   dedicated landing page for SketchLog specifically (hero, app
   showcase with 5 phone mockups, 6-step workflow, privacy band, final
   CTA). Not yet deployed to its own domain — was being built toward a
   subdomain like `sketchlog.dvkarts.com`, using the same
   `GitHub Pages + free-tier SSL` pattern already proven working for
   the main site.

**These use different design systems on purpose** — the main portfolio
site is a light "warm paper" theme (Ink Blue `#33475C` / Ochre
`#B9782E` / `#FAF6EE`), matching the Android app's default palette. The
standalone SketchLog page is a distinct dark theme (`#0E0C0A` background,
brighter ochre `#D3902E`, cream text `#F2ECDF`). Don't collapse them
into one palette — they're deliberately different products/contexts.

## Hosting

- Registrar: Namecheap. **Nameservers must stay on "Namecheap BasicDNS"**
  — we briefly switched to Cloudflare and had to switch back; Cloudflare
  isn't needed for a static GitHub Pages site.
- DNS: 4 `A` records for `@` pointing to GitHub Pages' 4 IPs
  (185.199.108/109/110/111.153), 1 `CNAME` for `www` →
  `<username>.github.io`.
- SSL is free and automatic via GitHub Pages once DNS resolves — no
  Cloudflare or separate certificate needed.
- The `CNAME` file at the repo root controls which domain GitHub Pages
  serves the repo at — keep it in sync with whatever domain/subdomain
  is intended for that specific repo.

## Known gotcha we hit

**GitHub Pages is case-sensitive on file/folder names** — a folder
uploaded as `SketchLog` will 404 if the HTML references
`images/sketchlog/` (lowercase). Always match exact casing between the
HTML `src`/`href` attributes and what's actually in the repo.

## Conventions

- Fonts: Fraunces (headings, serif, 500-600 weight) + Inter (body) —
  loaded via Google Fonts `<link>` tags, not self-hosted
- Phone mockups are built with plain CSS (rounded frame + notch), not
  images — keeps them editable and avoids needing device-frame assets
- Charts (donut, bar) in the standalone SketchLog page are CSS
  (`conic-gradient` for the donut, flexbox height bars for weekly/
  category charts) — not images, not a charting library
- The "App" showcase section's tab row is real interactive JS (click a
  tab → it highlights + the matching phone scales up via a
  `.active-phone` class + the strip auto-scrolls to center it) — not
  decorative
- Real screenshots used elsewhere are from the actual running Android
  app (`com.dvkart.sketchlog`), not mockup/placeholder images

## What NOT to do

- Don't copy layout/branding from stock templates or other sites
  wholesale — reference composition/structure only, rebuild with
  original copy, colors, and assets. This came up explicitly with a
  stock "Goal Tracker" banner template — used for layout inspiration
  only, nothing copied directly.
- Don't invent Play Store download counts, review numbers, or other
  unverified stats in copy — the app isn't published yet. Use honest,
  currently-true claims instead (e.g. "No ads. No tracking. 100%
  offline." rather than "Downloaded 1000+ times").
