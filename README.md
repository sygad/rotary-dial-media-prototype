# Rotary Dial Media — reference prototype

A circular media player interface for a 360 × 360 round display, driven by a rotary
encoder and touch gestures. The intended target is an ESP32 running LVGL.

**This repo is reference only.** It records what the finished product should look like
and how it should behave, so the real build can be checked against it. It is
deliberately standalone: the firmware build lives elsewhere and doesn't link to or
depend on this repo.

## Play with it

Open **`index.html`** in a browser. There's no build step and nothing to install.

```bash
open index.html
```

If your browser blocks local files, serve the folder instead:

```bash
python3 -m http.server 8000
```

Then go to <http://localhost:8000>.

### The playground (`index.html`)

The round screen in the middle is the prototype, unchanged. The side panel is there to
help you explore it.

| Panel | What it does |
|---|---|
| **Screen** | Jump straight to any of the six screens. Each one shows its Figma frame number. |
| **Rotary encoder** | A virtual knob that stands in for the physical encoder, which is a separate input from the touch panel. Drag it round, scroll on it, or press `[` / `]`. |
| **Touch gestures** | Swipe and tap buttons, plus the on-screen taps (EQ zones, back button). |
| **State** | Live readout of the screen, album, track, playback, volume and EQ. |
| **Overlays** | Draws every box from `docs/DESIGN-TOKENS.md` on the current screen, or shows the zone that decides dial versus swipe. Also offers 1× / 1.5× / 2× size and pointer coordinates in the 360 × 360 space. |
| **Event log** | Each input and what it caused, e.g. `Encoder · Dial +1 → Volume 62`. |

### Controls

| Input | Keyboard | Mouse / touch on the screen |
|---|---|---|
| Tap | `Space` / `Enter` | Click |
| Swipe | Arrow keys | Drag |
| Rotary encoder | `[` / `]` (or `-` / `=`) | Drag the outer ring in a circle, or use the scroll wheel |
| Tap an EQ zone | `1` treble · `2` bass · `3` subs | Click the icon |
| EQ back button | `Esc` | Click the button |

### The original prototype (`prototype/index.html`)

This is the file exactly as it came out of the design sessions: a single file with the
album art embedded. **It's the behavioural authority.** The playground copies its engine
and only adds things alongside it (the panel, the overlays, and loading the art from
`assets/art/`). If the two ever disagree, the prototype wins.

## The screens

```
Clock ─tap─▶ Menu ─tap─▶ Album browse ─tap─▶ Now Playing ─swipe up─▶ EQ overview ─tap zone─▶ EQ focus
               ◀─swipe down─┘     ◀─swipe down─┘      ◀──────── swipe down ─────────┘
```

| # | Screen | What you can do |
|---|---|---|
| 01 | Clock | Tap to wake |
| 02 | Menu | Drag the list behind a fixed highlight; tap to choose |
| 03 | Album browse | Swipe left / right between albums; tap to open |
| 04 / 05 | Now Playing | Tap to play or pause; swipe left / right to change track; the dial sets volume |
| 06 | EQ overview | Tap treble, bass or subs |
| 13–15 | EQ focus | The dial adjusts the chosen parameter; back returns to the overview |

The full rules are in [`docs/SPEC.md`](docs/SPEC.md).

## Documentation

| File | Contents |
|---|---|
| [`docs/SPEC.md`](docs/SPEC.md) | Screen-by-screen flow and interaction rules |
| [`docs/DESIGN-TOKENS.md`](docs/DESIGN-TOKENS.md) | Exact coordinates, colours and type from Figma |
| [`docs/TIMINGS.md`](docs/TIMINGS.md) | Every animation duration and gesture threshold |
| [`docs/FIGMA.md`](docs/FIGMA.md) | Source file, frame node IDs, how to re-export |
| [`docs/OPEN-QUESTIONS.md`](docs/OPEN-QUESTIONS.md) | Gaps the design doesn't answer yet |
| [`CLAUDE.md`](CLAUDE.md) | Ground rules for working from this reference |

## Layout

```
index.html              playground: the prototype plus an exploration panel
prototype/index.html    original prototype, self-contained (the authority)
assets/art/             album art used by the playground
docs/                   spec, design tokens, timings, Figma map, open questions
```

## Design source

Figma file `jAaJDrPIrLTzMMPcqeqG4U`, page "Prototype - Structured". Figma is the source of
truth for anything visual. Re-export values rather than adjusting them by eye.

## Album art

The five covers are real artwork. They're here to test the interface against real titles
of different lengths. **They're not licensed for distribution**, which is why this repo is
private. Replace them before anything here goes public.
