# cool-baby-series — CLAUDE.md

AI kids-animation series for a private client: his ~10-month-old daughter ("הבוסית במשקפיים" / "Cool Baby") and their two Japanese Akita dogs. Operator: Noam (does not edit video; editing is done in code with Remotion by Claude).

## Start here
New session? Read `START-HERE-SESSION-PROMPT.md`, then `docs/PLAN.md`, `docs/RESEARCH.md`, `docs/DECISIONS.md`.

## Rules
1. **Child privacy first.** Real photos/videos/voice of the girl never go into git, public links, or posts. Keep them in `references/photos/` (gitignored). Use a nickname. No "real vs cartoon" comparison posts.
2. **The approved character sheet is the character.** After approval, generate only from the sheet, never re-describe from scratch or re-use the real photos.
3. **No third-party IP** (Mickey swim ring in the real photo → our own star-pattern ring).
4. **Higgsfield Unlimited = manual web use only.** Automation only through API/MCP/CLI (credits).
5. **Ask before** purchases, publishing, or sending anything to the client.
6. Prices and model capabilities change monthly — date every price you write, and mark unverified claims.
7. Record every plan change in `docs/DECISIONS.md`.

## Layout
- `docs/` plan (md + interactive html), research, decisions
- `prompts/` copy-paste prompts (DNA blocks, sheets, keyframes, video, script, music, narration)
- `episodes/<EP>/` shot list, later episode.json + assets
- `editing/` Remotion template spec
- `references/` notes about the client's reference images (the images themselves are local-only)
