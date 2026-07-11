# KNOWLEDGE — fivefold (one-truth map: what/why/where)
*Created 2026-07-11 (FELT5-BUILDER Lane S knowledge-coverage audit — folder had zero KNOWLEDGE.md; distilled from README.md).*

## What this is
A capability-showcase site: five self-contained "rooms," each a single hand-written HTML file arguing a different design philosophy (three English, two Hebrew/RTL). No framework, no build step, no JS/CSS libraries — the only external dependency is Google Fonts. `index.html` is the front door (five expanding panels, keys 1–5 jump to a room).

## Why it's shaped this way
Deliberately zero-tooling: every room is a standalone artifact that proves a design doctrine can be executed in hand-written HTML/CSS/JS alone — no React, no bundler, nothing hiding the craft. Doctrine intentionally contradicts room-to-room ("every room disagrees with the last") — it's a range demonstration, not a single coherent product.

## Where things are
- `index.html` — front door / room selector.
- `kinetic.html` (EN, "Motion is the message") — particle typography, spring physics, pointer repulsion.
- `evidence.html` (EN, "The page is an instrument") — live self-measuring charts (letter frequency, scroll velocity, dwell time, reading speed).
- `manifesto.html` (EN, "Ornament is debt") — neo-brutalist ten-laws poster.
- `ivrit.html` (HE, RTL, "כתב") — Hebrew letter history, self-drawing א, script-era timeline, nikud toggle.
- `maabada.html` (HE, RTL, "מעבדה") — Hebrew letters as Verlet-physics bodies, pendulum wave, live color mixer.
- `.vercel/` — deployed on Vercel; git repo (own `.git`, 10 commits as of audit).
- All pages respect `prefers-reduced-motion`, hold layout 375px–1440px+, no console errors.

## What's NOT here
No MISSIONS.md/NOW.md — this is a finished showcase, not an in-progress project with open work; README.md's room table is both the map and the status.
