# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static single-file landing page for **Crave Recipes** — an Android recipe app. The entire site is `index.html`. No build tools, no bundler, no dependencies to install.

## Workflow

1. Edit `index.html` in this project
2. Preview locally via the dev server (see below)
3. Deploy by pushing to `master` — GitHub Pages auto-deploys to `https://recipes.crave.co.nz`
4. Record the live URL in the Android app project (`C:\Projects\recipe-pwa`) under Play Store Publishing

## Quick Reference

See [`claude/claude-quickref.md`](claude/claude-quickref.md) for the full command reference (DISPLAY, COMMIT, WRAP, ARCHIVE, etc.).
Completed work is archived in [`claude/project-reference.md`](claude/project-reference.md).

**Command definitions:**
- `WRAP` — summarise the session, update the Done list in CLAUDE.md, save memory, and write the session summary to `claude/project-reference.md`
- `ARCHIVE` — move completed/stale tasks from CLAUDE.md Tasks section to `claude/project-reference.md`
- `DISPLAY` — show all pending tasks from CLAUDE.md
- `COMMIT` — commit and push to master; GitHub Pages deploys automatically within ~1 minute

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

## Hosting

- **Platform:** GitHub Pages — repo `zero-noise-dev/crave-recipes`
- **Live URL:** https://recipes.crave.co.nz
- **DNS:** Cloudflare CNAME `recipes` → `zero-noise-dev.github.io` (DNS only, not proxied)
- **Deploy:** push to `master` branch — site updates automatically within ~1 minute

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
| API key management | Claude API key + Pexels API key; show/hide/save/clear |
| Backup & Restore | JSON export v4; includes recipes, photos, attributions, tags |

## Tasks

### Pending

- [ ] **Record live URL** — add `https://recipes.crave.co.nz` to `C:\Projects\recipe-pwa` under Play Store Publishing
- [x] **Dedicated privacy URL** — `privacy/index.html` created; nav/footer links updated to `/privacy`; live at `https://recipes.crave.co.nz/privacy` (2 Jun 2026)
- [ ] **API key** — remove or rotate the Claude API key stored in app settings once current Anthropic credit runs out
- [x] **Google Play buttons** — restored to active links pointing to live Play Store listing (hero, bottom CTA, mobile nav, both footers)

### Done

- [x] Initial landing page — hero, features, import, cooking features, FAQ, privacy policy
- [x] Privacy policy reviewed and finalised (1 Jun 2026)
- [x] Git initialised
- [x] 'Built for Cooking' section added (1 Jun 2026)
- [x] Deployed to GitHub Pages — https://recipes.crave.co.nz (1 Jun 2026)
- [x] Nav links fixed (Features/FAQ now work from privacy page), API key section reframed as optional, contact email updated to recipes@crave.co.nz (1 Jun 2026)
- [x] Screenshots replaced — duo-split dark/light hero + carousel with 5 slides (Home, Ingredients, Method/Cooking, Settings); method screen serves as Cooking Mode (2 Jun 2026)
- [x] Screenshot section redesigned — single duo-split (background removed via Python flood-fill) floating over blurred flat-lay background; carousel removed (2 Jun 2026)
- [x] Hero/FAQ polish — removed Android badge, standardised Play buttons, FAQ copy improvements, nutritional info FAQ entry added (2 Jun 2026)
- [x] Git username set globally to zero-noise-dev (2 Jun 2026)
- [x] Hero image replaced with hero-home-page-light.png (2 Jun 2026)
- [x] API key wording and FAQ copy tightened — removed 'free' references, updated iOS and nutritional answers (2 Jun 2026)

## Privacy Policy Notes

Decisions made in session 1 worth preserving:

- App stores (especially Apple) want data categories listed even when the answer is none — the "table below reflects this" line was added for that reason.
- API key warning ("treat like a password… remove before sharing backups") was added because the JSON export v4 backup includes the API key.
- Use **"Crave Recipes"** consistently throughout the policy — never just "Crave".
- Date format: `D Month YYYY` (e.g. `1 June 2026`) so it's unambiguous if updated later in the same month.

## Git

Always commit as `zero-noise-dev` — this is the GitHub handle used for all commits on this account. The global git config is set; do not override it.

## Key Constants

| Item | Value |
|---|---|
| Live URL | `https://recipes.crave.co.nz` |
| GitHub repo | `zero-noise-dev/crave-recipes` |
| Play Store URL | `https://play.google.com/store/apps/details?id=nz.co.crave.recipes` |
| Contact email | `recipes@crave.co.nz` |
