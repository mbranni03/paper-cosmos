# Paper Cosmos

A ~30 second hand-drawn-looking animation with a procedural soundtrack, in one file: `index.html` (canvas 2D, one WebGL shader, Web Audio). No libraries, no image or audio assets, no network.

The original brief is in `PROMPT.md`.

## Open

Double-click `index.html` in a current Chrome, Edge, Firefox or Safari and press the orange play button. Browsers only allow sound after a click. It loops by default.

| Key | Action |
|---|---|
| Space / click | play / pause |
| Left / Right | seek one beat (hold Shift for one bar) |
| 1-9, 0 | jump to scene 1-10 |
| L | loop on/off (off = ends on the final pose) |
| R | record one pass to a video file (see Export) |

Debug: `index.html?t=12.5` opens paused on that second.

## Tweak the timing

Everything is timed from the `SCENES` table at the top of the script: beats per scene, plus the chord each scene plays over. `BPM` sits right above it. Visuals and music are both laid out from that table, and each scene's exit is keyed to its own end, so lengthening or shortening a scene keeps every morph landing on the next scene's downbeat.

Each scene is one function in `DRAW` (its picture for a given beat) and one in `MUSIC` (its notes, booked relative to the scene's first beat).

## Export

**Built in (best quality):** press `R`. The piece restarts, records one pass of the canvas plus the soundtrack with `MediaRecorder`, and downloads `paper-cosmos.webm` (Safari saves `.mp4`) at 1280x720, 60 fps, about 12 Mbit/s. Keep the tab visible while it records (about 30 s). With loop on, the clip loops seamlessly. Press `L` first if you want it to end on the final pose.

Browser-recorded WebM files have no duration header, and some editors dislike them. This ffmpeg command fixes that and makes a standard MP4:

```
ffmpeg -i paper-cosmos.webm -c:v libx264 -crf 16 -pix_fmt yuv420p -c:a aac -b:a 192k paper-cosmos.mp4
```

**Screen capture:** record the browser window with QuickTime (File > New Screen Recording) or OBS (Window Capture plus desktop audio). Make the window large first. The canvas renders at 1280x720 and scales to fit.

## What's inside

- **Paper look:** a generated paper texture (noise, fibres, vignette) is multiplied over every frame. A grain layer re-rolls 12 times a second, and outlines are re-jittered at 12 fps so they "boil" like hand-drawn frames. Fills are printed slightly off-register.
- **One cast of 864 dots** carries the middle of the film: DNA rungs, then a spiral whose divergence angle sweeps into the golden angle, then sunflower seeds, birds, an accretion disk and finally a comet.
- **Tunnel:** a log-polar kaleidoscopic IFS fragment shader, rendered at 640x360 and drawn into the 2D canvas.
- **Sound:** Karplus-Strong plucked strings (rendered once per note), detuned-saw string pads, additive glockenspiel and marimba, a felt kick, brush snare, noise risers and whooshes, a generated hall reverb and a dotted-eighth echo.
- **Sync:** the AudioContext clock is the master clock, and the visuals read it with output-latency compensation.
