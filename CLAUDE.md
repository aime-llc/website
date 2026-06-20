# aime website — Claude Code guide

## What this project is
Static marketing site for aime (ai, me) — two self-contained HTML files, no build step, no framework. Deployed via GitHub Pages to `aime.fyi` (see `CNAME`).

```
index.html   Homepage — hero, what-it-is, cookbook (hardware-scan/model-select), ownership/privacy, how-it-works, final CTA
learn.html   Deeper dive — capabilities, audiences, cookbook technical deep-dive (#cookbook), privacy, teacher model, demo, FAQ
CNAME        GitHub Pages custom domain (aime.fyi)
```

Design system: dark (`#050507` bg), Inter-style sans, ocean-blue/violet/teal gradient accents, SpaceX-inspired (bold type, cinematic glow, hairline borders). CSS is embedded per-file (duplicated across `index.html`/`learn.html` intentionally — no shared stylesheet, keep it that way unless asked to refactor).

## Development rules
- No pinned/sticky scroll-jacking effects — tried once, felt broken, reverted. Use simple `.reveal` (IntersectionObserver fade-up) for scroll animations only.
- Keep both files single-file/self-contained (style + script inline). Don't introduce a build step or external JS/CSS dependencies without asking.
- Test with headless Chrome screenshots (`google-chrome --headless=new --screenshot=...`) since there's no dev server — just open the file or serve via `python3 -m http.server`.

## Skill routing

When the user's request matches an available skill, invoke it via the Skill tool. When in doubt, invoke the skill.

Key routing rules:
- Product ideas/brainstorming → invoke /office-hours
- Strategy/scope → invoke /plan-ceo-review
- Design system/plan review → invoke /design-consultation or /plan-design-review
- Visual polish → invoke /design-review
- QA/testing site behavior → invoke /qa or /qa-only
- Code review/diff check → invoke /review
- Ship/deploy/PR → invoke /ship or /land-and-deploy
- Save progress → invoke /context-save
- Resume context → invoke /context-restore
