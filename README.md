# Integer Overflow Lab

An interactive, browser-based teaching module that shows how fixed-width
integers behave in C: how the same bits mean different numbers depending on
signedness, how arithmetic silently wraps around when a result doesn't fit, and
why that wraparound causes real security bugs.

Built for **SE/CprE 4210 — Learning Sprint #2**. It demonstrates concepts only;
it is not an exploit, shellcode, or attack tool.

## What it teaches

The app is split into three panels, each focused on one idea:

1. **One value, two meanings.** A single bit pattern is displayed as both a
   signed (two's complement) and an unsigned integer. Clicking the sign bit
   makes the two readouts diverge, which makes signed/unsigned conversion
   concrete instead of abstract.
2. **Arithmetic that wraps.** You pick an operation (`+`, `−`, `×`, `<<`) and
   two operands. The app shows the *true* mathematical result next to the value
   actually *stored* in the variable, flags whether overflow occurred, and
   places the stored value on a number line of the representable range.
3. **Allocation size overflow.** A real-world consequence: computing
   `count * element_size` to size a buffer. When that product overflows,
   the program reserves a tiny buffer and then writes far past its end — a
   classic heap buffer overflow. The default inputs (2^30 elements × 8 bytes on
   a 32-bit `size_t`) ask for 8.6 GB but wrap to **0 bytes**.

## Interaction

- **Width** dropdown — 8, 16, 32, or 64 bits.
- **Signed / unsigned** toggle — applies to every panel at once.
- **Bit grid** — click any bit to flip it; bytes are grouped with their hex value.
- **Value input + slider + quick-set buttons** (0, −1, +1, MAX, MIN).
- **Operand inputs** and an operation selector for the arithmetic panel.
- **count / element_size inputs** for the allocation panel.

All numbers accept decimal or `0x` hex, and all arithmetic is computed with
exact big integers (`BigInt`) and then masked to the chosen width, so the
displayed values are correct even at 64 bits.

## Running it

It's a single self-contained file — no build step, no dependencies to install.

- **Locally:** open `index.html` in any modern browser (double-click it, or
  `File → Open`).
- **Served:** drop it behind any static web server, e.g.

  ```bash
  python3 -m http.server 8000
  # then visit http://localhost:8000
  ```

- **GitHub Pages:** enable Pages for this repo (Settings → Pages → deploy from
  the default branch) and it will be served at the Pages URL.

The only external resource is the IBM Plex font from Google Fonts; the page
falls back to system fonts if it's offline.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The entire application — markup, styles, and logic. |
| `README.md` | This file. |
| `reflection.md` | Short write-up of the build experience and workflow. |

## Built with

Plain HTML, CSS, and JavaScript (`BigInt` for exact fixed-width math, inline SVG
for the number line). No frameworks.
