# Claude Code — working instructions

## What this repo is

A **standalone reference** for the Rotary Dial Media interface. It shows intent: how the
product should look and behave. It isn't where the product gets built, and the real
project doesn't link to or depend on it.

`prototype/index.html` is the **reference implementation**. It's a browser prototype, but
it's the authority on screen flow, gestures, animation timing and exact layout
coordinates. `index.html` at the root is a playground that wraps a copy of the same
engine with an exploration panel. If the two disagree, the prototype wins.

The eventual product is an **ESP32 + LVGL** firmware build driving a 360 × 360 round
display with a rotary encoder. That build happens in its own repo.

## Hard rules

1. **The prototype and `docs/` are the specification.** If something isn't in them,
   it isn't specified. Ask rather than invent. This project has already lost time to
   invented details.
2. **Never guess a coordinate, colour, size or duration.** Every value is recorded in
   `docs/DESIGN-TOKENS.md` and `docs/TIMINGS.md`, taken from the Figma source. Use those
   numbers literally.
3. **The design space is 360 × 360.** All coordinates in the docs are in that space and
   map 1:1 to the physical display. Don't rescale or "adjust for" the panel.
4. **Where the design is silent, raise it.** Open questions are listed in
   `docs/OPEN-QUESTIONS.md`. Add to that file rather than filling a gap yourself.
5. **Keep the playground faithful.** Changes to `index.html` may add tooling around the
   engine. They must not change how the device behaves. Behaviour changes go into
   `prototype/index.html` first, then get mirrored.

## Verifying behaviour

Open `prototype/index.html` (the authority) or `index.html` (the playground) in a browser.
There's no build step.

How browser gestures map to hardware:

| Prototype | Hardware |
|---|---|
| Drag up / down / left / right | Touch swipe on panel |
| Drag the outer ring in a circle | Rotary encoder |
| Mouse wheel, or the playground's virtual knob | Rotary encoder |
| Tap | Touch tap |

## Repo layout

```
index.html                playground — prototype engine plus exploration panel
prototype/index.html      reference implementation — the behavioural authority
assets/art/               album art for the playground (see README)
docs/SPEC.md              screen-by-screen flow and interaction rules
docs/DESIGN-TOKENS.md     exact coordinates, colours, type, from Figma
docs/TIMINGS.md           every animation duration in one table
docs/FIGMA.md             source file and frame node IDs
docs/OPEN-QUESTIONS.md    gaps the design does not yet answer
```

## Before any firmware work (in the real project)

Confirm these with the project owner first:

- Exact board and display module (`docs/OPEN-QUESTIONS.md` Q1)
- Whether the panel has touch, or whether the encoder is the only input (Q2)
- Audio source and playback library (Q3)

## Source of truth for the design

Figma file `jAaJDrPIrLTzMMPcqeqG4U` ("Rotary Dial Media"), page **Prototype - Structured**.
Frame node IDs are in `docs/FIGMA.md`. If a value in this repo disagrees with Figma,
Figma wins. Re-export rather than adjusting by eye.
