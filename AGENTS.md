# AGENTS.md

Asteroids clone in vanilla JS. No build, no bundler, no dependencies, no tests.

## Run

Serve the directory and open `index.html`:

```bash
npx serve .
# http://localhost:3000
```

Opening `index.html` directly (double-click) also works — no module/ESM/CORS issues.

## Architecture

- `index.html` — fixed `<canvas id="canvas" width="800" height="600">`, loads `game.js`.
- `game.js` — entire game in one file: `Bullet`, `Asteroid`, `Ship`, `Particle` classes + global state + main `loop(ts)`.
- Canvas size is hardcoded `W=800` / `H=600` at the top of `game.js`; bounds wrapping is toroidal via `wrap()`.

## Conventions

- Single-file design is intentional; do not split into modules unless asked.
- Classes are defined at top level; state (`ship`, `bullets`, `asteroids`, `particles`, `score`, `lives`, `level`, `state`) is module-global, reinitialized by `initGame()`.
- Asteroid size codes: `1=small, 2=medium, 3=large`; arrays `RADII`/`SPEEDS`/`POINTS` are indexed by these codes (`0` is unused).
- All prose/comments/README are in Spanish.

## Verification

There is no test, lint, or typecheck command. To verify changes, load the game in a browser and play: spawn → shoot asteroids → die → gameover → restart.