# STRATA — audio-reactive topographic wave generator

**Live: [pxl-pshr.github.io/strata](https://pxl-pshr.github.io/strata/)**

Hash-seeded topographic contour-line fields that move like water and react to sound.
A single self-contained WebGL2 page — no build step, no dependencies.

Every sheet is rolled from an 8-hex hash into a 29-parameter DNA (wave fan, fbm
terrain, domain warp, contour density, palette…) and is shareable as a `?h=` token,
including any slider tweaks — e.g.
[`?h=deadbeef~11:44_20:0.9`](https://pxl-pshr.github.io/strata/?h=deadbeef~11:44_20:0.9).

## Run locally

Any static server:

```sh
python3 -m http.server 8735
# open http://localhost:8735
```

## Features

- **Field**: a fan of directional wave fronts + fbm terrain + domain warp, rendered
  as anti-aliased contour lines with heavier index contours every Nth level, plus
  glow, grain, and vignette.
- **Audio-reactive**: input modes Off / Demo groove (synthetic 116 bpm — no mic or
  file needed) / Microphone / Audio file (looping playback). Bands are split into
  bass/mid/high with attack–release smoothing and a bass-onset beat detector.
  Mapping: bass→swell, mid→warp, level→flow speed, high→shimmer + hue shift,
  beat→contour ripple + zoom pulse. All mapping strengths are sliders; live meter.
- **Color modes**: mono (black & white), duotone, spectrum (hue along height),
  terrace (filled elevation bands); invert, hue/spread/saturation.
- **Auto drift**: eases the DNA toward a freshly rolled target sheet every ~10s with
  exponential smoothing — no abrupt changes. Discrete params that would pop are held;
  hue/angles wrap the short way. Toggling off freezes the state into a shareable token.
  Click the 🔒 next to any slider to pin that setting while everything else wanders.
- **Atlas**: deal 12 random sheets in a grid, click one to load it.
- Each hash gets a formation name, elevation, and sheet code (e.g. *Halcyon Scarp ·
  +6,763 m · sheet MU-25*), stamped on the PNG export.

## Controls

- Drag = pan, wheel = zoom, `⌂` = recenter
- `space` = new sheet, `t` = atlas, `esc` = close atlas
- `a` = auto drift, `f` = fullscreen (hides all overlays — VJ-ready)
- `↓` = download sheet PNG
