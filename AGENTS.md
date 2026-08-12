# AGENTS.md

Pure HTML5 Canvas arcade game. No build system, no dependencies: `index.html` (page + inline CSS), `game.js` (all game logic), `favicon.svg`.

## Run / verify
- No package.json, tests, lint, or typecheck. Nothing to install or run.
- Verify manually in a browser: open `index.html` directly, or `npx serve .` and visit http://localhost:3000.

## Gotchas
- `game.js` is a plain browser script loaded via `<script src>` in `index.html`, NOT an ES module. Do not add `import`/`export`; it runs at global scope under `'use strict'`.
- Canvas size is hardcoded in TWO places: the `width`/`height` attributes on `<canvas>` in `index.html` and the `W`/`H` consts at the top of `game.js`. Change both together.
- UI strings and code comments are in Spanish ("NIVEL", "PUNTAJE", "GAME OVER"). Keep new UI text in Spanish.
- README claims power-ups and a "estrella fugaz" that are NOT implemented in `game.js`. Don't trust the README's feature list.

## Game wiring (not obvious from the code)
- Game state machine: `state` is one of `'playing' | 'dead' | 'gameover'`. On `gameover`, pressing Space restarts.
- Space is used both for shooting (during play) and restarting (on game over) via the `pressed()` single-shot input helper, which consumes `justPressed` entries. Input is tracked by `e.code`; `preventDefault` stops arrow/space page scroll.
- World is toroidal: `wrap(v, max)` wraps x over `W` and y over `H`.
- `loop()` clamps `dt` to 0.05s so physics don't explode after a tab-switch stall.
- Asteroid `size` 3 (large, 20 pts) splits into 2 (50 pts), which splits into 1 (100 pts). Points come from `POINTS[size]`.
