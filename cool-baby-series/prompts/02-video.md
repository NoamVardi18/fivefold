# Video prompts (Seedance 2.0 / Kling 3.0, image-to-video)

Upload the approved keyframe as start frame + the character sheets as references. 4–6 s. **Sound OFF** (all audio is built in the edit). 16:9, 1080p (720p for tests).

```
Animate the start frame. Duration: 5 seconds. Horizontal 16:9.

ACTION (one or two clear beats only):
[e.g. [BABY] slowly slides her bear sunglasses down her nose with one finger and looks straight into the camera. After a beat, [DOG1] tilts his head and his tongue flops out.]

CAMERA: [static locked camera / slow push-in / gentle lateral dolly / low tracking shot following the action]
TIMING: animated-feature cartoon timing – clear anticipation, soft weight, small overshoot, then a short hold at the end (we need handles for editing).

KEEP: the exact character designs, outfit, collars, colors and background from the start frame and the attached references.
AVOID: morphing, face changes, extra limbs or fingers, new characters, text, logos, flicker, fast shaky camera.
```

## Rules
- 1–2 beats per shot. Ask for a **hold at the start and end** (handles) — the editor trims.
- Dogs: subtle motion is safe (head tilt, tongue, tail, ears). Running = hard shot → try both Seedance and Kling.
- The sunglasses transition is done in the edit (crossfade YARD → YARD_JUNGLE from the same angle + a transition graphic), not by the model.
- 2–4 versions per shot; pick against the sheet; log the winning prompt in `prompts/log.md`.
- Stop rule: 4 failures → simplify the action, switch model, or split the shot.
- Continuity: last frame of shot N (export a still) → start frame of shot N+1 when the action continues.
