# Interaction specification

Display: **360 × 360 round**. All coordinates below are in that space.

## Screen flow

```
Clock
  tap ──────────────▶ Menu
                        tap ─────────▶ Album browse
                        drag down ◀──── (from first item)
                                          tap ─────────▶ Now Playing
                                          drag down ◀───
                                                          drag up ────▶ EQ overview
                                                          drag down ◀───
                                                                         tap zone ──▶ EQ focus
                                                                         back ◀──────
                                                          drag down ◀───────────────── (from either EQ screen)
```

## 1. Clock

Black screen, time centred. Any tap wakes to Menu.

## 2. Menu

Five items: Search, Playlist, Albums, Artists, Radio.

- A teal highlight pill is **stationary** at the centre; the list scrolls behind it.
- The list **follows the finger** during the drag, with a gentle magnetic pull toward
  the nearest slot (see `TIMINGS.md`). The pull fades to zero at the midpoint between
  items so there is never a visible jump.
- The item inside the pill is white; all others are mid-grey. The colour changes live
  as items pass under the pill.
- Tap selects.

**Not yet designed:** only the Albums branch exists. Search, Playlist, Artists and Radio
have no screens — every item currently opens Album browse. See `OPEN-QUESTIONS.md` Q4.

## 3. Album browse

- One album per screen, art full-bleed.
- Drag left / right moves between albums, following the finger, snapping on release.
- Album title sits in a band near the bottom. If the title is too wide it scrolls
  (see "Text overflow" below).
- Tap opens Now Playing at track 1, paused.
- Drag down returns to Menu.

## 4. Now Playing

Two visual states, driven by playback:

**Paused** — play disc and triangle visible, title band visible.
**Playing** — transport bar visible (previous / pause / next plus progress bar);
play disc hidden; title band hidden except during a peek (below).

These correspond to Figma frames `04 Now Playing` and `05 Now Playing / Transport`.
There is no "pause disc" state.

Interactions:

- **Tap** toggles play / pause.
- **While playing, the transport bar splits into thirds.** The left third (previous
  icon) skips back 5 seconds, the middle (pause icon) pauses, and the right third
  (next icon) skips forward 5 seconds. Tapping anywhere else on screen still toggles
  play / pause. A skip shows **+5s** or **−5s** in the same label as volume. Skipping
  forward past the end moves to the next track; skipping back stops at the start.
- **Drag left / right** changes track. The album art slides a full screen width,
  following the finger, exactly as album browsing does.
- **Rotate the dial** adjusts volume, shown on the arc plus a temporary label.
- **Drag up** opens EQ overview. **Drag down** returns to Album browse.

Playback (prototype values): each track runs **20 seconds**, the progress bar animates
from zero, and resets on every track change. At the end it advances to the next track
and continues.

**Title peek:** while playing, any track change — swiped or automatic — fades the title
band in, holds, then fades it out. If the title scrolls, the hold lasts one complete
scroll pass, up to a maximum of 6 seconds.

## 5. EQ overview

- Album art, darkened. A **trident divider** splits the circle into three zones:
  treble (upper left), bass (upper right), subs (lower centre).
- The volume arc from Now Playing is **preserved** and still shown.
- Tap a zone to focus that parameter. Drag down returns to Now Playing.

## 6. EQ focus

Per Figma frames `13`–`15` (Option C):

- The **selected parameter's icon only**, centred in the upper area.
- A large back button below it.
- The arc shows the parameter's level in that parameter's colour.
- No trident, no numeric readout, no other icons.

Interactions: rotate the dial to adjust; back button returns to EQ overview;
drag down exits to Now Playing.

## Text overflow

Applies to track titles and album titles alike.

- Text is measured against the usable width. If it **fits**, it is centred and still —
  no animation.
- If it **does not fit**, it left-aligns at the start, holds briefly truncated, slides
  left by exactly the hidden amount, holds so the end can be read, returns, and repeats.
  It never scrolls further than the overflow.
- Scroll duration scales with the amount hidden.

## Arcs

- All arcs start at the **6 o'clock position** and sweep **clockwise**.
- Rounded caps.
- An 8px arc sits centred inside a 12px black ring.
- Volume: 0–100. EQ parameters: −12 to +12 (prototype value, see `OPEN-QUESTIONS.md` Q5).
