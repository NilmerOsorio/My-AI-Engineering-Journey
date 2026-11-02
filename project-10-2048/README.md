# 🔢 Project 10 — 2048: Sliding Tile Puzzle

Welcome to the tenth project in my **AI Engineering Journey**! 🚀

A sleek, responsive browser-based **2048** puzzle game. Slide the board with the arrow keys, WASD, or a touch swipe, merge matching tiles, and chase the 2048 milestone. Your best score is saved locally, and the win/loss overlays keep every run clear.

Built with **plain HTML5, CSS3, and Vanilla JavaScript** — no game frameworks, build tools, or backend services.

Created with **Spec-Driven Development (SDD)** and an **OpenCode** AI coding agent.

---

## ✨ Features

- 🎯 **True 4×4 matrix model** — a 16-cell board of tile objects, with null cells for empty slots and tile values that grow by powers of two.
- ↔️ **Four-direction slide & merge** — arrow keys, WASD, and touch swipes all feed the same deterministic move engine.
- 🧠 **Correct single-merge rules** — a tile can merge only once per move; newly merged tiles never cascade in the same move (`2,2,2,2 → 4,4`, not `8`).
- 🎲 **Random tile spawner** — every board-changing move adds a `2` (90%) or `4` (10%) to a random empty cell.
- 🏆 **Live score + persistent best** — merged values are added to the score, and a new personal best is written to `localStorage` immediately.
- 🪟 **Win milestone** — creating a 2048 tile opens a victory dialog with **Keep Playing** and **New Game** options.
- 🧱 **Game-over detection** — the run ends only when the board is full **and** no adjacent equal tiles remain, with a final score summary and restart button.
- 🎨 **Tile color system** — dedicated palettes for `2 → 2048`, an extra style for super tiles, automatic font scaling for 3–5 digit values, and gold glow on the top tile.
- 🎬 **Seamless slide & merge motion** — tiles glide between cells with a GPU-friendly `translate3d` transition. Merge swaps and new spawns wait for the actual `transitionend`, then land with a subtle scale/brightness pop — no cut-off slides or mid-glide snaps.
- 📱 **Responsive layout** — the square board scales from small phones to desktop with no horizontal overflow.
- ♿ **Accessible interactions** — focusable board, live announcements, a screen-reader board summary, dialog focus trapping, `Escape` support, and reduced-motion handling.
- 🔁 **Session-safe restarts** — a session token invalidates pending move callbacks when you start a new game mid-animation.

---

## 🕹️ How to Play

1. The game starts with two random tiles on the board.
2. Slide every tile in one direction: **← ↑ → ↓** or **W A S D**.
3. When two equal numbers collide, they merge into their sum and that value is added to your score.
4. A new `2` or `4` spawns after every valid move.
5. Keep merging to create the **2048** tile. The game ends only when the board is full and no legal moves remain.

### Scoring

| Merge | Points |
| --- | --- |
| `2 + 2 → 4` | **+4** |
| `4 + 4 → 8` | **+8** |
| `128 + 128 → 256` | **+256** |
| `1024 + 1024 → 2048` | **+2048** |

Multiple merges in one move all count. The **Best** card updates in real time whenever the current score passes the stored record.

### Controls

| Action | Keyboard | Pointer / touch |
| --- | --- | --- |
| Slide left | `←` or `A` | Swipe left |
| Slide right | `→` or `D` | Swipe right |
| Slide up | `↑` or `W` | Swipe up |
| Slide down | `↓` or `S` | Swipe down |
| New game | **New Game** button | Click / tap |
| Keep playing after 2048 | `Escape` or **Keep Playing** | Click / tap |
| Restart after game over | **Play Again** button | Click / tap |

---

## 🗂️ Project Structure

```text
project-10-2048/
├── index.html              # Header, score cards, 4x4 board, win/loss dialogs, live regions
├── styles/
│   └── style.css           # Design tokens, board grid, tile palette, animations, responsive layout
├── js/
│   └── main.js             # Matrix engine, slide/merge logic, transition-synced finalization, spawner, input, score, state machine
├── SPEC.md                 # Original specification contract
└── README.md               # Run instructions, architecture notes, SDD workflow, agent metadata
```

---

## 🚀 How to Run

1. Clone or download this repository.
2. Navigate to the `project-10-2048` folder.
3. Open `index.html` directly in a modern browser (Chrome, Edge, Firefox, or Safari).
4. Or serve the folder with **VS Code Live Server** (or any static server).

No installation, package manager, or build step is required. Scores persist per browser origin, so use the same URL when reopening the game.

> **Offline note:** the Google Fonts link is progressive enhancement. The game falls back to system fonts if it is unavailable.

---

## 🧠 How It Works

### Board model

The board is a `4×4` array of cells. Each occupied cell holds a tile object:

