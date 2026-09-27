# Opening prompt for a local Claude Code session

> **How to use:** move the `cool-baby-series/` folder to wherever you want on your machine (ideally as a separate git repo), open Claude Code inside it, and paste everything below the line as the first message.
> The prompt is in English so the agent follows it precisely. You can talk to it in Hebrew.

---

You are taking over an AI kids-animation production that was planned in a cloud session which had **no access to YouTube, Reddit, X, Medium, Substack, TikTok or ChatGPT links, and could not install tools**. Your job is to (1) ground the plan in reality with fresh research, (2) set up the production toolchain on THIS machine, (3) build and verify the Remotion editing template, and (4) improve the plan — you may change any decision if you have evidence, but log why.

## The project in 5 lines
- Client (a father) wants a **real animated series** — proper episodes, NOT reels — about his ~10-month-old daughter and their two Japanese Akita dogs, published on social platforms (YouTube as the home; Facebook/Instagram; TikTok only after a policy check).
- Working title: "הבוסית במשקפיים" / "Cool Baby". Hook mechanic: when she puts on her bear-ear sunglasses the ordinary world becomes an adventure.
- **Format: horizontal 16:9, 1920×1080 (4K master if the pipeline allows), 24fps, ~3–4 minute episodes** with a cold open, title sequence, 3 acts and end credits. Pilot + 1–2 episodes first. Vertical 9:16 cut-downs (30–60s) are optional promo material only.
- **Quality bar: professional.** Noam said explicitly: "this is serious work, it must work professionally, not just throw something out." That means: animatic before generation, every shot approved against the character sheets, real sound design and a mixed soundtrack, consistent color, clean Hebrew typography, and a QC pass before anything goes to the client.
- The operator (Noam) **does not know how to edit video** — editing is done in code with Remotion, driven by you. Assets are generated manually on Higgsfield (Nano Banana Pro for images, Seedance 2.0 / Kling 3.0 for video).
- The client chooses the pilot plot from 3 options (see `docs/PLAN.md`).

