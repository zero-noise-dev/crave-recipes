# Crave Website — Session Handoff

*Summarised from the recipe-pwa Claude Code session, 1 Jun 2026*

---

## Context

The Crave Recipes Android app (`C:\Projects\recipe-pwa`) has a pre-launch task to build a website for the Play Store submission (privacy policy, app listing, download CTA). A website was created in Claude chat using `project.md` as the content source. The HTML and a design-summary MD file were downloaded locally.

---

## Decisions Made

**Project structure**
- Website lives in its own folder: `C:\Projects\crave-website` — separate from the Android app project
- The two projects are independent; once the website is live, its URL gets recorded in `project.md` under Play Store Publishing

**The downloaded MD file**
- Not strictly necessary — the HTML itself is the source of truth
- Can be used as a content brief when prompting the design skill, in place of copying from `project.md` directly
- Set aside unless it's well-structured enough to be useful as input

**Skill usage**
- The installed design skill is not modified — it's run normally with your content passed as context in the same message
- No new custom skill is created

---

## Next Steps

1. ✅ Create `C:\Projects\crave-website` folder
2. ✅ Open a new Claude Code session rooted there
3. Run the design skill with the following as context:
   - The existing HTML file (read or paste it)
   - Section 2 (feature table) from `C:\Projects\recipe-pwa\claude\project.md` — the authoritative content source
   - App colour palette: accent orange `#f0954a`, dark bg `#1a1612`, card `#241f1a`
   - App name: **Crave Recipes**, package ID: `nz.co.crave.recipes`
   - Request: polished multi-section landing page — hero, features, screenshots placeholder, privacy policy stub, Play Store download CTA
4. Save the output HTML back to this folder
5. Once the site is live, record its URL in `project.md` → Section 7 → Play Store Publishing

---

## Design Skill Prompt Template

> "Here is my existing HTML: [paste or read file]. Here is the app feature list and design context: [paste Section 2 from project.md + colour palette above]. Use the design skill to produce a polished multi-section landing page with: hero section, feature highlights, screenshots placeholder, privacy policy stub, and a Play Store download CTA."

---

## App Content Reference

Key details to keep consistent with the Android app:

| Item | Value |
|---|---|
| App name | Crave Recipes |
| Package ID | nz.co.crave.recipes |
| Accent colour | `#f0954a` (orange) |
| Dark background | `#1a1612` |
| Card background | `#241f1a` |
| Font (heading) | Lora or Merriweather |
| Font (body) | Atkinson Hyperlegible or Nunito |
| Tagline (suggested) | Zero tracking. Zero sign-up. |
| Features summary | AI recipe import (URL, photo, PDF, DOCX), serving scaler, measurement hints, PDF export, offline/local storage |
