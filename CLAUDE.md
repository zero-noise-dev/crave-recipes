# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static single-file landing page for **Crave Recipes** — an Android recipe app. The entire site is `index.html`. No build tools, no bundler, no dependencies to install.

## Workflow

1. Edit `index.html` in this project
2. Preview locally via the dev server (see below)
3. Deploy `index.html` to a static host (GitHub Pages, Netlify, etc.)
4. Record the live URL in the Android app project (`C:\Projects\recipe-pwa`) under Play Store Publishing

## Dev Server

```bash
# Start static file server (configured in .claude/launch.json)
npx serve -p 3000 .
```

Site is then available at `http://localhost:3000`.

## Architecture

All HTML, CSS, and JavaScript lives in a single file: `index.html`.

**Two-page layout via JS toggle** — the page has two top-level sections that are shown/hidden with `showMain()` / `showPrivacy()`:
- `#main` — the marketing landing page
- `#privacy` — the Privacy Policy

**External dependencies** (CDN only, no local installs):
- Google Fonts: Lora (serif headings) + Nunito (body)
- Lucide icons: `lucide.createIcons()` called once at page load; icons are declared as `<i data-lucide="icon-name">` in markup

**CSS variables** (defined on `:root`):
- `--accent: #f0954a` — orange, used for all interactive highlights
- `--bg: #1a1612` / `--card: #241f1a` — dark backgrounds matching the Android app palette

**Scroll animations** — `.fade-in` elements are observed via `IntersectionObserver`; adding `visible` class triggers the CSS transition.

**FAQ accordion** — `toggleFaq(btn)` closes any open item before opening the clicked one (only one open at a time).

**Mobile nav** — the desktop `<ul>` is hidden below 640px; a hamburger button opens `#mobileNav` (full-screen overlay). `openMobileNav()` / `closeMobileNav()` manage body scroll lock.

## App Feature Reference

This is the authoritative feature list for the Crave Recipes Android app. Use it when updating site copy.

### Import

| Feature | Notes |
|---|---|
| URL import | First option; JSON-LD extraction, HTML stripping fallback, JS-rendered detection, web search fallback |
| Photo / Camera | Full-res sent to AI for OCR |
| PDF import | Up to 40 pages; multi-recipe PDFs detected and split automatically |
| DOCX import | via mammoth.js |
| Paste text | |
| Duplicate detection | |
| Tag normalisation on import | |
| Bulk import with attribution | PDF/DOCX ≥2 recipes: bulk apply or per-recipe cycle |

### Browse & Search

| Feature | Notes |
|---|---|
| Search bar | |
| Sort order | Newest first (default) · A→Z toggle |
| Tag filter chips | |
| Filter by attribution | Bottom sheet with tag chips + attribution radio list; both filters combinable |
| Favourites filter | ❤️ chip; heart on cards + detail header |
| Grid / list view | |
| Home stats bar | Recipes · Tags · Avg Cook |

### Recipe Detail

| Feature | Notes |
|---|---|
| Serving scaler | Fraction display |
| Step check-off | Cooking mode |
| Measurement hints | Metric / US Imperial / US Cups / Weight; per-recipe override |
| Temperature converter | Auto-extracts from steps; manual fallback |
| Cook's notes | Free-text; shown below description |
| Edit screen | Drag/drop reorder; ingredient/method section dividers |
| PDF export / print | Filename case preserved; thumbnail on page 1 |
| Share as text / screenshot | |

### Settings

| Feature | Notes |
|---|---|
| Theme | Light · Dark · System · OLED · High Contrast |
| Font style | Readable (Atkinson Hyperlegible + Merriweather) / Default (Nunito + Lora) |
| Font size | S / M / L |
| Measurement mode | Metric / US Imperial / US Cups / Weight |
| Tags & Sources manager | Rename, delete, reset to defaults |
| API key management | Show/hide/save/clear |
| Backup & Restore | JSON export v4; includes recipes, photos, attributions, tags |

## Key Constants

| Item | Value |
|---|---|
| Play Store URL | `https://play.google.com/store/apps/details?id=nz.co.crave.recipes` |
| Contact email | `claude@crave.co.nz` |
