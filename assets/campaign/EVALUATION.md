# Campaign asset evaluation — 2026-07 ads

Every candidate graded against the same rubric:

1. **3-second test** — would a non-technical person get it at a glance?
2. **On-brand** — dark, minimal, no clutter, legible at thumbnail size.
3. **Honest** — real product, real capability, nothing we can't demo.
4. **Technically sound** — sharp, no cut-off UI, no debug artifacts, no personal data visible.

Captured against the user's live local instance (`http://127.0.0.1:7900`, offline mode, qwen/llama via Ollama, Claude Code as the online provider). All chat prompts used were generic/non-personal by design (tip lists, packing lists) so nothing from the real memory/session history could leak into a response. The Graph screenshots and video have every SVG `<text>` label force-hidden before capture — the real graph is full of the owner's actual memories and file paths, so no label text is ever rendered in what got saved.

Mobile (390×844) shots are graded honestly even though they turned up a real product bug: the app is not responsive at that width yet. That's a legitimate finding, not a capture mistake — flagged in "anything you couldn't capture" in the final report.

---

## Real product screenshots

| File | Verdict | Reasoning |
|---|---|---|
| `raw-chat-streaming.png` | **GOOD** | Mid-stream answer, cursor visible, red stop button, toggle + mode badge in frame. Reads instantly as "AI answering you live." No personal data — generic prompt. **Used on site.** |
| `raw-chat-empty.png` | GOOD | Clean empty state, on-brand, honest. Not exciting enough for the ad grid so left unused, but technically fine. |
| `raw-chat-complete.png` | **BAD** | Scrolled so the user's question is off-screen, and the answer cuts off mid-word ("techniques▊") with a stalled cursor — reads as broken, not finished. Also a wall of text that doesn't scan at thumbnail size. |
| `raw-toggle-closeup.png` | **GOOD** | Tight crop on the actual Offline/Online segmented control, the product's signature UI element. Crisp, on-brand, unmistakable in 3 seconds. **Used on site.** |
| `raw-graph-nodes.png` | **GOOD** | All text labels stripped before capture (privacy) — shows the colored node/edge shape of the memory map without exposing any of the owner's real memory or session content. Still clearly reads as "an interactive map of dots." **Used on site.** |
| `raw-settings-installer.png` | **GOOD** | Shows the real model installer (Claude Code / Codex / Gemini rows, Ollama model picker, an "Install" button with model size). No personal data. Did not actually trigger a download (would pull multiple GB onto the owner's real machine for no reason). **Used on site.** |
| `raw-files-strip.png` | **GOOD** | Online mode, a real `breakfast-grocery-list.csv` created by Claude Code sitting in the files strip with a working download affordance. This is the single best proof of the "real files" claim. No personal data (grocery list is synthetic demo content). **Used on site.** |
| `raw-mobile-chat.png` | **BAD** | Real bug, honestly captured: at 390px the sidebar doesn't collapse, the wordmark clips to "ime", the dark-mode icon overlaps the Online pill, and the composer placeholder wraps ugly ("Messa / ge aime..."). Not shippable as an ad. |
| `raw-mobile-graph.png` | **BAD** | Same root cause — no responsive layout at phone width. Not broken/overlapping like the chat shot, but the desktop nav rail eats over a third of the frame, leaving the graph squeezed into a small corner. Doesn't read as "mobile app" in 3 seconds. |

## Poster ads (designed, self-contained HTML → screenshotted)

Eight copy concepts, each shot at 1600×900 (social/OG) and 1080×1080 (square). All built from the site's real design tokens (`#050507` bg, hairline borders, ocean/violet/teal gradient, Inter-stack), no stock photography, no fabricated stats, no fake testimonials.

| Concept | Verdict | Reasoning |
|---|---|---|
| `poster-01-one-switch` | **GOOD** | Headline mirrors the real toggle pixel-for-pixel. Instantly legible, honest, on-brand. Strongest single concept — **used as OG/share image.** |
| `poster-02-memory-yours` | **GOOD** | Abstract dot-and-edge graphic echoes the real Graph page without exposing any real data. Clear "your data, your machine" claim. |
| `poster-03-real-files` | **GOOD** | File-chip mockup matches the real files-strip component. Directly demonstrates the least-known, newest feature. |
| `poster-04-data-stays` | **GOOD** | Simple lock icon, no overreach — copy matches what's actually true (local storage, no forced account). |
| `poster-05-switch-vendors` | **GOOD** | Clearly shows the "vendors are plug-ins" idea with neutral pill shapes (no third-party logos used, avoiding trademark issues). |
| `poster-06-tidy` | **GOOD** | Directly mirrors the real Tidy button and merge behavior. Honest, specific, on-brand. |
| `poster-07-phone-pairing` | **GOOD** | Plainest visual of the set (two device outlines, no phone chrome) but still on-brand and honest about what's shippable today — LAN pairing, not a hosted sync service. |
| `poster-08-free-or-paid` | **GOOD** | Pure typographic poster, no illustration. Cleanest read at thumbnail size; good as a closer/CTA card. |

All 16 poster files (8 concepts × 2 sizes) pass the rubric. Only `poster-01` is used inline on the site (as the CTA share image / product-proof section accent); the rest are ad-campaign deliverables for use off-site (social, etc.), per the brief.

## Video

| File | Duration | Verdict | Reasoning |
|---|---|---|---|
| `v1-offline-streaming.mp4` | 16.9s | **GOOD** | Real typing (not pasted), real Ollama streaming response, dark mode, toggle visible throughout. Muted-safe (no audio track). H.264, 357KB. **Used on site.** |
| `v2-online-file-create.mp4` | 22.8s | **GOOD** | Flips Offline→Online on camera, asks for a 5-item camping CSV, Claude Code streams a response and the file lands in the files strip — then mode was restored to offline immediately after capture. Sped 1.5x from the raw 34s take to land in the 10–25s target without cutting any of the narrative. H.264, 135KB. **Used on site.** |
| `v3-graph-drag.mp4` | 12.4s | **GOOD** | Optional clip. Labels force-hidden for the entire recording (verified via a 150ms re-hide interval, since the graph simulation keeps re-rendering `<text>` nodes). Shows a real node drag. Slowed 1.8x from the raw 6.9s take so the drag reads clearly. Not used on site (kept the section lean per the "don't redesign wholesale" rule) but ready for ad use. |

None of the raw intermediate `.webm` captures were kept — only the final H.264 MP4s.

---

## Summary

- **25 GOOD** / **3 BAD** out of 28 evaluated candidates.
- BAD assets (`raw-chat-complete.png`, `raw-mobile-chat.png`, `raw-mobile-graph.png`) are kept in this folder for the record, per instructions, but are not referenced anywhere in `index.html`.
- Site update uses 5 real screenshots + 2 videos + 1 poster (as share image), all GOOD.