```js
{ id: 12, value: 64 }
```

The stable `id` lets the renderer keep a DOM element per tile and animate it from one cell to another. Empty cells are `null`.

### Slide & merge algorithm

`computeMove(direction)` reads each row or column from the movement edge inward:

1. **Compress** — drop empty cells from the line.
2. **Merge in one pass** — compare adjacent values, merge matching pairs, add the merged value to the score, and skip the consumed neighbour. Skipping is what prevents double merges.
3. **Assign** — write the resulting tiles back to the nearest edge cells.
4. **Track movement** — record each source tile's target cell for the CSS transition.
5. **Report** — return the next grid, merge metadata, points gained, and a `changed` flag.

An unchanged move is rejected: no tile spawns, no score changes, and the board gives a short nudge animation instead.

### Move pipeline & animation

```text
key / swipe
   ↓
computeMove(direction)
   ↓ changed?
   ├─ no  → board nudge, stop
   └─ yes → mark busy, update score/best, glide tiles (250 ms)
              ↓
           wait for every moved tile's transform transitionend
           (with a timeout fallback so input can never stay locked)
              ↓
           finishMove()
              ├─ replace merged sources with the new tile (scale/brightness pop)
              ├─ spawn a random 2 or 4 (soft scale/fade entrance)
              ├─ refresh screen-reader summary
              ├─ check 2048 milestone
              └─ check game-over condition
```

Tiles are absolutely positioned in a CSS grid layer. Changing their `--row` / `--column` custom properties updates a `translate3d(...)` transform, and CSS transitions that transform over `250 ms` with a smooth `cubic-bezier(0.25, 1, 0.5, 1)` ease. That pace is deliberate: the motion is slow enough to visually track every tile across the board, yet still snappy enough for rapid play. The JavaScript engine tracks only tiles whose coordinates actually changed and waits for all of their `transitionend` events before replacing merged tiles or spawning. That timing is what keeps the animation seamless: source tiles are never removed early, and a new tile never appears before the glide has landed.

The merge pop animates the independent `scale` and `filter` properties (`1 → 1.1 → 1` plus a light brightness flash), while position remains controlled by `transform`. Because the effects use separate properties, a merge can pop without interrupting or snapping its positional transition. If `transitionend` is missed, a fallback timer completes the move; reduced-motion users get a near-instant version of the same sequence.

### Game state machine

| Flag | Meaning |
| --- | --- |
| `busy` | A move animation is running; further input is ignored until it finishes. |
| `won` | The 2048 tile has been reached; the win dialog is latched. |
| `over` | The board is full with no legal merges; input is blocked. |
| `newBest` | The run passed the stored record and should show the badge on game over. |

A `session` counter increments on every restart. Active slide listeners and fallback timers check the token, and restarting explicitly cancels the current slide, preventing stale tiles from appearing after a fast reset.

### Game-over check

The board is over only when **both** conditions hold:

- every cell is occupied, and
- no horizontally or vertically adjacent tiles share a value.

---

## 💾 Persistence

| Key | Value |
| --- | --- |
| `game2048.best.v1` | Highest score reached in this browser |

Reads and writes are wrapped in `try/catch`. If storage is blocked or unavailable (for example, strict private mode), the game continues with an in-memory best score.

Only the best score is persisted. The current board and score reset on reload, which keeps every session a fresh run.

---

## ♿ Accessibility

- The board is focusable and labelled as a game group.
- A hidden **board summary** describes every row and the current score; a polite **live region** announces merges, wins, and game over.
- Win/loss dialogs use `role="dialog"`, `aria-modal="true"`, labelled titles, and focus management.
- Focus is trapped inside an open dialog and returns to the board or the triggering control when it closes.
- `Escape` dismisses the win dialog through the same path as **Keep Playing**.
- Arrow-key input calls `preventDefault()` so the page does not scroll while playing.
- `prefers-reduced-motion` collapses slide transitions and pop animations to near-instant while keeping every game rule and input path identical.

---

## 🧪 Validation

The implementation was checked in a headless Edge browser with Playwright, including:

- **Deterministic matrix tests** — left, right, up, and down slides; gap compression; `2,2,4,4` merges; `2,2,2,2 → 4,4`; no cascading merge; unchanged moves.
- **Game-over logic** — full board without equal neighbours, full board with one legal pair, and a board with an empty cell.
- **Win/loss flows** — threshold detection, correct score summary, new-best badge, keep-playing path, restart reset, and input blocking after game over.
- **DOM pipeline** — merged tile at the target cell, one spawn per valid move, score/best updates, and input unlock after animation.
- **Motion continuity** — computed `250 ms` transform transition, mid-slide tile coordinates interpolate between origin and destination, merged tiles appear only after `transitionend`, and the fallback path releases input if an event is missed.
- **Persistence** — writing and restoring `game2048.best.v1` across reloads.
- **Interactions** — Arrow keys, WASD, invalid-move nudge, dialog focus trap, `Escape`, and a real touch swipe via CDP.
- **Layout** — 16 tiles aligned exactly with their grid cells, distinct palettes, font scaling for large values, square board at desktop and mobile widths, and no horizontal overflow.
- **Stress** — a long automated session until game over with no runtime errors.

