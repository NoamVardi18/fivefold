# Remotion editing template: spec

Build this in a separate folder/repo (e.g. `cool-baby-editor/`). Nothing is built yet, by design. The local session builds it and verifies it.

## Goals
- Noam doesn't edit video. He drops approved clips and audio into a folder, and Claude assembles, mixes and renders a professional episode from a JSON file.
- Every episode is reproducible, and episode 2 reuses everything from episode 1.

## Output presets
| Composition | Size | fps | Use |
|---|---|---|---|
| `Episode` | 1920×1080 (4K `Episode4K` if the source allows) | 24 | Main deliverable |
| `EpisodePreview` | 960×540 | 24 | Fast proxies for reviews |
| `Promo` | 1080×1920 | 24 | Optional vertical cut-down, reusing shots with a per-shot focal point for reframing |

Final encode: H.264 High, CRF ~16–18, AAC 320k (plus a ProRes master option). Preview: CRF 28.

## Episode schema (`episodes/EP01/episode.json`), a draft to refine
```json
{
  "id": "EP01",
  "title": { "he": "הכובע שעף", "en": "The Hat That Flew Away" },
  "fps": 24,
  "grade": { "preset": "warm-soft", "grain": 0.07 },
  "coldOpenEndsAt": 20,
  "shots": [
    { "id": "SH01", "src": "shots/SH01.mp4", "in": 0.4, "dur": 3.0,
      "transition": { "type": "cut" }, "desc": "ECU sunglasses slide down",
      "focal": [0.5, 0.45] }
  ],
  "narration": [ { "src": "audio/narr_01.wav", "at": 1.0, "text": "תכירו את ..." } ],
  "music": [ { "src": "audio/theme.mp3", "at": 20, "gainDb": -6, "duckDb": -10 } ],
  "sfx": [ { "src": "sfx/whoosh.wav", "at": 7.2, "gainDb": -3 } ],
  "captions": { "he": "auto-from-narration", "en": "subs/EP01.en.srt" },
  "titleCard": { "at": 20, "dur": 8 },
  "endCard": { "dur": 10, "credits": ["Created by ...", "Narration ..."] }
}
```
- Timeline positions are **computed** from shot durations. Audio `at` is in seconds on the final timeline.
- Validation (zod or similar): missing files, negative/overlapping durations, and the total duration against the shot list, with human-readable errors.

## Features
1. **Missing-asset placeholders:** if `src` is missing, render a clean card showing the shot id, description and a timer. Lets the animatic render with still keyframes (`.png` becomes a gentle Ken Burns move) before clips exist.
2. **Transitions:** cut (default), crossfade, dip-to-white, and the signature **"sunglasses-on" transition** (two lens shapes close in and open onto the imaginary world with a shimmer). Also "sunglasses-off" as the reverse.
3. **Audio:** narration, music and SFX layers. Automatic ducking of music under narration (smooth 150ms ramps). Per-clip gain. Fade in/out.
4. **Captions:** Hebrew, RTL-correct, a rounded Hebrew font (e.g. Rubik, Varela Round or Heebo, bundled locally), 1–2 lines, safe area, outline or soft shadow. Word timing from local Whisper (Hebrew fine-tune) or aligned from the script. English SRT burned in or exported as a sidecar.
5. **Look:** one color-grade preset for the whole series (CSS filters or a LUT via WebGL), subtle animated film grain, optional vignette.
6. **Title sequence** (about 8s, logo + theme song) and **end card** with credits. Can be built in HyperFrames and imported as a clip if that looks better.
7. **CLI:** `npm run preview -- EP01`, `npm run render -- EP01 [--final|--promo]`, `npm run qc -- out/EP01.mp4`.
8. **QC script (ffmpeg):**
   - loudness: integrated −14 LUFS ±1, true peak ≤ −1 dBTP
   - `blackdetect` and `freezedetect`
   - resolution, fps, duration
   - a report written to `out/EP01.qc.md`
9. **Frame check:** after every render, extract frames at fixed points and check them visually before sending anything to Noam.

## Done when
- A demo EP01 renders from placeholders plus sample audio, with correct Hebrew captions, ducking, grain, title and end cards.
- QC passes.
- The README explains to Noam, in Hebrew, how to add a clip version and re-render.
