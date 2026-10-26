# Design tokens

Every value here was exported from the Figma file, not measured by eye.
Coordinates are top-left origin in the 360 × 360 design space.

## Colours

| Token | Hex | Used for |
|---|---|---|
| Menu highlight | `#3c8194` | Menu selection pill |
| Treble | `#32ACA4` | Treble clef, treble arc |
| Bass | `#9C0D90` | Bass clef, bass arc |
| Subs | `#AB1049` | Speaker icon, subs arc |
| Volume arc | `#ECD613` | Volume arc |
| Progress fill | `#FF00FB` | Track progress played |
| Progress track | `#D9D9D9` | Track progress remaining |
| Back button | `#5B5B5B` @ 80% | EQ focus back button |
| Trident | `#919191` | EQ divider lines |
| Panel black | `#000000` | Backgrounds, bands, rim |

## Type

Family **Inter** throughout.

| Element | Size | Weight |
|---|---|---|
| Clock | 96px | 200 (Extra Light) |
| Menu items | 36px | 300 (Light), 60px line height |
| Track title | 24px | 400 (Regular) |
| Album title | 24px | 400 (Regular) |

Menu unselected items render at `#808080`, selected at `#FFFFFF`.

## Ring and arcs

| Property | Value |
|---|---|
| Black ring | radius 168 → 180 (12px), drawn out to 184 so the clip edge is black |
| Arc | radius 170 → 178 (8px), centred in the ring |
| Arc start | 6 o'clock, clockwise |
| Arc caps | round |
| Album art clip | radius 174, so art ends under the solid black ring |

Album art must never reach the panel edge. If art and ring both run to the edge, each is
antialiased there and a thin fringe of art shows through the rim. Clipping the art at
r=174, under the opaque ring, leaves only black at the edge.

The 2px of black either side of the arc is deliberate — it prevents two edges
antialiasing onto the same pixel, which produced a visible fringe.

## Screen 02 — Menu

| Element | x | y | w | h |
|---|---|---|---|---|
| Highlight pill | 54 | 151 | 251 | 58 |
| Text block | 121 | 29 | 125 | 300 |

Item pitch 60px. Item 3 (Albums) centres on the pill at y=180.

## Screen 04 — Now Playing (paused)

| Element | x | y | w | h |
|---|---|---|---|---|
| Play disc | 126 | 107.3 | 120 | 120 (radius 60, black 80%) |
| Play triangle | 178 | 142 | 30 | 46.9 (white) |
| Title band (Figma) | −2 | 211 | 364 | 52 (black 80%) |
| Title text (Figma) | 40 | 220 | 315 | 29 |

**Deviation:** the title band was moved to **y = 267.7** at the owner's request, so it sits
equidistant between the bottom of the play disc (y=227.3) and the bottom of the screen
(y=360) — 40.35px clear above and below. The title is also **centred** rather than
left-aligned. Both are intentional changes from the Figma frame.

Because the circle narrows at that height, usable text width is **220px** starting at
**x = 70**.

## Screen 05 — Now Playing (transport)

| Element | x | y | w | h |
|---|---|---|---|---|
| Transport band | 33 | 138 | 294 | 85 (radius 42.5, black 80%) |
| Previous | 68.9 | 159.6 | 39.1 | 33.8 |
| Pause bars | 160.4 | 151 | 39.1 | 50.8 (two 13px bars) |
| Next | 252 | 159.6 | 39.1 | 33.8 |
| Progress track | 69 | 213.8 | 222.1 | 3.4 |

This frame has **no title band** — hence the peek behaviour described in `SPEC.md`.

## Screen 06 — EQ overview

Background: album art with a **75% black** overlay.

| Element | x | y | w | h |
|---|---|---|---|---|
| Trident group | 71 | 48 | 219 | 196.9 |
| Treble clef | 77.5 | 80 | 50 | 100 |
| Bass clef | 225 | 92 | 72 | 77 |
| Subs speaker | 136 | 233.3 | 75 | 66.7 |

Trident lines: vertical from (178.7, 48) to (178.7, 181.9); diagonals from the junction
to (71, 244.8) and (290, 242.5). Stroke 2.65.

## Screens 13–15 — EQ focus (Option C)

| Parameter | Icon x | Icon y | Icon w | Icon h |
|---|---|---|---|---|
| Treble | 154 | 64 | 50 | 100 |
| Bass | 152 | 80 | 72 | 77 |
| Subs | 142 | 85 | 75 | 66.7 |

Back button: **184 × 85 at (88, 206)**, radius 42.5, `#5B5B5B` at 80%, white arrow
stroke 6.875.

## Icons

The clef, speaker and back-arrow vectors are embedded in `prototype/index.html` as SVG
paths exported directly from Figma. Reuse those paths — do not redraw them. For LVGL,
convert the same paths rather than substituting a font glyph or an approximation.
