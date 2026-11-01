# /goclaude

A Claude skill for planning and designing a website that **doesn't look AI-made**.

Give it the current site's URL and 1 to 3 brand websites whose look and feel you like. It will:

- **Scan** the current site, its social channels and your inspiration brands. It uses real fetches, not memory.
- **Confirm** what the organization is, then lay out its story using the **StoryBrand** framework: audiences, problem, plan and one clear call to action.
- **Declutter the navigation** to 5 items or fewer, with a mapping table showing where every old link went so nothing is lost.
- **Define what goes above the fold**, so a visitor knows in 5 seconds what the organization does.
- **Write `DESIGN.md`**, a design plan where every color, font and layout choice names its source.
- **Build a preview first:** header, hero, animated stats and footer. Parallax and count-up numbers are on by default, and both respect reduced-motion settings.
- **Use real photos and video** from the organization. It generates atmosphere with AI only when your session has a generator (Higgsfield preferred, then an OpenAI image model), and only after you approve the cost. It never generates fake people.
- **Check accessibility** against WCAG 2.2 AA: keyboard, contrast, screen readers and reduced motion.

## Install

**Claude Code (plugin):**
```
/plugin marketplace add joechura/goclaude
/plugin install goclaude@goclaude
```

**Any repo (copy the folder):** put `skills/goclaude/` in `.claude/skills/goclaude/` in your project, or in `~/.claude/skills/goclaude/` to use it everywhere.

**claude.ai:** zip `skills/goclaude/` and upload it under Settings → Capabilities → Skills.

## Use
```
/goclaude
```
It asks for the current site's URL and your inspiration brands, then stops for your OK three times:

1. Intake: your URL and inspiration brands.
2. Strategy: what the organization is, its story, the new navigation and what goes above the fold.
3. Preview: a link to the first build to approve or change.

Made by Joe Chura.
