# Personal site — Dmitrii Nikolaev

Single self-contained page. No build step, no dependencies, no external requests: open `index.html`
in a browser and it works, on disk or on any static host.

## Files

- `index.html` — the whole site (HTML + CSS + a few lines of JS, ~27 KB)
- `img/avatar.png` — the hero portrait
- `cv.pdf` — the PDF the "📄 CV" chip links to. Currently a copy of `<repo>/cv-dev/cv-dev.pdf`.
  Replace it whenever the master CV changes: `cp ../cv-dev/cv-dev.pdf cv.pdf`

## Publishing on GitHub Pages

1. Create a repository — `<username>.github.io` for a user site, or any repo for a project site.
2. Copy `index.html`, `cv.pdf` and `img/` into it, commit and push.
3. Repo → Settings → Pages → Source: "Deploy from a branch", branch `main`, folder `/ (root)`.
4. The site appears at `https://<username>.github.io/` within a minute or two.

## Editing

Everything is in one file, in document order: hero → featured projects → experience → skills →
education → languages → footer. The colour palette is the six variables at the top of `<style>`:

```
--bg      page background        --accent   copper, links and headings
--card    card background        --accent2  blue, used in tags
--ink     body text              --line     borders
```

Experience entries are `<article class="job">` blocks with two `<details>` sections — "What the work is"
is open by default, "Highlights" is collapsed. The jump navigation is a plain list of anchors; if you
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

## Deliberately not included

- **No numbers that are not verified.** The percentages in `scratchpad/bullets.md` (40% token generation,
  30% VRAM, 28% MAP, 19% pricing accuracy, request volumes, latencies) appear nowhere on this page. A
  public page is the worst place for a figure you cannot defend. Confirm them and they can be added to
  the Highlights lists, where they would be the strongest content on the page.
- **No gallery, hobbies, certificates or courses sections.** There is no material for them in this repo.
