Build a self-contained ~30 second animation as plain code only — no Remotion, HyperFrames, React, or other animation frameworks. Prefer a single HTML file with canvas (2D and/or WebGL) plus Web Audio, or a tiny vanilla JS + HTML pair. Everything must run from opening the file locally.

Style:
- Textured off-white paper / slightly sketchy, hand-coded look (subtle grain or imperfect strokes), not slick After Effects CGI
- One mascot: small orange rectangular character with stubby legs/arms and square eyes
- Seamless morphs between scenes (no hard cuts) timed to music

Storyboard (~30s):
1. Character drops onto a faint horizontal line, blinks, waves; concentric rings expand into a transition
2. Brief abstract cosmic flash → close-up blue branching neuron with glowing center (flash to B&W sketch briefly)
3. Dark scene: 3D-ish glass prism hit by white light → rainbow spectrum (Dark Side of the Moon energy)
4. Rainbow stretches into a colorful DNA double helix → dissolves into a spiral of glowing dots
5. Spiral becomes sunflower seed head; yellow petals bloom on warm pink/orange gradient
6. Sunflower scatters into a bird murmuration against purple–orange sunset; flock forms a dense disc
7. Disc becomes a glowing accretion disk around a black hole → collapses into a bright streak
8. Streak flies over a gray cratered moon toward a colorful cartoon Earth
9. Warp into a psychedelic fractal tunnel → snap back to off-white
10. Character returns, arms up, eyes closed as ^ ^ smile

Audio:
- Procedural / Web Audio soundtrack only (no external MP3 downloads)
- Aim for real-instrument-ish timbres (plucks, pads, soft percussion) — iterate until it feels musical, not bleeps
- Sync major scene morphs to beats or swells

Engineering:
- 1280×720 (or 16:9 responsive), 60fps target where feasible
- One timeline / clock driving both visuals and audio
- Easy to tweak scene timings in one place
- Add a short README: how to open, how to export (e.g. record the tab or use a simple capture note)

First implement a playable skeleton (character + one morph + basic music bed), then flesh scenes in order until the full loop matches the storyboard. Prefer math/procedural drawing over image assets.