## Read first (in this order)
1. `CLAUDE.md` — rules for this folder
2. `docs/PLAN.md` — the full plan (the source of truth; `docs/plan.html` is the same plan as an interactive page with copy buttons, also published at https://claude.ai/artifact/CffN4icsfHCU75kxjQZ8kn)
3. `docs/RESEARCH.md` — findings, sources, and **what is unverified**
4. `docs/DECISIONS.md` — each decision, the reason, and how confident it is
5. `editing/REMOTION-SPEC.md` — what to build
6. `prompts/` and `episodes/EP01-hat/shotlist.md`

## Phase 0 — Ground yourself in the field (do this before building anything)
Goal: replace assumptions with what practitioners are actually doing *this month*.

1. **Run the `/last30days` skill** (if it is not installed, find and install it, or tell me and do the equivalent manually with web search limited to the last 30 days) on each of these topics:
   - `AI kids animation series Seedance Higgsfield consistent characters`
   - `Nano Banana Pro character sheet consistency cartoon`
   - `Kling 3.0 vs Seedance 2.0 animated animals dogs`
   - `Remotion Claude Code video editing workflow`
   - `HyperFrames HeyGen`
   - `YouTube inauthentic content policy AI animation kids`
   - `TikTok AI generated likeness minors policy`
   - `AI animated short film full episode workflow professional 2026`
   - `AI animated pet series viral` (what makes audiences come back)
   Also study how professional preschool episodes are structured (e.g. Bluey's ~7-min episodes: cold open, one small problem, escalation through imagination, warm resolution) and adapt the structure to 3–4 minutes.
   Summarize per topic: what changed, what people recommend, prices/new models, red flags.
2. **Watch the two reference videos the client sent** — you can reach YouTube from here:
   - https://youtu.be/NnvRMs_0UQ8 — "How to Build a Kids Animation Channel with AI (Full Workflow)" (likely Higgsfield-sponsored)
   - https://youtu.be/4LryAnzFLMw — "How to Create AI Animated Stories That Make Money on YouTube in 2026"
   Get transcripts (e.g. `yt-dlp --write-auto-subs --skip-download`, or download audio and transcribe with Whisper). Extract their exact character-consistency method, prompts, tool settings, and compare with `docs/PLAN.md`. Save to `docs/research/video-NnvRMs.md` and `docs/research/video-4LryAn.md`.
3. **Read the ChatGPT conversation the client shared**: https://chatgpt.com/share/6ab8c610-32d4-83eb-96cf-e86cfc908514 — tell me whether it matches what the client wants (the cloud session could not open it).
4. **Verify every item marked UNVERIFIED in `docs/RESEARCH.md`** by opening the original sources (Reddit, Medium, Substack, X were blocked in the cloud). Update the file with ✅/❌ and dates.
5. **Check live prices** on https://higgsfield.ai/pricing and the Unlimited page, ElevenLabs, Suno. Note which offers are promotional.
6. **Find useful skills / MCP servers**: official Remotion agent skills (https://www.remotion.dev/docs/ai/skills), HyperFrames skill, Higgsfield MCP/CLI (credits only — never automate the Unlimited web UI), ElevenLabs MCP. Install what is clearly useful; list the rest.

Write a short `docs/GROUNDING-REPORT.md`: what we learned, what it changes in the plan, and what I (Noam) should do differently.

## Phase 1 — Audit this machine and propose local upgrades
Check OS, CPU/GPU (NVIDIA? Apple Silicon?), RAM, free disk, Node, Python, ffmpeg, git, Homebrew/winget, existing apps (DaVinci Resolve, CapCut, Topaz, ComfyUI, Docker).
Then propose — with setup commands and cost/benefit — ideas that use a personal machine, for example:
- **Local Hebrew transcription for captions**: Whisper / faster-whisper with a Hebrew fine-tune (check ivrit.ai models on Hugging Face) → word-timed Hebrew captions from the dad's narration, fed straight into Remotion.
- **Local upscaling / frame interpolation** (Real-ESRGAN, RIFE, or Topaz if installed) instead of paying per-clip upscale credits.
- **Local image/video models via ComfyUI** (e.g. Flux Kontext for keyframe edits, Wan 2.x image-to-video) — only if the GPU can handle it; compare quality/time vs Higgsfield honestly.
- **Audio cleanup** of the dad's phone recordings (noise reduction, loudness normalize to −14 LUFS with ffmpeg).
- **A watch-folder workflow**: Noam drops `SH07_v2.mp4` into a folder → a script updates the episode JSON and re-renders a preview.
- **A simple asset/approval tracker** (a local HTML page or markdown table) showing, per shot: keyframe approved? clip approved? which version?
- **Backups**: which folders must be backed up; the child's real photos stay local, never in git.
Ask me before installing anything large (>1 GB) or paid.

## Phase 2 — Build the Remotion template
Create it in a **separate folder/repo** (e.g. `../cool-baby-editor/`) as specified in `editing/REMOTION-SPEC.md`. Use the official Remotion skill if available.
Definition of done:
- `npm run render -- EP01` renders a 1920×1080 24fps MP4 (plus an optional 1080×1920 promo composition that reuses the same shots with reframing) from `episodes/EP01/episode.json`.
- Production-grade structure: typed episode schema with validation (clear error if a shot is missing or durations don't add up), preview vs final render presets (fast low-res proxy / final high-bitrate ProRes or high-CRF H.264 + AAC 320k), reproducible renders, a README explaining how Noam swaps in a new clip version.
- A QC script: loudness (target −14 LUFS integrated for YouTube, true peak ≤ −1 dBTP), black frames, frozen frames, resolution/fps, duration vs. shot list.
- It works with **missing assets** (placeholder cards with the shot description) so we can render the animatic before any clip exists.
- Hebrew captions render RTL correctly with a rounded Hebrew font; music ducks under narration; grain + one color grade; title card with the sunglasses animation; end card.
- You verified the output by extracting frames (e.g. at 1s, 5s, middle, end) and looking at them, and by checking audio levels. Send me the demo MP4 and the frames.

## Phase 3 — Improve the plan
Challenge the plan with what you learned. You may change: tool choices, pricing, episode length, style recommendation, shot list, prompts, schedule, the editing approach. For every change: update `docs/PLAN.md` (and `docs/plan.html` if simple), and add an entry to `docs/DECISIONS.md` (old → new, evidence link, date). Then add a section "More ideas" with concrete ideas for making the series better or cheaper (formats, recurring gags, seasonal episodes, behind-the-scenes content that does NOT show the real child, merch, brand collabs, English version).

## Guardrails (do not break these)
- **The child's privacy**: real photos of the girl never go into git or any public place; keep them in `references/photos/` (gitignored). Use a nickname in all content. No "real photo vs cartoon" posts anywhere (TikTok bans AI likeness of real minors). After the character sheet is approved, remind Noam to delete the real photos from Higgsfield (their terms allow training on uploaded content; deleted content is excluded).
- **No Disney/other IP** (the real swim ring has Mickey on it — never reproduce).
- Never automate Higgsfield's Unlimited web UI (against their terms); automation only via their API/MCP/CLI with credits.
- Ask before any purchase, subscription, publishing, or sending anything to the client.
- Mark anything you did not verify as unverified. Don't present guesses as facts.

Start with Phase 0 and report to me after each phase in Hebrew, briefly.
