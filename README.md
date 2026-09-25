# Personal site — Dmitrii Nikolaev

Single self-contained page. No build step, no dependencies, no external requests: open `index.html`
in a browser and it works, on disk or on any static host.

## Files

- `index.html` — the whole site (HTML + CSS + a few lines of JS, ~27 KB)
- `cv.pdf` — the PDF the "📄 CV" chip links to. Currently a copy of `<repo>/cv-dev/cv-dev.pdf`.
  Replace it whenever the master CV changes: `cp ../cv-dev/cv-dev.pdf cv.pdf`

## Publishing on GitHub Pages

1. Create a repository — `<username>.github.io` for a user site, or any repo for a project site.
2. Copy `index.html` and `cv.pdf` into it, commit and push.
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

## Deliberately not included

- **No numbers that are not verified.** The percentages in `scratchpad/bullets.md` (40% token generation,
  30% VRAM, 28% MAP, 19% pricing accuracy, request volumes, latencies) appear nowhere on this page. A
  public page is the worst place for a figure you cannot defend. Confirm them and they can be added to
  the Highlights lists, where they would be the strongest content on the page.
- **No photo.** Add one with an `<img class="hero-photo">` next to the hero text if you want one.
- **No gallery, hobbies, certificates or courses sections.** There is no material for them in this repo.
