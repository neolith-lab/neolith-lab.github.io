# Neolith — company site

Static rebuild of the Neolith marketing site (https://neolithapp.com/en), published with
GitHub Pages at **https://neolith-lab.github.io**.

The live site is a Next.js app; this is a plain HTML + CSS reproduction of the same
content — no build step, no dependencies, no runtime JS beyond a small theme toggle.

## Files

    index.html            the whole page (header, hero, capabilities, services, footer)
    styles.css            all styling; dark theme by default, light theme via the toggle
    blog/index.html       the blog index; the newest post is featured on top
    blog/*.html           one page per post (~450-680 words, all "3 min read")
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

## Blog

`blog/index.html` lists the posts; each post is its own file in `blog/`. To add one, copy
an existing post page and replace the title, the `.post-meta` line (date and read time) and
the `.post-body` contents. Then add a matching `<a class="post-card">` to `blog/index.html`.

Everything currently in `blog/` was written for this site — the topics trace back to the
services on the landing page: voice agents, agentic systems, workflow audits, last-mile
queries and human-in-the-loop design. `agentic-ai-components.html` is based on the team's
own write-up of agentic architectures. To feature a different post on top, move its
`<a class="featured-post">` block and add its card to the list below.

Read times are stated at roughly 225 words per minute, rounded up, so all posts sit at
"3 min read".

## Content note

Copy, imagery and the footer notice on the landing page are taken from the live site so the
two stay in sync. The blog is original to this repo; contact is the sales mailto address.
