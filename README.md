# Neolith — company site

Static rebuild of the Neolith marketing site (https://neolithapp.com/en), published with
GitHub Pages at **https://neolith-lab.github.io**.

The live site is a Next.js app; this is a plain HTML + CSS reproduction of the same
content — no build step, no dependencies, no runtime JS beyond a small theme toggle.

## Files

    index.html            the whole page (header, hero, capabilities, services, footer)
    styles.css            all styling; dark theme by default, light theme via the toggle
    assets/                logo, mockup image, fonts, contributor avatars
    .nojekyll              tells GitHub Pages to serve the files as-is

## Editing

Everything is hand-editable:

- **Copy** lives inline in `index.html`. Section order: hero → capability cards → services → footer.
- **Colours and spacing** are CSS variables at the top of `styles.css` (`--bg`, `--accent`, `--muted`, …).
- **Adding a capability card**: copy one `<article class="card">` block. The thin coloured
  rule on top of each card is driven by `.card:nth-child(n)::before`.
- **Adding a service**: copy one `<div class="service">` block; even-numbered rows flip the
  image to the left automatically.

Dark is the default theme and matches the live site; the header toggle switches to light
and remembers the choice in `localStorage`.

## Local preview

    python3 -m http.server 8899
    # then open http://localhost:8899

Opening `index.html` directly with `file://` also works.

## Deploying

This repo is the Pages source: the branch is published from the repository root, so
committing to `main` is the deploy. Nothing to build.

## Content note

All copy, imagery and the footer notice are taken from the live site so the two stay in
sync. Blog and contact pages are still served by the Next.js site; the header links there.
