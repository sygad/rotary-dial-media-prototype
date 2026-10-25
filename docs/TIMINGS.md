# Timings

Every duration in the prototype, in one place.

| Behaviour | Value |
|---|---|
| Title fade in | 250ms |
| Title fade out | 500ms |
| Title crossfade on track change | 250ms |
| Title hold before fading | max(2000ms, one full scroll cycle) |
| Text scroll cycle | 2600ms + 55ms per hidden pixel |
| Text scroll easing | ease-in-out |
| Album / track art slide | 280ms, cubic-bezier(.2, .9, .3, 1) |
| Menu snap on release | 220ms, cubic-bezier(.2, .85, .35, 1) |
| Menu magnetic pull (during drag) | 0.34 x (1 - t^2), t = distance from nearest slot / 30px |
| Transport bar fade | 220ms |
| Volume label hold | 1100ms |
| Arc value change | 100ms linear |
| Track length (prototype) | 10s |

## Gesture thresholds

| Threshold | Value |
|---|---|
| Movement before a drag counts as a drag | 5px |
| Horizontal travel to change album or track | 64px |
| Vertical travel to trigger up/down | 40px (60px from album browse) |
| Rotary step | 8 degrees |
| Volume per step | 2 |
| EQ per step | 1 |

## Rotate versus swipe

The dial engages only when the touch **begins near the rim** (beyond 68% of the radius)
**and** travels around the circumference rather than across it — tangential movement
must exceed radial movement by 1.2x.

This matters: an earlier version treated any touch starting near the rim as a rotation,
which broke the upward swipe to EQ, because an upward drag naturally starts low on a
circular screen. On hardware with a physical encoder this disambiguation is unnecessary —
the encoder and the touch panel are separate inputs.
