# GORILLAS 🦍🍌

A faithful, browser-playable recreation of the classic **1985 QBasic `GORILLA.BAS`** —
two gorillas atop a city skyline lobbing exploding bananas at each other.

> The repo is named `gorilla_python`, but to make the game playable in any
> browser with zero setup it's implemented as a single self-contained HTML5
> Canvas + JavaScript file. No server, no build step, no dependencies.

## Play it

Just open **`index.html`** in any modern browser (double-click it, or drag it
into a browser tab). That's the whole install.

To serve it locally instead:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## How to play

1. Pick **2 Players (hot-seat)** or **1 Player vs Computer**, set names,
   gravity (Earth/Mars/Moon/Jupiter), and how many round wins take the match.
2. On your turn, enter an **Angle** (0–90°, automatically mirrored for the
   player on the right) and a **Velocity**, then hit **FIRE!** (or press
   <kbd>Enter</kbd> in either field).
3. Watch the **red wind arrow** at the bottom — wind pushes your banana left or
   right in flight. Adjust your next shot accordingly.
4. Hit the other gorilla to score the round. First to the win target takes the
   match.

## Features faithful to the original

- Procedurally generated, multi-colored city skyline with lit windows
- Random wind each round (shown as an arrow), plus selectable gravity
- Bananas blow real craters in buildings (destructible terrain)
- The sun gets a shocked face when you bonk it
- Throwing animation and a victory dance for the winner
- Turn-based hot-seat play **or** a computer opponent that walks its shots in
- Retro DOS-blue palette, monospace UI, and WebAudio blips/explosions

## Tech notes

Everything lives in `index.html`. Buildings are rendered to an offscreen
canvas that doubles as the **collision mask**: craters are erased from it with
`destination-out` compositing, so destruction and hit-testing stay perfectly in
sync. Physics integrates velocity, gravity, and wind per frame with light
sub-stepping for smooth arcs.
