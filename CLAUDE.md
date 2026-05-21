# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static GitHub Pages site hosted at `second-chances.me` (set via `CNAME`). Built on the [Massively](https://html5up.net/massively) template by HTML5 UP. No build step or package manager — changes to HTML/CSS/JS are deployed directly by pushing to `main`.

## Architecture

### Pages
- `index.html` — main page with featured post, post grid, pagination, and contact form
- `generic.html` — generic article/content page
- `elements.html` — UI component reference (buttons, forms, tables, etc.)

### Styles
SASS source lives in `assets/sass/` and compiles to `assets/css/main.css`. The compiled CSS is committed to the repo. If SASS is compiled locally, run:

```bash
sass assets/sass/main.scss assets/css/main.css
```

SASS is organized as:
- `libs/` — variables, mixins, breakpoint system, vendor prefixes
- `base/` — reset, page defaults, typography
- `components/` — buttons, forms, icons, images, etc.
- `layout/` — wrapper, intro, header, nav, main, footer, navPanel

Breakpoints are defined in both `main.scss` and `assets/js/main.js` and must stay in sync: `xxsmall` (≤360px) through `default` (≥1681px).

### JavaScript
`assets/js/main.js` handles: parallax background (`#wrapper`), scroll-triggered intro hide/show (via Scrollex), responsive nav panel (desktop nav moves to slide-out panel on ≤medium breakpoint), and page load animations (removes `is-preload` from `body`).

Dependencies (all vendored, no npm):
- jQuery, jquery.scrollex, jquery.scrolly — scroll effects
- browser.min.js — browser/OS detection used to disable parallax on mobile/IE/HiDPI
- breakpoints.min.js — responsive JS breakpoints
- util.js — panel plugin for the mobile nav drawer

## Deployment

Push to `main` — GitHub Pages serves the site automatically. No CI or build pipeline.
