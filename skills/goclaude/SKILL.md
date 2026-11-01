---
name: goclaude
description: Use when starting or redesigning a website and it must not look AI-generated or templated, especially when given an existing site URL to rebuild, inspiration brands to borrow from, or a need to clarify the org's story, CTA, navigation, above-the-fold content, accessibility, or real media before building.
---

# goclaude

Turn an existing site URL + 1–3 inspiration brands into a confirmed plan (`DESIGN.md`) and a first preview, before the full build. The site should feel made by people who know the org: real brand, real words, real media, a clear story, a clean nav, accessible motion.

**Core rule: every design decision traces to a source.** That means the org's real brand or content, a named move from an inspiration brand you actually visited, or an accessibility/UX rule. Anything without a source is a default, and defaults are what make sites look AI-made.

## Working with the user
The user may be on a phone. Keep each message short, ask one thing at a time, and stop at exactly **three checkpoints** (marked ⏸). Between checkpoints, work without asking.

## Steps

### 1. Intake ⏸
If not already given, ask for the current site URL. Then ask:
> "What brand websites have the look and feel you want? Give me 1 to 3."

Accept 1–3 brand names or URLs. If the user gives more than 3, ask them to pick 3.

### 2. Scan (no questions)
Use real fetches (WebFetch or curl). If a site blocks you (bot wall, maintenance page, tiny response), retry with a browser tool if one is available. Otherwise ask the user for a screenshot. Don't work from memory.
- **Current site:** homepage + every top-level nav page. Record the nav inventory (all items, dropdown children, header buttons, footer links, with counts), CTAs, logo, brand colors and fonts (from CSS), mission wording, programs, **real stats with their source URL**, platform, and donation/signup providers.
- **Social channels:** linked from the header/footer. Pull the YouTube video list and thumbnails, and note Instagram/Facebook handles. See `references/media.md`.
- **Each inspiration brand:** fetch its homepage and one inner page. Write 2–3 *specific, buildable moves* per brand (see `references/anti-ai-look.md`). "Bold and athletic" is not a move.
- **Generators:** note whether this session has Higgsfield tools, an `OPENAI_API_KEY`, or neither.

### 3. Confirm the org + strategy ⏸
Send one compact message:
1. "Here's what I think [org] is: [one sentence]. Right?"
2. StoryBrand: audiences, problem, guide, 3-step plan, **direct CTA**, transitional CTA, one-liner (`references/storybrand.md`). If there are multiple audiences, the direct CTA is a **hub** (e.g. "Get Involved"), not a single-audience action like "Donate".
3. Nav: current count and problems (broken links, duplicates) → proposed ≤5 items + one primary button. Add a mapping table **grouped by old menu**, one row per group (`references/ux-nav-accessibility.md`). The item-by-item table goes in `DESIGN.md`.
4. Above the fold: headline (≤10 words, says what they do), subhead, buttons, media, proof point.
5. Look: one line per inspiration brand naming the moves you'll borrow, plus one line for the org's own brand (colors and fonts you'll keep or fix).
6. **Facts to confirm:** list every place where the org's own sources disagree (e.g. three different chapter counts) or where a key fact is missing. Never pick one silently.

Wait for "yes" or corrections. Apply corrections without re-asking everything.

### 4. Write `DESIGN.md` (no questions)
Fill `templates/DESIGN.md` at the project root. Every token, move, and stat has a source. Unknown facts go in as `[TODO: …]` under Open questions. **Never invent stats, quotes, names, prices, or dollar impacts.**

### 5. Preview ⏸
Detect the stack. If the repo is empty, use Astro. Build **only** the header/nav, hero, one stats band with counters, and the footer, with parallax and counters per `references/motion.md`. Use real media. Generate media only after the user approves the cost (`references/media.md`).

Push to a branch and give the user the preview URL, plus one line for each: what's borrowed from where, and what to look at. Ask: "Go, or what should change?"

### 6. Build + verify
Build the rest from `DESIGN.md`: homepage sections, the CTA hub page, and the nav targets. Then verify:
- Run an automated accessibility check (axe/Lighthouse) and a keyboard pass. Fix what they find.
- Test reduced motion: no parallax, final numbers shown.
- Test at a 390px phone width and at desktop width.
- Run the anti-AI final check (`references/anti-ai-look.md`).

Report what passed and what's still open.

## Hard rules
| Rule | Why |
|---|---|
| Fetch inspiration sites; don't describe them from memory | Memory gives vibes; vibes give generic design |
| Confirm what the org is before strategy | A wrong premise wastes the whole build |
| No invented stats, quotes, or copy | Credibility; use `[TODO]` |
| Old→new nav mapping for every item | Decluttering must not lose pages people need |
| Never generate or AI-alter images of the org's real people or the community it serves | Misrepresents real people. Crop, upscale, and background removal are OK; synthetic bodies or motion are not |
| Generators only with user-approved cost | It's the user's money |
| Reduced-motion + keyboard + contrast before "done" | Accessibility is the floor |

## References
- `references/storybrand.md`: BrandScript slots, multi-audience hub CTA, section order
- `references/ux-nav-accessibility.md`: nav audit, above-the-fold test, WCAG checklist
- `references/anti-ai-look.md`: banned defaults → replacements, borrowed-move format
- `references/motion.md`: accessible counters + CSS parallax code
- `references/media.md`: real media sourcing, gallery, generator choice + spend rules
- `templates/DESIGN.md`: the output
