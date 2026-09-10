# ATEM SuperSource Animation Generator

A free, browser-based tool for creating smooth SuperSource box animations on Blackmagic Design ATEM switchers — no paid apps, no installations, no account required.

> Built by a live church video operator who spent years trying to animate the SuperSource and finally cracked it.

**[▶ Open the app](https://yourusername.github.io/atem-supersource-generator)**

---

## What it does

The ATEM SuperSource doesn't have a built-in animation timeline. This tool generates the XML macro file that makes it move — with proper easing curves, frame-accurate timing, and all four boxes supported.

You set the **From** position and **To** position for each SuperSource box, choose your easing and duration, and download a ready-to-import XML macro file. Import it into ATEM Software Control via **File → Restore**, then trigger it from a Stream Deck button using Bitfocus Companion.

---

## Features

- **Visual preview** — see the animation play before you export
- **Click to select** boxes, drag to move, corner handles to resize, edge handles to crop/mask
- **Zoom and pan** the canvas to see boxes that are off-screen
- **Snap grid** with centre and edge snap guides (toggle on/off)
- **Multi-select** — Shift-click or rubber-band drag to select multiple boxes
- **10 built-in presets** from real-world church production macros
- **Save your own presets** — persists across sessions
- **Load existing XML macros** — upload any ATEM export, browse all SuperSource macros in the file, and load one into the editor
- **Reverse animation** — swap From↔To and download the reversed macro
- **Undo / Redo** — 10 levels, Ctrl+Z / Ctrl+Y
- **All ATEM models** supported — from ATEM Mini to Constellation 4K (up to 40 camera inputs)
- Handles both **V2** (`SuperSourceV2Box*`) and **legacy** (`SuperSourceBox*`) XML formats

### Keyboard shortcuts

| Key | Action |
|-----|--------|
| `Space` | Play / Stop preview |
| `F` | Show From frame |
| `T` | Show To frame |
| `R` | Reverse animation |
| `Ctrl+Z` | Undo |
| `Ctrl+Y` | Redo |
| `Esc` | Deselect all |
| `Shift+drag` | Add to selection / uniform scale |
| `Alt+drag` | Bypass snap |
| `Scroll` | Zoom in / out |

---

## How to use

1. **Select your ATEM model** in the top dropdown
2. **Enable the boxes** you want to animate using the toggles in the left panel
3. **Set From and To values** — either type values, scrub by clicking and dragging a number, or drag boxes directly on the canvas
4. **Choose easing and duration** in the right panel
5. **Preview** — press Space or click Play
6. **Download XML** — click the download button, name your macro and set the index
7. **Import** — in ATEM Software Control go to **File → Restore** and select the downloaded file
8. **Trigger** — set up a button in Bitfocus Companion using the **Macro: Run** action

### Importing from Companion (Stream Deck)

In Bitfocus Companion:
- Add the **Blackmagic ATEM** connection pointing to your switcher's IP
- Create a button → add action **Macro: Run** → select your macro number
- Assign to a Stream Deck key

> ⚠️ **Important:** Restoring an XML file overwrites any existing macro at that index. Check which macro slots you're using before importing.

---

## Supported devices

| Model | Inputs | SuperSources |
|-------|--------|-------------|
| ATEM Mini / Pro / ISO | 4 | — |
| ATEM Mini Extreme / ISO | 8 | 1 |
| ATEM SDI Extreme ISO | 8 | 1 |
| ATEM Television Studio range | 8 | — |
| ATEM 1 M/E Production Studio 4K | 10 | — |
| ATEM 2 M/E Production Studio 4K | 20 | 1 |
| ATEM 2 M/E Broadcast Studio 4K | 20 | 1 |
| ATEM 1 M/E Constellation HD / 4K | 10 | 1 |
| ATEM 2 M/E Constellation HD / 4K | 20 | 1 |
| ATEM 4 M/E Constellation HD / 4K | 40 | 2 |
| ATEM Constellation 8K | 8 | 1 |

---

## Technical notes

- **Single file** — the entire app is one self-contained HTML file with no external dependencies, no CDN calls, no tracking. It works completely offline.
- **BMD coordinate system** — uses the correct ±16 / ±9 BMD unit space (not the slightly-off values used by many other tools)
- **XML format** — generates `SuperSourceV2Box*` opcodes compatible with modern ATEM firmware (8.x+). Also reads legacy `SuperSourceBox*` format from older firmware and third-party tools.
- **Easing** — uses cubic Bezier curves with 8 preset options (Linear, Smooth, Ease Cubic, Ease Quart, Ease In, Ease Out, Bounce, Overshoot)
- **Frame timing** — one `MacroSleep` op per frame, same approach as the original DVE Animation Generator

---

## Credits

Inspired by the [DVE Animation Generator](https://zmip.github.io) by zmip (Karel). The SuperSource XML format and box values in the built-in presets come from real productions.

---

## License

MIT — free to use, modify, and share. If you improve it, share it back with the community.
