# FIVEFOLD

**One studio. Five doctrines. Every room disagrees with the last.**

A capability showcase built as five self-contained rooms, each arguing a different design philosophy — three in English, two in Hebrew (fully RTL). No frameworks, no build step, no libraries: every page is a single hand-written HTML file with inline CSS/JS. The only external dependency is Google Fonts.

| Room | File | Language | Doctrine |
|------|------|----------|----------|
| I — KINETIC | `kinetic.html` | EN | Motion is the message. ~2,750-particle typography with spring physics, pointer repulsion, and a timed morph sequence. |
| II — EVIDENCE | `evidence.html` | EN | The page is an instrument. Every chart measures this page and this reading session, live: letter frequency, scroll velocity, dwell time, your reading speed, the font's true rendered anatomy. |
| III — DOCTRINE | `manifesto.html` | EN | Ornament is debt. Ten design laws set as a neo-brutalist poster on an honest grid. |
| IV — כתב | `ivrit.html` | HE | Three thousand years of the Hebrew letter — parchment, ink, and right-to-left as a compositional axis. Self-drawing א, script-era timeline, nikud toggle. |
| V — מעבדה | `maabada.html` | HE | Play is a method. A night lab: Hebrew letters as physics bodies (hand-written Verlet engine), a pendulum wave, a live color mixer. |

`index.html` is the front door — five expanding panels; keys **1–5** jump straight into a room. Every room carries a shared nav pill to cycle through the others.

All pages respect `prefers-reduced-motion`, run without console errors, and hold their layout from 375px to 1440px+.
