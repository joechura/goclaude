# Media: real first, generated only for atmosphere

## Priority order
1. **The org's own media**: images on its current site, YouTube, Instagram, Facebook, press kit.
2. **Media the user supplies** (links, uploads, screenshots).
3. **Generated atmosphere** (only if a generator is available, see below).
4. **No image**: typography, color, texture. Better than stock or fake.

Never use generic stock photos. They are the #1 tell of a template/AI site.

## Finding the org's media
- Scrape the site's `<img>`, `og:image`, and CSS background URLs. Keep the largest version (check `srcset`).
- Find social links in the site header/footer. Record every channel in the brief.
- **YouTube:** fetch the channel's `/videos` page and pull the video IDs out of its HTML (`"videoId":"…"`). Titles come from `https://www.youtube.com/oembed?url=https://youtu.be/<ID>&format=json`. The RSS feed (`/feeds/videos.xml?channel_id=<ID>`) is a fallback that isn't always available. Thumbnails: `https://i.ytimg.com/vi/<VIDEO_ID>/maxresdefault.jpg` (fallback `hqdefault.jpg`). Embed with `youtube-nocookie.com` and a click-to-load facade, not an autoplaying iframe.
- **Instagram / Facebook / TikTok** usually block automated fetching. Don't fight it; ask the user to paste 5–10 post links or screenshots, or use images already on the site.
- Download chosen images into the repo (`public/media/` or the framework's equivalent), compress them (WebP/AVIF, ≤ 300KB for full-width), and record each one's source URL in `DESIGN.md` → Media credits.
- **Rights:** the org's own media on the org's own site is fine. Anything from a third party (press photo, photographer credit, partner) gets flagged `[CHECK RIGHTS]` in the brief.

## Gallery
A real gallery uses real moments with **real alt text** describing what's happening ("Two runners crossing the finish line, one using a racing wheelchair"), not "image of runner". Mixed aspect ratios in a masonry/bento grid beat uniform squares. Keyboard-operable lightbox, or none.

## Generated media: which generator
Check what tools *this* session actually has. Don't assume.

| Available | Use |
|---|---|
| Higgsfield tools (`*Higgsfield*` / `higgsfield` MCP tools) | Preferred for video and images. |
| No Higgsfield, but an OpenAI API key in env (`OPENAI_API_KEY`) | OpenAI's current image model for stills. No video. |
| Neither | Skip generation. Say so in one line and use real media + design. |

### Spend rules (any paid generator)
1. Check the balance first (Higgsfield: `balance` tool).
2. Tell the user what you'll generate, how many, and the estimated credit cost, and **wait for a yes**.
3. Pass the agreed cap as `max_credits` (Higgsfield). Generate one, show it, then do the rest.
4. Record model, prompt, and cost in `DESIGN.md` → Media credits.

### What may be generated
- **Yes:** atmosphere and place: empty city streets at dawn, a road surface, a finish-line banner with no people in focus, weather, light, texture, abstract motion loops.
- **Real photos of real people:** crop, upscale, extend background (outpaint), and background removal are fine. Don't animate them or change their bodies, faces, or equipment.
- **Never:** people who could be mistaken for the org's real members, beneficiaries, or staff; people with disabilities; children; anything presented as a real event, real result, or real testimonial. That misrepresents real people. Use the org's real media instead.

### Hero video spec
16:9 (plus 9:16 for mobile if budget allows), 5–8s, seamless or slow loop, no audio, ≤ 4MB, with a poster frame. Muted, looped, `playsinline`, a pause button, and no autoplay under reduced motion.
