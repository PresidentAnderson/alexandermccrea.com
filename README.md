# alexandermccrea.com

Personal site for Alexander McCrea, campaign organizer for left-of-centre candidates.
Static site: one HTML page, one image, no build step.

## Layout

| Path | What it is |
|---|---|
| `index.html` | The live homepage. Plain HTML + inline CSS, Google Fonts (Bricolage Grotesque, Source Serif 4). |
| `assets/alexander-mccrea.jpg` | Portrait used in the hero. **Low-res (380×380) crop taken from the preview screenshot** — replace with the original photo when available. |
| `design/Main.dc.html` | The homepage artboard as authored in the Claude Design canvas. Source of truth for layout and copy; `index.html` is derived from it. |
| `design/canvas.json` | Canvas index for that artboard. |
| `design/alexmcrae-preview.png` | Screenshot of a later rendering of the hero (shows the photo, an EN/FR toggle and different nav labels — see "Known gaps"). |

Design canvas: https://claude.ai/artifact/SgGJqSPPhA28rKCkjE5yMY (version 1791675150-c837, 2026-10-10).

## Editing

Edit `index.html` directly for copy changes. If the design canvas is updated instead, re-derive `index.html` from
`design/Main.dc.html`: drop the `support.js` script, the `<x-dc>`/`<helmet>` wrappers and the trailing `text/x-dc`
script block; move the font `<link>` into `<head>`; replace every `{{accent}}` with `#F5B700`.

## Deploy

Hosted on **GitHub Pages**, served straight from the `main` branch root (no build step, `.nojekyll` present).
Every push to `main` republishes within about a minute.

- Live URL: https://alexmccrea.com/ (also https://www.alexmccrea.com/; the github.io address redirects there)
- Repo: https://github.com/PresidentAnderson/alexandermccrea.com (public; GitHub Pages on a private repo needs a paid plan)
- Custom domain: `alexmccrea.com`, set 2026-10-10. The `CNAME` file in the repo root holds it; DNS at Cloudflare
  (zone cd50840b3a2d9651a6d279a956a92829) has four A records on the apex to GitHub Pages and a `www` CNAME to
  `presidentanderson.github.io`, all DNS-only (not proxied) so GitHub can issue the certificate.

The Vercel team `axaiinovation` was tried first and refused (account suspended for billing, HTTP 402).

## Known gaps (as of 2026-10-10)

1. ~~Contact email~~ — filled in 2026-10-10 (alexmtaichi@gmail.com). The form opens the visitor's mail client with the fields pre-filled; there is no server-side handler.
2. **Placeholder copy.** 20 bracketed placeholders remain in `index.html`: the three "My story" paragraphs, the
   three campaign cards (`[YEAR] · [RACE]`, `[CANDIDATE NAME]`, description), the testimonial and its attribution,
   and the footer `[LINKEDIN]` / `[SOCIAL]` links (which currently point to `#top`).
3. **Photo.** See `assets/` note above. The hero slot is square; a 4:5 portrait will also work (`aspect-ratio` on the `<img>`).
4. **Preview vs. artboard.** `design/alexmcrae-preview.png` shows a version with an EN/FR language toggle and a
   "LEFT-OF-CENTRE CAMPAIGNS" eyebrow. No French copy exists in this repo. The artboard (and therefore `index.html`)
   is English only; the eyebrow wording was taken from the preview.
5. **Domain.** Live on `alexmccrea.com`. The repo is still named `alexandermccrea.com` (that domain is unregistered)
   and the design canvas is titled `alexmcrae.com` (owned by someone else).
6. **Privacy link** in the footer points to `#top`; there is no privacy page.
