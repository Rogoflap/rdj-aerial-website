# RDJ Aerial Services — website

Static site, no build step. Same brand system as the business cards and flyers: Oswald + IBM Plex Sans/Mono, ink-950 ground, sectional-chart accent colors per service line.

## Files

- `index.html` — the whole site (single page, anchor-linked sections)
- `styles.css` — all styles
- `favicon.svg`
- `assets/docs/` — PDF info sheets linked from the Training and Residential service cards

## Lawn aeration sub-site

`aeration/` is a second, self-contained site for RDJ Services' lawn aeration business (`/aeration/` once deployed), with its own `index.html`, `styles.css`, and `favicon.svg`. The two sites link to each other from the nav and footer. Content came from the Nextdoor business page; the Neighborhood Favorite years (2021–2025) and the two quoted recommendations are from that page — re-check them against Nextdoor before relying on exact wording. The photo/video gallery is a commented-out block in `aeration/index.html` (search for "PHOTO / VIDEO GALLERY") — uncomment it once files are in `aeration/assets/`.

## Local preview

No build tooling needed — any static file server works:

```bash
python -m http.server 8093
```

Then open http://localhost:8093

## Deploying

Recommended: **Cloudflare Pages** or **Netlify**, both have a free tier that's plenty for a site this size and both support a custom domain.

1. Push this folder to a GitHub repo (or drag-and-drop deploy — both Cloudflare Pages and Netlify support uploading a folder directly without git, if you'd rather skip GitHub).
2. Connect the repo in Cloudflare Pages / Netlify. Build command: none. Output/publish directory: `/` (the repo root).
3. Buy a domain (e.g. `rdjaerialservices.com`) from any registrar (~$12/yr) and point its DNS at the host — both platforms walk you through this in their dashboard.

## Editing

It's plain HTML/CSS, no framework — edit `index.html` and `styles.css` directly. A few notes if you're changing content:

- Pricing lives in the `#pricing` section of `index.html` — it currently mirrors the Training/Residential flyer pricing (Claude-suggested, not finalized numbers).
- Service card accent colors are set per-card with `style="--card-accent:var(--cyan-400)"` etc. — the five accents (`--cyan-400`, `--violet-400`, `--crimson-500`, `--teal-500`, `--amber-500`) are defined at the top of `styles.css`.
- The hero's circular graphic is hidden below 540px viewport width to keep the headline the first thing mobile visitors see.

## Git

This folder was initialized as its own git repo (`git init`), separate from any other project. The first commit used a placeholder name/email (`Roger Davis` / `roger@example.local`) since no git identity was configured — update it before your next commit:

```bash
git config user.name "Your Name"
git config user.email "your@email.com"
```
