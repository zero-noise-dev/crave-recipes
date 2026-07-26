# Crave Website — Project Reference

This file is an archive of completed work and session history. Updated via `ARCHIVE` command when CLAUDE.md grows too large.

---

## Session: 2 June 2026 — Hero Image Swap & Copy Polish

Replaced the duo-split phones graphic with `hero-home-page-light.png`. Tightened all API key copy to remove misleading "free" references — the key itself costs nothing to create but requires purchased credits, so calling it free was inaccurate in context. Updated two FAQ answers to be more direct.

### Changes Made

- **Screenshots section:** `duo-split-transparent.png` swapped out for `hero-home-page-light.png`; alt text updated
- **API key heading:** "with a free API key" → "with a Claude API key"
- **API key CTA link:** "Get your free API key →" → "Get your API key →"
- **API key body copy:** Removed "Anthropic offers free credits when you sign up"
- **FAQ — API key cost:** Removed "Anthropic also offers free credits when you first sign up"
- **FAQ — Do I need a key:** "The key is free to obtain from Anthropic's website" → "You can get a key from Anthropic's website"
- **FAQ — iOS:** "Not currently. Crave is Android-only for now." → "No. Crave is Android-only."
- **FAQ — Nutritional info:** "No. Food is made to be enjoyed, not counted." → "No. Food is for enjoying, not calculating."

---

## Session: 6 June 2026 — Polish, Pexels, Privacy URL & Store Assets

A broad session covering several independent changes across the site plus creation of Google Play Store screenshot assets.

### Changes Made

**Dedicated privacy page**
- Created `privacy/index.html` as a real static page at `https://recipes.crave.co.nz/privacy` (replaces JS toggle)
- All nav and footer Privacy links in `index.html` updated to point to `/privacy`

**Unsplash → Pexels**
- Replaced all Unsplash references with Pexels (`pexels.com/api`) across `index.html` and `CLAUDE.md`
- Updated Settings path to "Settings → Pexels API Key"

**Contact email fix**
- Corrected `recipe@crave.co.nz` → `recipes@crave.co.nz` in `index.html`, `privacy/index.html`, and `CLAUDE.md`

**Google Play buttons — Coming Soon state**
- All "Free on Google Play" buttons replaced with non-clickable "Coming to Google Play" (`btn-coming-soon` style) pending app approval
- Footer Google Play link changed to plain text
- Task added to CLAUDE.md to restore active links once app is approved

**Pillars grid fix**
- Changed `repeat(auto-fit, minmax(175px,1fr))` to `repeat(3,1fr)` — eliminates empty background slots on wide viewports

**Text wrapping fixes**
- `&nbsp;` chains added to prevent orphaned words: "Free&nbsp;forever", "handles&nbsp;it&nbsp;all", "phone&nbsp;a&nbsp;pleasure"
- Second sentences in Zero Sign-Up, Local Storage, and Backup & Restore pillar cards forced to new line with `<br>`

**Revert commands added to quick reference**
- `claude/claude-quickref.md` updated with safe (`revert`) and destructive (`reset --hard`) revert instructions

**Google Play Store screenshot assets**
- Created `store-assets/screenshots.html` — 4 branded 1080×1920 slides (Home, Import, Recipe Detail, Edit)
- Dark palette, Lora serif headlines, orange accent chips — consistent with site design
- Screenshots generated via Chrome DevTools (Vivaldi has a known bug with this feature over RDP; use Chrome/Edge instead)
- Files stored in `store-assets/` alongside the HTML template; 5MB PNGs are within Google Play's 8MB limit

---

## Session: 2 June 2026 — Unsplash API as Second Optional Enhancement

Added Unsplash photo API alongside Claude API as a second optional enhancement. Redesigned the API section from a single description+steps card into two side-by-side provider cards. Updated FAQ to cover both keys. Updated CLAUDE.md feature reference.

### Changes Made

- **API section redesign:** Replaced `.api-box` (single card, description left / steps right) with `.api-providers` grid (two equal cards side by side, stacks on mobile)
- **Claude API card:** Label "AI Import"; same steps, updated Settings path to "Settings → Claude API Key"
- **Unsplash API card:** Label "Recipe Photos"; 4-step setup pointing to `unsplash.com/developers`; described as completely free
- **FAQ:** "Do I need a Claude API key?" → "Do I need an API key?" covering both; "How much does the API key cost?" → "How much do the API keys cost?" with Unsplash noted as free
- **CLAUDE.md:** Settings feature reference updated to note both API keys

---

## Session: 2 June 2026 — Dedicated Privacy Page

