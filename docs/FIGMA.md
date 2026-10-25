# Figma source

File: `jAaJDrPIrLTzMMPcqeqG4U` — "Rotary Dial Media"
Page: **Prototype - Structured** (node `559:178`)

The original concept board is on the page "Waveshare Device" (node `540:122`). It is
loose artwork — unnamed ellipses, boolean subtracts and mask groups — and is **not**
suitable for export. The "Prototype - Structured" page was created by cloning each
screen into a named 360 x 360 frame; use it instead.

| Frame | Node ID |
|---|---|
| 01 Clock | `559:179` |
| 02 Menu | `559:182` |
| 03 Album Browse / Physical Graffiti | `559:188` |
| 03a Album Browse / Alt 1 | `559:195` |
| 03b Album Browse / Alt 2 | `559:199` |
| 04 Now Playing | `559:203` |
| 05 Now Playing / Transport | `559:222` |
| 06 EQ / Base | `559:245` |
| 07 EQ Opt A / Treble | `559:261` |
| 08 EQ Opt A / Bass | `559:276` |
| 09 EQ Opt A / Subs | `559:292` |
| 10 EQ Opt B / Treble | `559:307` |
| 11 EQ Opt B / Bass | `559:322` |
| 12 EQ Opt B / Subs | `559:337` |
| 13 EQ Opt C / Treble | `559:352` |
| 14 EQ Opt C / Bass | `559:364` |
| 15 EQ Opt C / Subs | `559:376` |

**Options A and B are not used.** The product uses **Option C** — one parameter shown at
a time with a large back button. A and B are retained for reference only.

## Re-exporting

Use the Figma MCP server. `exportAsync({format: "SVG_STRING"})` on a vector node returns
the exact path; `absoluteBoundingBox` gives coordinates relative to the frame origin.
Do not read values off a screenshot — that produced repeated errors during prototyping.
