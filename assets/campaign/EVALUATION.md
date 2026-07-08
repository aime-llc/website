# Campaign asset evaluation — 2026-07 ads

Every candidate graded against the same rubric:

1. **3-second test** — would a non-technical person get it at a glance?
2. **On-brand** — dark, minimal, no clutter, legible at thumbnail size.
3. **Honest** — real product, real capability, nothing we can't demo.
4. **Technically sound** — sharp, no cut-off UI, no debug artifacts, no personal data visible.

Captured against the user's live local instance (`http://127.0.0.1:7900`, offline mode, qwen/llama via Ollama, Claude Code as the online provider). All chat prompts used were generic/non-personal by design (tip lists, packing lists) so nothing from the real memory/session history could leak into a response. The Graph screenshots and video have every SVG `<text>` label force-hidden before capture — the real graph is full of the owner's actual memories and file paths, so no label text is ever rendered in what got saved.

Mobile (390×844) shots are graded honestly even though they turned up a real product bug: the app is not responsive at that width yet. That's a legitimate finding, not a capture mistake — flagged in "anything you couldn't capture" in the final report. (This bug was fixed and the mobile shots were re-graded; see the "Re-shoot (2026-07-07)" section below.)

---

## Real product screenshots

| File | Verdict | Reasoning |
|---|---|---|
| `raw-chat-streaming.png` | **GOOD** | Re-shot 2026-07-07 against the new Markdown renderer. Mid-stream frame: tip 1 and 2 already render as real bold text, tip 3 is still arriving as raw `**` characters with the cursor blinking and the red stop button live, so the frame itself shows the raw-to-rendered transition. Toggle + mode badge in frame. Generic prompt, no personal data. **Used on site (video poster).** |
| `raw-chat-empty.png` | GOOD | Unchanged this pass. Clean empty state, on-brand, honest. Not exciting enough for the ad grid so left unused, but technically fine. |
| `raw-chat-complete.png` | **GOOD** (was BAD) | Re-shot 2026-07-07. Same reply, now fully settled: three numbered tips, each with a real bold lead-in, full sentence intact, nothing scrolled off-screen or cut mid-word. The old capture's problems (scrolled past the question, answer stopped mid-word) do not reproduce with the new renderer and a shorter prompt. Not referenced on any page, kept as a spare "final state" companion to the streaming shot. |
| `raw-toggle-closeup.png` | **GOOD** | Unchanged this pass. Tight crop on the actual Offline/Online segmented control, the product's signature UI element. Crisp, on-brand, unmistakable in 3 seconds. **Used on site.** |
| `raw-graph-nodes.png` | **GOOD** | Unchanged this pass. All text labels stripped before capture (privacy) — shows the colored node/edge shape of the memory map without exposing any of the owner's real memory or session content. Still clearly reads as "an interactive map of dots." **Used on site.** |
| `raw-settings-installer.png` | **GOOD** | Unchanged this pass. Shows the real model installer (Claude Code / Codex / Gemini rows, Ollama model picker, an "Install" button with model size). No personal data. **Used on site.** |
| `raw-files-strip.png` | **GOOD** | Re-shot 2026-07-07, online mode. Now shows the full upgraded reply: a rendered Markdown table (Item / Quantity / Notes for a synthetic `grocery-list-lunch.csv`), the new in-chat clickable file link with download icon, the files strip below, and the "Saved grocery-list-lunch.csv to your Downloads folder" toast fired by clicking that link. One frame now proves three features at once. Synthetic grocery-list content only, no personal data. **Used on site (video poster).** |
| `raw-mobile-chat.png` | **GOOD** (was BAD) | Re-shot 2026-07-07 at 390×844. The responsive fix landed: hamburger icon at top-left, Offline/Online toggle fully visible and uncramped, wordmark not shown in the collapsed header (by design, not clipped), composer placeholder renders on one line. Reply shows real bold Markdown ("**Set clear**") with no overlap or wrap issues. None of the three original bugs reproduce. |
| `raw-mobile-graph.png` | **GOOD** (was BAD) | Re-shot 2026-07-07 at 390×844. The desktop nav rail is gone: hamburger + toggle at top, then the Sessions/Memories/Skills pills, search box, and Tidy button all fit on one line without crowding, then the full dot graph has the frame instead of a squeezed corner. Labels were hidden via a CSS `svg text { display: none !important }` rule (stronger than the old JS-interval approach) and verified with a programmatic check for leaked `<text>` content (0 leaked nodes, including after a simulated drag interaction). |

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
| `v1-offline-streaming.mp4` | 20.8s | **GOOD** | Re-shot 2026-07-07 against the Markdown renderer. Dark mode from the first frame (the pre-toggle light-mode instant was trimmed off), real typing (`pressSequentially`, not pasted), the same "three quick tips" prompt as the original. Frame-by-frame review (2fps contact sheet, full clip) shows: idle → typing → "Thinking…" with red stop button → tip 1–2 render as real bold text while tip 3 is still mid-flight as raw `**` characters with a blinking cursor → settles into the fully rendered three-item bold list, held for the last ~4s. No personal data, no cut text. H.264 yuv420p 1120×630, 189KB. **Used on site (unchanged filename, poster `raw-chat-streaming.png`).** |
| `v2-online-file-create.mp4` | 19.2s | **GOOD** | Re-shot 2026-07-07. Dark mode from frame 1 (light-mode instant before the app's own theme toggle finished was trimmed). Flips Offline→Online on camera, types "Make a CSV of a 3-item grocery list for lunch…" for real, Claude Code streams the reply with a rendered Markdown table plus the new in-chat file link, then the clip clicks that link on camera and holds on the "Saved grocery-list-lunch.csv to your Downloads folder" toast. Mode was restored to offline via the UI immediately after the recording context closed (verified with a follow-up screenshot). Sped 1.35x from the raw 28s take to land in the 10–25s target, same technique as the original capture. Synthetic grocery-list content only. H.264 yuv420p 1120×630, 112KB. **Used on site (unchanged filename, poster `raw-files-strip.png`).** |
| `v3-graph-drag.mp4` | n/a | **BAD (removed)** | Unchanged this pass, stays revoked per the 2026-07-07 correction below. Not re-shot; graph video is out of scope for this refresh. |
| `v4-new-chat.mp4` | 13.4s | **GOOD** (new) | New clip, mobile viewport (390×844), dark mode. Fresh empty state (hamburger + toggle both fully visible, no clipping) → types and sends a generic productivity-tip prompt → reply renders → holds on the filled session → taps the "New chat" button on camera → back to the empty "What can I help with?" state, held to the end. Demonstrates the New Chat button and the fixed mobile layout in one shot. No personal data. H.264 yuv420p 390×844, 55KB. Not embedded on either page (kept the proof section lean, same call as `v3-graph-drag.mp4` previously) but ready for ad use. |

None of the raw intermediate `.webm` captures were kept — only the final H.264 MP4s.

---

## Summary

- **27 GOOD** / **1 BAD** out of 29 evaluated candidates (post re-shoot; `v4-new-chat.mp4` adds one new candidate).
- The `v3-graph-drag.mp4` BAD/removed verdict from the 2026-07-07 correction stands untouched.
- Site update (original pass) used 5 real screenshots + 2 videos + 1 poster (as share image), all GOOD.


## Correction (2026-07-07, PM)

- `v3-graph-drag.mp4` is revoked to **BAD** and removed: frame inspection at ~3s shows real unredacted memory/session labels and a real filesystem path. The 150ms label re-hide did not hold during the drag. Never grade a graph video GOOD without frame-by-frame inspection.

## Re-shoot (2026-07-07): Markdown rendering + mobile responsive fix

The product shipped several UI upgrades since the original capture: assistant replies now render real Markdown (headings, bold, lists, tables), filenames in replies are clickable download links with a "Saved to your Downloads folder" toast, a New Chat button lives in the chat header, and the app is responsive at phone widths with a hamburger drawer. The screenshots and clips above were showing the old raw-text, desktop-only era, so they were re-captured against the live app at `http://127.0.0.1:7900`.

**What changed:**
- `raw-chat-streaming.png`, `raw-chat-complete.png`: new prompt, same spirit as the original ("three quick tips"), now rendering as real bold Markdown instead of literal `**` characters.
- `raw-files-strip.png`: now shows the rendered table, the in-chat file link, and the download toast, not just the files strip.
- `raw-mobile-chat.png`, `raw-mobile-graph.png`: re-graded BAD to GOOD now that the responsive layout fix has landed. The three specific bugs noted in the original BAD verdicts do not reproduce.
- `v1-offline-streaming.mp4`, `v2-online-file-create.mp4`: re-shot end to end (unchanged filenames so page references keep working), now showing the raw-to-rendered Markdown transition and the file-link/toast interaction respectively.
- `v4-new-chat.mp4`: new, optional, demonstrates the New Chat button on a mobile viewport.

**Method notes (carried forward from the correction above):**
- Every capture used a session started from the "New chat" button, never an existing session from the app's history.
- All chat prompts were generic, non-personal demo content (productivity tips, a synthetic grocery list) so nothing from real memory or session history could appear in a reply.
- Graph label hiding was upgraded from a JS re-hide interval to a persistent CSS rule (`svg text { display: none !important }`), then verified with a programmatic scan for leaked `<text>` content (0 leaked nodes), including after a simulated drag, before the screenshot was graded.
- Every new video was inspected frame by frame (contact sheets at 2fps covering the full clip) before being graded GOOD. No frame contains real session data, personal data, or debug artifacts.
- Online mode was only enabled for the two captures that needed it and was restored to offline immediately after, verified with a follow-up screenshot each time.
