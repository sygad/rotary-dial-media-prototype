# Open questions

Gaps the design does not answer. Do not fill these in independently — raise them.

**Q1 — Hardware.** The Figma page is named "Waveshare Device" and the screens are
360 x 360 round, but the exact board, display module and driver are not confirmed.

**Q2 — Input.** Does the panel have touch, or is the rotary encoder the only input? The
design assumes both swipe gestures and dial rotation. If there is no touch, every swipe
needs an encoder equivalent and the interaction model changes substantially.

**Q3 — Audio.** Source (local storage, Bluetooth, network), decoder and output stage are
all unspecified. The prototype fakes playback with a 20-second timer.

**Q4 — Unbuilt menu branches.** Search, Playlist, Artists and Radio appear in the menu
but have no designed screens. Only Albums exists.

**Q5 — EQ range.** The prototype uses -12 to +12. This was assumed, not specified. Real
range and step depend on the DSP.

**Q6 — Track end behaviour.** The prototype advances to the next track and keeps playing.
Not specified in the design. Album end behaviour (stop, repeat, next album) is also open.

**Q7 — Volume range and curve.** The prototype uses a linear 0-100. Not specified.

**Q8 — Title visibility during playback.** Figma frame 05 has no title band, so the track
name is hidden while playing except during the peek. Confirm this is intended on hardware,
where a glanceable display may want the title permanently visible.

**Q9 — Clock.** Shows a static 20:41. Time source (RTC, NTP, phone) is unspecified.
