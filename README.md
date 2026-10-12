# Personal site — Dmitrii Nikolaev

Single self-contained page. No build step, no dependencies, no external requests: open `index.html`
in a browser and it works, on disk or on any static host.

## Files

- `index.html` — the whole site (HTML + CSS + a few lines of JS, ~32 KB)
- `img/avatar.png` — the hero portrait
- `cv.pdf` — the PDF the "📄 CV" chip links to. A copy of `../resume/base/cv-eng_.pdf`.
  Replace it whenever the base CV changes: `cp ../resume/base/cv-eng_.pdf cv.pdf`

## Publishing on GitHub Pages

1. Create a repository — `<username>.github.io` for a user site, or any repo for a project site.
2. Copy `index.html`, `cv.pdf` and `img/` into it, commit and push.
3. Repo → Settings → Pages → Source: "Deploy from a branch", branch `main`, folder `/ (root)`.
4. The site appears at `https://<username>.github.io/` within a minute or two.

## Editing

Everything is in one file, in document order: hero → experience → skills →
education → languages → footer. The colour palette is the six variables at the top of `<style>`:

```
--bg      page background        --accent   copper, links and headings
--card    card background        --accent2  blue, used in tags
--ink     body text              --line     borders
```

Experience entries are `<article class="job">` blocks with project summaries and technology tags.
The orange `.where` subtitle identifies the client or project team; put technical details in the description and tags.
The jump navigation is a plain list of anchors; if you
add or rename a job, update both the `id` on the article and the link in `<nav class="jump">`.

### Portrait and frame

The hero portrait is `img/avatar.png`, shown at 190 px inside `<div class="hero-porthole">`. To swap the
picture, replace the file or change the `src` on `<img class="hero-photo">`.

Two frame styles are built in:

- **Porthole** (default) — a round frame with a thin copper ring, a navy rim and eight small marks.
  Markup: `<div class="hero-porthole">`.
- **HUD** — the photo floats inside copper corner brackets and a dashed tick ring, with no solid rim.
  Markup: `<div class="hero-porthole is-hud">`.

To switch, add or remove `is-hud` on that div; the CSS for both lives next to each other in `<style>`.

To tune the porthole, edit these rules in `.hero-porthole`:

- `padding` — gap between the photo and the rim (default `3px`).
- `box-shadow` — the rings, innermost first: copper ring `1px`, navy rim `2.5px`, faint outer copper
  `3px`. Keep the hover rule in `.hero-porthole:hover` in step with it.
- `.hero-porthole::after` — the marks: the `1.2deg` in `repeating-conic-gradient` sets their width,
  `45deg` their spacing (eight marks), and the `2px`/`1px` in the `mask` their radial size.
- `--port` — overall frame size (default `190px`).

## Content source

Use `../resume/base/cv-eng.tex` as the primary content source for current roles, results and education.
Retain complementary projects from the longer website history; omissions from a short CV do not
mean those projects should be removed from the website. The latest content update was
12 October 2026. Keep benchmark and production contexts, hardware configurations and qualifiers
such as "up to", "approximately", "best measured" and "indicated" attached to performance claims.
Keep client descriptions anonymous as supplied in the resume. The publications section is a
selected list, matching the base resume.
