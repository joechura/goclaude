# Look match: does it look like the brands they picked?

When someone names inspiration brands, they're describing a whole look. Small details copied onto a different kind of page will pass every other check and still miss.

## Look read (per brand, from screenshots)
Fill this in before any design decision, using real measurements when you can read them from the page (`getComputedStyle`, element sizes).

| Item | Example |
|---|---|
| Page color | white, black strip on top |
| Photo share | full-width hero 650px tall at 1440; photos take over half the page |
| Title size/style | 60px weight 900, centered |
| Secondary type | 14px typewriter mono, caps, under titles |
| Section rhythm | title → row of items → 3 tall photo tiles, repeated |
| Buttons | small pills on photos, small black rectangle on white |
| Text amount | almost none: labels, not paragraphs |

## Lead brand
Pick one brand's look read as the page's skeleton. Other brands supply moves only where they fit that skeleton. Follow the user's lead if they point at one.

Translate the skeleton to the org's content by role: what's their hero subject, what plays the part of "product row", what plays the part of "photo tiles"? Keep the org's own name, logo, words and photos. Match the system without copying the brand's assets, logo or text.

## Side-by-side gate
1. Screenshot the preview at the same widths as the brand screenshots, with animations finished.
2. Give a separate agent only the images, not your reasoning or the plan. Ask: "Do these look like the same family of site? Compare page color, photo size, type, rhythm and text amount. Name each mismatch. Pass or fail."
3. On a fail, fix the named mismatches, in that order, and rerun. Up to two rebuilds. If it still fails, tell the user.

Failing signs: a different page color from the lead brand, under half the photo share, more text than the brand, or layouts the brand never uses.

## Corrections gate
List every correction the user made at the checkpoints. For each, point to where it shows on the first screen, or say where it moved and why. A correction that's only technically present (a list further down the page) doesn't count.
