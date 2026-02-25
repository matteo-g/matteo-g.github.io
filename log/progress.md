# Project Log — matteo-g.github.io

## What this repo is
Jekyll site based on the **Academic Pages** template, hosted on GitHub Pages.
- Live URL: https://matteo-g.github.io
- Repo: https://github.com/matteo-g/matteo-g.github.io
- Branch: master (auto-deploys to GitHub Pages on push)
- Stack: Jekyll + Minimal Mistakes fork + Susy grid + SCSS

---

## Session 1 — 2026-02-25

### Goal
Restructure the default Academic Pages template into a minimal personal site
inspired by https://jmbenkert.ch/

### Design decisions
- Minimal aesthetic: no sidebar, centered content (max 720px), clean typography
- Light mode only (no dark mode toggle)
- Nav: Home | Research | Projects | CV | Side Quests

### New files created
| File | Purpose |
|------|---------|
| `_layouts/minimal.html` | New layout — no sidebar, extends default.html |
| `_sass/layout/_minimal.scss` | All CSS for the minimal layout: home hero, paper entries, side quest list |
| `_pages/research.md` | Research page (Working Papers + Publications), all placeholders |
| `_pages/project-management.md` | Project Management page, 3 placeholder projects |
| `_pages/side-quests.md` | Blog archive using Liquid loop over site.posts |

### Files modified
| File | What changed |
|------|-------------|
| `_pages/about.md` | Rewritten as Home page: `.home-hero` div with photo (left) + bio (right) |
| `_data/navigation.yml` | New nav: Home / Research / Projects / CV / Side Quests |
| `_config.yml` | author_profile→false globally; url→matteo-g.github.io; repo→matteo-g/...; added sitemap.md to exclude list |
| `assets/css/main.scss` | Added `@import "layout/minimal"` |
| `_includes/masthead.html` | Removed light/dark mode toggle button |
| `_includes/head/custom.html` | Added `localStorage.setItem('theme','light')` to force light mode |
| `_includes/footer/custom.html` | Removed hardcoded `<a href="/sitemap/">Sitemap</a>` link |
| `_pages/sitemap.md` | Added `published: false` (belt-and-suspenders with exclude in config) |

### Bugs fixed this session
1. **Sitemap link in body** — was hardcoded in `_includes/footer/custom.html`
2. **Dark mode for all visitors** — JS was reading OS `prefers-color-scheme: dark`; fixed by writing `localStorage` to "light" before JS runs
3. **"Side Quests" hidden in hamburger menu** — nav overflow; fixed by renaming "Project Management"→"Projects" in nav + tightening nav CSS

---

## Current state of placeholders (everything still TODO)

### _config.yml — update these fields
```yaml
title: "Matteo Grigoletto / Site Title"   # → just "Matteo Grigoletto" or similar
name: "Your Name"                          # → real name
description: "Your Name's academic portfolio"
author:
  name: "Your Sidebar Name"
  bio: "Short biography..."
  location: "Earth"
  employer: "Red Brick University"
  email: "none@example.org"
  googlescholar: "..."   # already has a real URL — verify it's correct
  orcid: "..."           # placeholder URL
  github: "academicpages"  # → matteo-g
  bluesky: "bsky.app"   # → real handle or remove
```

### _pages/about.md
- Replace "Your Name", "Placeholder Role", "Placeholder Institution"
- Replace placeholder bio paragraphs
- Replace placeholder@email.com
- Replace `/images/profile.png` with actual photo (upload to images/)

### _pages/research.md
- Replace placeholder paper titles, coauthors, years, journals
- Add real PDF links once files are in /files/

### _pages/project-management.md
- Replace 3 placeholder projects with real examples

### _pages/side-quests.md
- No content action needed — auto-lists posts from `_posts/`
- The existing placeholder posts (2012–2015) can be replaced or left until real posts are written

### /files/cv.pdf
- Does not exist yet — nav CV link is a dead link until uploaded

---

## Key architecture notes

- `_layouts/minimal.html` → extends `default.html` → renders `#minimal-main` div, no sidebar
- Sidebar is disabled globally via `author_profile: false` in all `_config.yml` defaults
- Dark mode is forcibly disabled via `localStorage.setItem('theme','light')` in `<head>`
- Nav item "Projects" links to `/project-management/` (page title stays "Project Management")
- The old template pages (`_publications/`, `_talks/`, `_teaching/`, etc.) still exist but are NOT in the nav — they're harmless leftovers
- `_pages/sitemap.md` excluded in `_config.yml` AND has `published: false`

## Next steps (likely session 2)
1. Fill in real personal info across `_config.yml` and `_pages/about.md`
2. Upload real profile photo to `images/`
3. Upload CV PDF to `files/cv.pdf`
4. Populate `research.md` with real papers
5. Populate `project-management.md` with real projects
6. Possibly refine the visual design (font, spacing, color of links, footer cleanup)
7. Consider removing or simplifying the footer (currently shows AcademicPages attribution)
