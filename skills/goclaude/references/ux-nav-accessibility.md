# UX, navigation, above the fold, accessibility

## Nav audit (do this on the CURRENT site first)
1. Inventory every top-level item, every dropdown child, every header button, every footer link. Count them.
2. Flag: duplicates, jargon/internal names, items only one audience cares about, dead or redirecting links, multiple competing buttons (Donate + Join + Shop + Register…).
3. Propose the new nav:
   - **≤ 5 top-level items**, labeled in the visitor's words (verbs or plain nouns: "Programs", "Events", "About", not "Our Impact Initiatives").
   - **One primary button** (the direct CTA). One quiet secondary text link (often Donate) is fine.
   - Dropdowns: ≤ 7 children, grouped by audience or task, no nested flyouts.
   - Everything else moves to the footer or a hub page.
4. Produce a **mapping table**: every old item → its new home (top nav / hub page / footer / removed + why). Nothing silently disappears. Long lists (e.g. 30 city pages) can be one row ("32 chapter pages → Chapters directory, off the menu").
5. Also check the **current links work**. Broken hrefs, menus that open the wrong page, and stale years are quick wins to report.

## Above the fold (first screen on a 390×844 phone AND a 1440×900 desktop)
Must answer in 5 seconds:
- **What do you do?** Headline in plain words, ≤ 10 words. Not a slogan the visitor has to decode.
- **For whom / why does it matter?** One-line subhead.
- **What do I do next?** Direct CTA button (high contrast) + transitional CTA (lower weight).
- **Is this real?** A real photo/video of the actual people/work, and ideally one proof point (a number, a credential).

Test: cover the logo. Could a stranger say what the org does? If not, rewrite the headline.

## CTA hub pattern ("Get Involved")
When there are multiple audiences, the direct CTA goes to a hub page with one clear card per path (e.g. Participate / Volunteer / Donate / Partner / Start a chapter). Each card: who it's for, what happens next, one button. Donation stays one click from every page via header/footer.

## Accessibility (WCAG 2.2 AA is the floor, not a stretch goal)
- **Contrast:** text ≥ 4.5:1 (large text ≥ 3:1), UI components and focus rings ≥ 3:1. Check text over images: add a scrim.
- **Keyboard:** everything reachable and operable by Tab/Enter/Space/Esc; visible `:focus-visible` style; skip link to main content as the first focusable element; menus close on Esc and return focus.
- **Structure:** one `<h1>` per page, no skipped heading levels, landmarks (`header`, `nav`, `main`, `footer`), `lang` on `<html>`.
- **Targets:** touch targets ≥ 44×44px; no hover-only content.
- **Media:** meaningful alt text; decorative images `alt=""`; captions on video; no autoplaying audio; pause control on any moving background.
- **Motion:** honor `prefers-reduced-motion` (see motion.md).
- **Forms:** visible labels (not placeholder-only), errors in text not just color, `autocomplete` attributes.
- **Text:** body ≥ 16px, line length 45–80ch, works at 200% zoom with no horizontal scroll.
- **Language:** plain language, short sentences, person-first or community-preferred terms (use the org's own wording; if unsure, ask).

### Verify, don't assume
After building, run an automated check when possible (e.g. `npx @axe-core/cli <url>` or Lighthouse accessibility) and fix every violation, then do a manual keyboard pass. Report the results, including anything not fixed.
