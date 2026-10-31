# alexandermccrea.com

Personal site for Alexander McCrea, campaign organizer for left-of-centre candidates.
Static site: one HTML page, one image, no build step.

## Layout

| Path | What it is |
|---|---|
| `index.html` | The live homepage. Plain HTML + inline CSS, Google Fonts (Bricolage Grotesque, Source Serif 4). |
| `assets/alexander-mccrea.jpg` | Portrait used in the hero. 1000×1000 square headshot. |
| `assets/art/` | Five paintings by Saali, shown in the "Art" gallery section (added 2026-10-30; originals came from Downloads, `image000000`–`000004`). |
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

- Live URL: https://alexandermccrea.com/ (also https://www.alexandermccrea.com/; the github.io address redirects there)
- Repo: https://github.com/PresidentAnderson/alexandermccrea.com (public; GitHub Pages on a private repo needs a paid plan)
- Custom domain: `alexandermccrea.com` (primary since 2026-10-30). The `CNAME` file in the repo root holds it. DNS at
  Cloudflare (zone b099de59fc07b7948050cf8228b5ec6a): four A records on the apex to GitHub Pages and a `www` CNAME to
  `presidentanderson.github.io`, all DNS-only (not proxied) so GitHub can issue the certificate. The zone also has
  Cloudflare Email Routing (MX/SPF/DKIM) — leave those records alone.
- Second domain: `alexmccrea.com` (zone cd50840b3a2d9651a6d279a956a92829; primary 2026-10-10 to 2026-10-30).
  Its records are proxied through Cloudflare and a Redirect Rule sends every request, apex and `www`, with a 301 to
  `https://alexandermccrea.com`, keeping the path and query string.

The Vercel team `axaiinovation` was tried first and refused (account suspended for billing, HTTP 402).

## Known gaps (as of 2026-10-10)

1. ~~Contact email~~ — filled in 2026-10-10 (alexmtaichi@gmail.com). The form opens the visitor's mail client with the fields pre-filled; there is no server-side handler.
2. **Placeholder copy.** 20 bracketed placeholders remain in `index.html`: the three "My story" paragraphs, the
   three campaign cards (`[YEAR] · [RACE]`, `[CANDIDATE NAME]`, description), the testimonial and its attribution,
   and the footer `[LINKEDIN]` / `[SOCIAL]` links (which currently point to `#top`).
3. ~~Photo~~ — replaced 2026-10-30 with the 1000×1000 original (from the `alexmcrae-site` bundle).
4. ~~French~~ — added 2026-10-30. EN/FR toggle in the header. English copy is the HTML itself; French is the `FR`
   table in the script at the bottom of `index.html`, matched by each element's `data-i18n` key (copied from the
   `alexmcrae-site` bundle, plus French written for the Campaigns heading, direct-email line and footer). When you
   change an English line, change its French line too. The page opens in `?lang=fr|en`, else the visitor's last
   choice, else their browser language. The bracketed placeholders are not translated; add French for them when the
   real copy arrives.
5. **Domain.** `alexandermccrea.com` is primary; `alexmccrea.com` redirects to it (see Deploy). The design canvas
   title `alexmcrae.com` is a third spelling owned by someone else (Porkbun) and is not connected.
6. **Privacy link** in the footer points to `#top`; there is no privacy page.
