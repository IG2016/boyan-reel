# Boyan Bashovski — Reel

A cinematic, scroll-driven portfolio for cinematographer / producer / director **Boyan Bashovski**. The site is one continuous vertical "reel" told across seven chapters (SCENE 01–07), with match-cut transition zones, film-grain + letterbox treatment, a scroll-linked timecode HUD, and click-to-play Vimeo screenings.

## Run locally

It's a static site — no build step. Serve the folder with any static server, e.g.:

```bash
npx serve .
# or
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

> Opening `index.html` directly via `file://` also works, but a local server is recommended so the ambient `.mp4` loops and fonts load cleanly.

## Structure

```
index.html          — the site (entry point)
support.js          — component runtime (required)
image-slot.js       — drag-and-drop portrait slot in the About section
assets/             — chapter thumbnail stills (from Vimeo)
uploads/            — ambient transition loops (muted, looping background video)
```

The five project films stream from **Vimeo** (embedded on click), so they cost the host zero bandwidth. Only the ambient loop `.mp4`s in `uploads/` are served from this site.

## Deploy

Any static host works. Recommended: **Cloudflare Pages** (effectively unmetered video bandwidth) or **Netlify**.

- **Cloudflare Pages / Netlify:** connect this repo, framework preset **None**, build command **(none)**, output directory **/** (root).
- **GitHub Pages:** Settings → Pages → deploy from branch `main`, folder `/ (root)`.

Point a custom domain (e.g. `boyanbashovski.com`) at the host and add SSL.

## Notes

- Respects `prefers-reduced-motion` (disables parallax, particles, autoplay loops, credit crawl).
- Only one video plays at a time; off-screen players pause automatically.
- The ROTC screening is an unlisted Vimeo video embedded with its private hash.
