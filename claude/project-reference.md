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
