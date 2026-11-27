# Jaswanth Duthulour — Digital Marketing Portfolio

Personal portfolio for Jaswanth Duthulour, Certified AI and Digital Marketing Specialist based in Dubai.
The owner supplies content section by section (text, logos, creatives, videos, dashboards); Claude builds it in.

- Live site (GitHub Pages, deploys automatically from `main`): https://duthulourjaswanth.github.io/duthulourjaswanth-Portfolio-/
- Repo: https://github.com/duthulourjaswanth/duthulourjaswanth-Portfolio-

## Stack

- One self-contained page: `index.html` (HTML + CSS + JS inline, no build step, no framework, no npm).
- Assets in `img/`. `.nojekyll` keeps GitHub Pages from processing files.
- Fonts: Syne (headings) and Manrope (body) from Google Fonts.
- To preview locally: `python3 -m http.server 8000`, then open http://localhost:8000

## Layout of index.html

Home sections (in order): hero `#top`, `#about`, `#expertise` (What I do), `#toolkit`, `#work` (Selected work),
`#brands` (Products and logo work + Websites I've built), `#journey`, `#credentials`, `#contact`.

Project subpages are full-screen overlays (`<div class="subpage" id="sp-NAME">`) opened by URL hash (`#modernfood`):
`findxpand`, `reachxpand`, `personaxpand`, `modernfood`, `vooki`, `insquad`, `lamsa`, `nfta`, `design`.
Routing lives in `const pages={...}` and `route()`. Each page can have a `runXx()` animation starter and an `xxClear()` stopper — register both in `route()` and in the clear list when adding a page.

## Content lives in JS data arrays (edit these, not the markup)

| What | Array / object |
|---|---|
| What I do | `services` |
| Toolkit | `kits` |
| Brand / product cards | `brandLogos` — `[key, name, bg, description, pageHash, tag, industry, imgSrc?, fit?]` |
| Journey timeline | `journey` (logos in `JLOGO`) |
| Certifications | `creds` (logos in `CLOGO`) |
| Design page | `DESIGN = {statics, carousels, profiles}` (formats in comments next to it) |
| Modern Food creatives | `MF_ADS`, `MF_SHOTS` (files `img/mf/mfNN-s.webp` thumb + `-l.webp` large) |
| Modern Food videos | `MF_VIDEOS` — `[file-stem, title, length, aspect]`, files in `img/mf/video/` (`stem.mp4` + `stem-poster.webp`) |
| Modern Food Facebook dashboard | `#mf-results` markup + `FB_DAILY` (daily views in thousands, traced from Meta Business Suite) |
| Vooki GIF/static posts | `VK_STATICS` + `#vk-g-posts` |

Lightbox: any element with `data-lb="<type>" data-i="<index>"` opens `#lb`; add new types in the delegated click handler (search `data-lb`).

## Conventions

- **Palette:** light only (dark theme is disabled via `data-theme=off`). White plus a friendly orange: `--hot:#ff8a3d; --deep:#f26419; --red:#ef6a1e; --ink:#3b2620`. No black backgrounds, don't overuse orange.
- **Images:** convert to WebP with Pillow (q ~82–92). Keep originals out of the repo. Transparent cut-outs (product packs) were made with `rembg` (isnet-general-use) and saved as WebP with alpha.
- **Video:** H.264 MP4, `-movflags +faststart`, 720p (`scale=1280:-2`, `-preset veryfast -crf 24`), poster frame as WebP. GIF-style clips: `muted loop playsinline`, play when in view.
- **Copy:** plain, specific, first person; no made-up stats. Use the real logo of every tool/brand (Iconify `logos`, simple-icons, devicon).
- **Mobile (≤640px):** grids listed in `RAILS` become horizontal swipe rails with dot indicators; What I do is an accordion; About has Read more; Journey steps clamp to 3 lines. When adding a new card grid, add its selector to `RAILS` so it stays short on phones.
- **Animations** respect `prefers-reduced-motion` via the `reduce` flag.
- Test at 1366×900 and 390×844 (Playwright works well) before pushing.

## Owner preferences

- Never delete or trash files without asking first (moving/renaming is fine).
- Commit and push to `main` after each finished change so the live site updates.
