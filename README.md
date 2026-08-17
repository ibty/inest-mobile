# Inest Interiors — mobile concept (draft)

A single-page, mobile-first concept for [inestinteriors.com](https://www.inestinteriors.com).
No build step, no dependencies. `index.html` is the whole site.

**Status: draft.** Not the live site. Indexing is blocked — see below.

---

## Deploy

    git init
    git add .
    git commit -m "Mobile concept — draft"
    git branch -M main
    git remote add origin https://github.com/<you>/inest-mobile.git
    git push -u origin main

Then on GitHub: **Settings → Pages → Source: Deploy from a branch →
Branch: `main`, folder: `/ (root)` → Save.**

Live in 1–2 minutes at:

    https://<you>.github.io/inest-mobile/

Pushing to `main` redeploys automatically. Give it a minute, and
hard-refresh — GitHub's CDN caches aggressively.

---

## Files

    index.html   the entire site — markup, CSS and JS in one file
    .nojekyll    stops GitHub running Jekyll over the files
    robots.txt   blocks search engines while this is a draft

`.nojekyll` matters: without it GitHub pipes everything through Jekyll,
which silently ignores any file or folder beginning with an underscore
and can rewrite content unexpectedly. The empty file switches it off.

---

## Two things to know about a draft on GitHub Pages

**It is publicly reachable.** On free and Pro accounts, a Pages site is
public even when the repository is private. Private Pages requires
GitHub Enterprise. Anyone with the URL can open this. That's usually
fine for a draft you're circulating — just don't treat the URL as
secret, and don't put client pricing or unreleased project names in it.

**Indexing is blocked, deliberately.** This page reuses copy from the
live site almost verbatim. A second public copy of that content can
cannibalise `inestinteriors.com` in search results. Two guards are in
place:

- `robots.txt` with `Disallow: /`
- a `<meta name="robots" content="noindex, nofollow">` tag near the top
  of `index.html`, inside a marked comment block

**When this becomes the real site, remove both.** Leaving them in will
keep the site out of Google entirely.

---

## Before it stops being a draft

Every photograph is hotlinked from `inestinteriors.com`, so this page
depends on that host staying up, and the images load from a different
origin than the page itself.

To fix: download them into `img/`, convert to WebP at roughly 1200px
wide, then update the `B` constant in the script block and the three
hero `src` attributes. That will cut page weight by more than half.

Also worth doing before launch:

- swap the 3-image hero carousel for one image or a short muted video —
  the carousel costs bandwidth on mobile data for little gain
- grow the feed to 25–40 frames; a reels-style gallery needs volume
  before scrolling feels rewarding