Added `privacy/index.html` as a real static page served at `https://recipes.crave.co.nz/privacy` so Google Play can verify the app's privacy policy URL. Previously the privacy policy was only accessible via a JS toggle (no real URL). Updated all nav and footer Privacy links in `index.html` to point to `/privacy` directly.

### Changes Made

- **Created `privacy/index.html`:** Standalone page with same dark palette, fonts, and nav as the main site; "Privacy" nav item marked active; "Back to home" links to `/`
- **`index.html` nav/footer:** All three Privacy links (desktop nav, mobile overlay, footer) changed from `onclick="showPrivacy()"` to `href="/privacy"`
- **CLAUDE.md:** Task marked done

---

## Session: 2 June 2026 — Screenshot Section, FAQ Polish, UI Tweaks

Replaced carousel with a single duo-split image floating over a blurred flat-lay kitchen background. Background removed from duo-split PNG using Python flood-fill (seeded from all edges, tolerance 40). Hero and FAQ copy polished. Git username set globally.

### Changes Made

- **Screenshot section:** Carousel removed (mobile pinch/zoom conflict). Now a single section with blurred/darkened `flat lay-home page.png` as background, and `duo-split-transparent.png` (phones with transparent background) floating over it
- **duo-split-transparent.png:** Generated via Python/Pillow flood-fill background removal — seeds from all 4 edges, tolerance 40
- **Hero:** Removed "Android Only" badge
- **Play Store buttons:** Standardised to "Free on Google Play" (was inconsistent)
- **FAQ:** Renamed "Surely there's some catch?" → "What's the catch?"; grouped both API questions together; API key answer rewritten to lead with "No. But..."; added "Is there nutritional information in recipes? No. Food is made to be enjoyed, not counted." as final entry
- **Git:** Global `user.name` set to `zero-noise-dev`; noted in CLAUDE.md

---

## Session: 1 June 2026 — Screenshots Replaced

Replaced all placeholder screenshots on the landing page with 7 new real-app images. Recommended and implemented a two-tier layout: the duo-split image (showing light and dark mode side-by-side) sits as a wide hero element above four cohesive flat-lay phone frames. The old Cooking Mode placeholder and "coming soon" note were removed. Changes committed and pushed to master.

### Changes Made

- **duo-split hero:** `duo-split-home page.png` displayed as a wide rounded block above the phone frames; new `.duo-split` CSS class added
- **4 flat-lay frames:** Home (`flat lay-home page.png`), Ingredients (`mix-recipe-ingredients.png`), Method (`mix-recipe-method.png`), Settings (`mix_recipe-settings.png`)
- **Removed:** old `home-screen.jpg`, `recipe-detail-bagel.jpg`, `import-screen.jpg` references and the Cooking Mode placeholder div
- **Unused images committed:** `floating-home-page.png`, `mix-recipe-import.png` (available for future use)
- **CLAUDE.md:** Done list updated; Screenshots task reduced to Cooking Mode only (still pending)

---

## Session: 1 June 2026 — Workflow Setup, Tasks, Quick Reference

Set up the claude workflow structure for this project to mirror recipe-pwa. Created `claude-quickref.md` with commands (DISPLAY, COMMIT, WRAP, ARCHIVE, BATCH, etc.) and `project-reference.md` as the session archive. Added 3 outstanding tasks to CLAUDE.md. WRAP command defined to write session summary here.

### Changes Made

- Created `claude/claude-quickref.md` with full command reference including GitHub Pages deploy notes
- Created `claude/project-reference.md` as archive (replacing Word doc reference guide)
- Added CLAUDE.md quick reference section pointing to both files
- Added tasks: Cooking Mode screenshot, Record live URL, API key rotation reminder

---

## Session: 1 June 2026 — Nav Fixes, API Key Reframe, Email Update

Updated the Crave Recipes landing page (`index.html`) with three fixes. Nav links for Features and FAQ were broken when viewing the privacy page — fixed by adding `showMain()` calls. The API key section was rewritten to present it as an optional enhancement rather than a requirement. The contact email was updated from `claude@crave.co.nz` to `recipe@crave.co.nz` throughout.

### Changes Made

- **Nav fix:** added `onclick="showMain()"` to Features and FAQ links so they work from the privacy page
- **API key section:** label changed to "Optional Enhancement"; headline rewritten to "Unlock the full power with a free API key"; copy now leads with "Crave works great out of the box"
- **Contact email:** updated to `recipe@crave.co.nz` in Privacy Policy and CLAUDE.md Key Constants
- **Committed and pushed** to master; auto-deployed to https://recipes.crave.co.nz