`node --check js/main.js` is also used as a fast syntax gate.

---

## 🧠 Spec-Driven Development (SDD) Workflow

This project follows the same SDD loop used across the lab:

1. **Specification first** — `SPEC.md` fixes the scope: the 4×4 matrix, slide/merge rules, random spawner, score and best-score tracking, win/loss overlays, tile aesthetics, motion requirements, and non-goals (no backend, no heavy frameworks).
2. **Contract-driven architecture** — file responsibilities are defined before implementation: semantic markup for the header, board, and dialogs; one stylesheet for the visual system; and one Vanilla JS engine for all game rules.
3. **Implementation against the contract** — the engine keeps the matrix model separate from rendering, exposes a single move pipeline, and uses stable tile IDs so the DOM can animate real movement rather than re-render every cell. Merge swaps and spawns are held until the slide's `transitionend`, with a timer fallback.
4. **Validation** — the acceptance surface is exercised against the spec: every direction, no-double-merge cases, valid/invalid moves, spawn behavior, live scoring, persistence, win and loss dialogs, keyboard and swipe input, transition continuity, focus handling, and responsive layout.
5. **Documentation** — this README records how to run the game, how the engine works, the storage contract, the accessibility behavior, and the agent configuration for traceability.

The goal is not just to generate code, but to make the requirements explicit, review the result against them, and keep the implementation understandable.

---

## 🤖 OpenCode AI Agent Metadata

Transparency matters when building with AI. Here is the agent setup used for this project:

- **Agent CLI Tool:** [OpenCode](https://opencode.ai)
- **AI Model:** `Big Pickle` *(OpenCode default reasoning model)*
- **Execution Mode:** `Build`
- **Workflow Methodology:** **Spec-Driven Development (SDD)**
- **Primary Input:** `SPEC.md`, the repository's project conventions, and the Project 09 README documentation pattern
- **Key Agent Capabilities Demonstrated:**
  - 📜 **Spec parsing** — translated the contract into a matrix model, move pipeline, state flags, scoring rules, and acceptance checklist.
  - 🧩 **Algorithm engineering** — edge-first line extraction, compression, single-pass pair merging, consumed-neighbour skipping, and movement metadata for animation.
  - 🎬 **DOM animation** — stable tile IDs, GPU-friendly `translate3d` positioning, transitionend-synchronized merge/spawn finalization, and independent scale/brightness pops that never interrupt the slide.
  - 🧠 **State management** — busy/won/over/new-best flags, a session token for safe restarts, and guarded input paths.
  - 💾 **Persistence** — defensive `localStorage` reads/writes with a graceful in-memory fallback.
  - 🎨 **UI engineering** — warm arcade tile palette, responsive square board, modal system, score bumps, nudge feedback, and reduced-motion support.
  - ♿ **Accessibility** — focusable board, live region announcements, screen-reader row summary, dialog focus trap, and `Escape` handling.
  - 🧪 **Validation** — syntax gate plus headless-browser suites for deterministic merges, win/loss flows, persistence, keyboard/swipe input, layout alignment, and long-session stress.

---

## 🛠️ Tech Stack

- **HTML5** — semantic header, score cards, game board, dialog overlays, live regions
- **CSS3** — custom properties, CSS Grid, `translate3d` transforms, easing curves, keyframe animations, responsive layout, `prefers-reduced-motion`
- **Vanilla JavaScript (ES6+)** — 2D matrix algorithms, stable-ID tile rendering, `transitionend` synchronization with timeout fallbacks, event handling, `localStorage`, and a small explicit state machine

---

## 🌐 Live Demo

🔗 **Live Site:** [View Project 10 Live](https://nilmerosorio.github.io/My-AI-Engineering-Journey/project-10-2048/)

---

## 📝 Notes

- Only the best score persists; the board and current score reset on reload.
- New tiles are distributed randomly, with a 90% chance of `2` and a 10% chance of `4`.
- The win dialog appears once per run. If the board is also locked after 2048, **Keep Playing** reveals the game-over summary.
- Input is intentionally locked for the short slide animation so moves cannot overlap.
- Touch swipes require at least a 24 px gesture and use the dominant axis.
- The board uses a fixed `4×4` layout by design; the spec's non-goals exclude multiplayer, accounts, and backend leaderboards.

---

*Part of my AI Engineering Portfolio — learning to build software with AI, understand the code, and ship with intention.* 🌟
