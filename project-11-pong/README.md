# 🏓 Project 11 — Neon Pong: Arcade PvP & PvC

Welcome to the eleventh project in my **AI Engineering Journey**! 🚀

A fast, glowing browser-based **Pong** game with local two-player duels and a three-tier computer opponent. Trade rallies on one keyboard, use either key set in single-player, or steer by touch on a phone or tablet. Aim your returns with the paddle edges, and be the first to **5 points**. Every serve, rally, pause, and rematch is handled by a pure Canvas game loop.

Built with **plain HTML5 Canvas, CSS3, and Vanilla JavaScript** — no game frameworks, build tools, or backend services.

Created with **Spec-Driven Development (SDD)** and an **OpenCode** AI coding agent.

---

## ✨ Features

- 🎮 **Two game modes** — local **Player vs. Player** on a single keyboard, or **Player vs. Computer** with three selectable AI tiers.
- ⌨️ **Flexible PvC controls** — in single-player, Player 1 can use **either** `W`/`S` **or** `↑`/`↓` interchangeably. In PvP, Player 1 keeps `W`/`S` and Player 2 keeps `↑`/`↓`.
- 📱 **Full touch support** — a responsive neon touch deck with large **Up** / **Down** hold-to-move buttons appears on phones and tablets. Players can also drag directly on the court, with multi-touch support for local PvP.
- 🟢🟡🔴 **Three distinct AI profiles** — Easy reacts slowly and occasionally misjudges the ball; Intermediate tracks with a short reaction window and a small aim error; Difficult predicts the full trajectory, including wall bounces, with near-perfect precision.
- ⚡ **Vector ball physics** — the ball moves on a real velocity vector, accelerates by 4.5% on every paddle hit (up to a cap), and bounces off the top and bottom walls.
- 🎯 **Edge-based deflection** — where the ball meets the paddle changes the return angle, from a flat centre hit to a sharp 58° edge shot.
- 🏆 **First to 5 wins** — goal detection, live scores, match-point and double-match-point HUD states, a scoring banner, and a victory overlay with a rematch option.
- ⏸️ **Pause anywhere** — pause from the header or with `Space`, `P`, or `Escape`; the match also pauses automatically when the tab loses visibility.
- 🖥️ **Crisp, responsive canvas** — a fixed `1000×600` logical arena scales to any screen with DPR-aware backing-store sizing and a locked `5:3` aspect ratio.
- 🌈 **Retro-neon presentation** — a glowing court, scanlines, paddle-hit flashes, a fading ball trail, oversized score numerals, animated overlays, and a custom arcade type system.
- 🧭 **Clear match context** — the scoreboard swaps **P2** for **CPU**, shows the selected difficulty, and mirrors the mode everywhere, including the pause and victory dialogs.
- ♿ **Accessible controls and overlays** — labelled canvas, live announcements, focus-trapped dialogs, `inert` closed overlays, `aria-pressed` mode/difficulty buttons, and reduced-motion support.
- 🔁 **Session-safe restarts** — starting a new match, restarting, or returning to the menu fully resets scores, paddles, ball, serve state, and held keys.

---

## 🕹️ How to Play

1. Pick **Local PvP** or **Player vs. Computer** from the start menu.
2. In PvC, choose **Easy**, **Intermediate**, or **Difficult**.
3. Press **Start Match**. After a short serve countdown, the ball launches toward one side.
4. Move your paddle to intercept the ball. Hitting with the paddle edge sends a sharper return.
5. The first player or computer to **5 points** wins the match.
6. Use **Rematch** to replay the same mode and difficulty, or **Change Mode** to return to the menu.

### Keyboard controls

| Action | PvP: Player 1 (left) | PvP: Player 2 (right) | PvC: Player 1 (left) |
| --- | --- | --- | --- |
| Move up | `W` | `↑` | `W` **or** `↑` |
| Move down | `S` | `↓` | `S` **or** `↓` |
| Pause / resume | `Space`, `P`, or `Escape` | `Space`, `P`, or `Escape` | `Space`, `P`, or `Escape` |
| Return to menu | **Menu** button | **Menu** button | **Menu** button |
| Restart during pause | **Restart** button | **Restart** button | **Restart** button |

In **PvC**, the computer controls the right paddle. The human player can switch freely between `W`/`S` and the arrow keys at any point in the match—both key sets stay active.

### Touch controls

On phones and tablets, a touch deck appears below the arena during play. On touch-first layouts, keyboard hints step aside so the controls stay clear.

| Gesture | PvP | PvC |
| --- | --- | --- |
| Drag on the **left half** of the court | Steers Player 1 | Steers Player 1 |
| Drag on the **right half** of the court | Steers Player 2 | Steers Player 1 |
| Hold the **left pad** Up / Down buttons | Moves Player 1 | Moves Player 1 |
| Hold the **right pad** Up / Down buttons | Moves Player 2 | Pad is hidden (AI controls the right paddle) |

PvP supports two simultaneous fingers—one on each half of the court—so both paddles can move at once. Touch drag uses damped follow motion for smooth, jitter-free steering, and all touch input is cleared when the match pauses, ends, or returns to the menu.


### Difficulty tiers

| Tier | Paddle speed | Reaction | Aim behavior |
| --- | --- | --- | --- |
| 🟢 **Easy** | 340 u/s | 240 ms | Tracks the ball's current Y with a wide error window and a 16% chance to miscalculate badly. |
| 🟡 **Intermediate** | 540 u/s | 70 ms | Follows a short forward lead (up to 220 ms) with a small aim error. |
| 🔴 **Difficult** | 780 u/s | 15 ms | Predicts the exact intercept point, folding the path through wall bounces, with almost no error. |

### Scoring

| Event | Result |
| --- | --- |
| Ball fully passes the left edge | **Player 2 / Computer** scores |
| Ball fully passes the right edge | **Player 1** scores |
| A player reaches **5** | Match ends immediately; the victory overlay opens |

After each point, the ball and paddles reset to the centre and the next serve is directed toward the player who conceded. The HUD announces **Match point** at 4 points and **Double match point** at 4–4.

---

## 🗂️ Project Structure

```text
project-11-pong/
├── index.html              # Header, scoreboard, canvas arena, touch controls, menu, pause and victory dialogs
├── styles/
│   └── style.css           # Neon design system, stage glow, responsive touch deck, score panels, menu cards, overlays, responsive rules
├── js/
│   └── main.js             # Fixed-step loop, keyboard/touch input, AI tiers, vector physics, scoring, renderer, state machine
└── README.md               # Run instructions, architecture notes, SDD workflow, agent metadata
```

---

## 🚀 How to Run

1. Clone or download this repository.
2. Navigate to the `project-11-pong` folder.
3. Open `index.html` directly in a modern browser (Chrome, Edge, Firefox, or Safari).
4. Or serve the folder with **VS Code Live Server** (or any static server).

No installation, package manager, or build step is required.

> **Offline note:** the Google Fonts link is progressive enhancement. The game falls back to system fonts if it is unavailable.

---

## 🧠 How It Works

### World model & canvas scaling

The simulation always runs in a **1000 × 600 logical world**, independent of the display size. The canvas is laid out with a CSS `aspect-ratio: 5 / 3`, and `resizeCanvas()` matches its backing store to the rendered size multiplied by the device pixel ratio (capped at `2`). The renderer then applies a single scale transform, so all physics and drawing share the same coordinate system on every screen.

`ResizeObserver`, `resize`, and `orientationchange` all refresh the backing store, keeping the court sharp after layout changes.

### Fixed-step game loop

Rendering uses `requestAnimationFrame`, but physics does not depend on the refresh rate:

```text
requestAnimationFrame
   ↓
delta = min(frame time, 50 ms)
   ↓
accumulator += delta
   ↓ while accumulator ≥ 1/120 s (max 8 steps)
stepSimulation(1/120 s)
   ↓
render()
```

The `1/120 s` fixed step keeps collisions and paddle movement consistent on 60 Hz, 120 Hz, and variable-rate displays. The capped accumulator and step limit prevent a long tab stall from producing a burst of simulation after the page resumes. Only `playing` advances the simulation; `menu`, `paused`, and `gameover` hold the world still.

### Ball physics

The ball carries a velocity vector `(vx, vy)`:

- **Launch** — each serve starts at `520 u/s` with a random angle within roughly ±19.5°.
- **Paddle hit** — speed is multiplied by `1.045`, capped at `1180 u/s`.
- **Deflection** — the ball's offset from the paddle centre becomes a normalized `-1…1` value, mapped to a bounce angle up to **±58°**. A centre hit returns flat; an edge hit returns sharply.
- **Collision** — circle-versus-rectangle overlap is tested against the paddle, with the ball repositioned just outside the paddle face to avoid sticking.
- **Walls** — top and bottom collisions reflect the vertical component and clamp the ball inside the court, preserving its speed.
- **Goals** — a point is awarded only once the whole ball has crossed beyond the left or right boundary.

A short trail of the last 18 positions is recorded for the glowing motion effect.

### AI decision model

The computer does not cheat by reading the ball's future position directly. Each tier shares one pipeline but changes its parameters:

1. **Perceive** — a decision timer throttles how often the AI updates its target, creating a human-like reaction window.
2. **Predict** — Easy aims at the ball's current height; Intermediate adds a limited forward lead; Difficult calculates the exact time to the paddle plane and folds the resulting Y through the walls using a triangular wave, which reproduces real bounce paths without simulating each frame.
3. **Aim** — an error offset is applied. Easy additionally has a 16% chance to aim far off the incoming line.
4. **Move** — the paddle travels toward the target at its tier speed, with a deadzone that stops jitter around the target.
5. **Reset** — while the ball is serving or moving away, the AI recentres instead of mirroring the player.

### Match state machine

| Phase | Meaning |
| --- | --- |
| `menu` | Start menu is open; the court is idle and scores are zero. |
| `playing` | Fixed-step simulation is active, including the serve-delay sub-state. |
| `paused` | The world is frozen; the pause dialog is open. |
| `gameover` | A player reached 5; the victory dialog is open and input is ignored. |

The serve countdown is a timer inside `playing`: paddles and ball are centred, movement is suspended, then `launchServe()` assigns the velocity. This keeps the serve deterministic and avoids a separate top-level phase.

Input is tracked in a `Set` of key codes rather than as per-frame flags. A second set holds held touch buttons, and a per-paddle drag record stores the active touch identifier and target Y. `window.blur` and tab hiding clear all input so a paddle never keeps moving after focus is lost; hiding the tab also pauses an active match.

### Input & touch routing

`paddleAxis(side)` merges every input source for a paddle:

- **Player 1** always reads `W` / `S`. In PvC it also reads `↑` / `↓`; in PvP those arrows belong only to Player 2.
- **Player 2** reads the arrow keys and the right-pad touch buttons. In PvC the AI owns the right paddle instead.
- **Touch buttons** add logical `left-up`, `left-down`, `right-up`, and `right-down` entries while held. Pointer capture keeps a press alive if a thumb slides slightly off the button.
- **Canvas drag** maps each touch to a side. PvC routes every touch to Player 1; PvP splits at the court's midpoint, and separate touch identifiers let both players drag at the same time.

The drag target is converted from viewport coordinates into the `1000 × 600` world and clamped to the court. Instead of snapping, `followTouchDrag()` eases the paddle toward the target with an exponential follow factor, so finger movement feels smooth while still responding within a few frames. While a drag is active it takes priority over button and keyboard input for that paddle.

`touchstart`, `touchmove`, `touchend`, and `touchcancel` are bound with `passive: false` on the canvas, and `preventDefault()` plus `touch-action: none` stop page scrolling and pinch-zoom during play. Every lifecycle transition—start, pause, resume, menu, game over, window blur, or tab hide—runs `clearInput()`, which releases held buttons, clears drag identifiers, and removes pressed-state styling.

The touch deck is only revealed during a live match. On PvC it switches to a centered solo pad and hides the Player 2 pad; on PvP it shows both. CSS media queries enable it for narrow viewports and coarse pointers, and the large buttons keep at least a 44 px target on phones.

### Rendering

The Canvas renderer draws the arena background, grid, centre divider, ghost score numerals, corner brackets, ball trail, both paddles, the ball, and the serve indicator every frame. Glow is produced with `shadowBlur` and gradients; paddle hits raise a short `flash` value for a brighter impact pulse. The entire scene is redrawn in logical coordinates, which keeps the visual layer simple and consistent.

### Overlays & focus

The start menu, pause dialog, and victory dialog are viewport-level overlays. `showOverlay()` hides every other overlay, removes `inert`, updates `aria-hidden`, and moves focus into the newly opened panel on the next animation frame. A document-level `Tab` handler traps focus inside the open dialog, and starting or resuming a match returns focus to the canvas.

---

## ♿ Accessibility

- The canvas is focusable, labelled as the **Neon Pong arena**, and described with the controls and win condition for screen readers.
- A polite **live region** announces match start, pauses, points, the current score, resumes, and the winner.
- All three overlays use `role="dialog"`, `aria-modal="true"`, labelled titles, and focus management; closed overlays are `inert`.
- Mode and difficulty choices expose their state with `aria-pressed`, and the difficulty fieldset is disabled outside PvC.
- Arrow-key input calls `preventDefault()` during play so the page does not scroll while steering.
- Touch buttons have descriptive `aria-label`s, visible pressed states, and at least 44 px targets; the court and buttons use `touch-action: none` so gestures never scroll or zoom the page.
- The touch deck is removed from the tab order when it is hidden or not in play, and it appears on mobile/tablet layouts without relying on hover.
- Pause, restart, resume, rematch, and menu actions are available as real buttons, not keyboard-only shortcuts.
- `prefers-reduced-motion` shortens or removes decorative animations while preserving gameplay and overlay behavior.

---

## 🧠 Spec-Driven Development (SDD) Workflow

This project follows the same SDD loop used across the lab:

1. **Specification first** — `SPEC.md` fixes the scope: local PvP, three PvC tiers, flexible PvC keyboard controls, arrow-key PvP controls, touch buttons and canvas drag, vector physics with edge deflection and speed increases, wall bounces, first-to-5 scoring, and neon overlays. It also sets the non-goals: no servers, WebSockets, external game frameworks, or gamepad support.
2. **Contract-driven architecture** — responsibilities were assigned before implementation: semantic markup for the scoreboard, touch deck, and dialogs; one stylesheet for the neon system; and one Vanilla JS engine for simulation, AI, scoring, input routing, and rendering.
3. **Implementation against the contract** — the world model, fixed-step loop, paddle/AI movement, collision resolution, serve state, overlay state machine, and multi-source touch/keyboard input were built as separate sections of `main.js`, with no framework runtime.
4. **Validation** — the acceptance surface was exercised against the spec: both modes, every AI tier, both PvC key sets, touch buttons, single- and multi-touch drag, pause/resume cleanup, scoring, match end, rematch, focus handling, responsive layout, and runtime errors.
5. **Documentation** — this README records how to run the game, how the simulation and AI work, the match lifecycle, accessibility behavior, and the agent configuration for traceability.

The goal is not just to generate code, but to make the requirements explicit, review the result against them, and keep the implementation understandable.

---

## 🤖 OpenCode AI Agent Metadata

Transparency matters when building with AI. Here is the agent setup used for this project:

- **Agent CLI Tool:** [OpenCode](https://opencode.ai)
- **AI Model:** `Big Pickle` *(OpenCode default reasoning model)*
- **Execution Mode:** `Build`
- **Workflow Methodology:** **Spec-Driven Development (SDD)**
- **Primary Input:** `SPEC.md`, the repository's project conventions, and the Project 10 README documentation pattern
- **Key Agent Capabilities Demonstrated:**
  - 📜 **Spec parsing** — translated the contract into game phases, physics rules, AI tiers, scoring conditions, and an acceptance checklist.
  - 🧩 **Simulation engineering** — a fixed `1/120 s` step, capped frame delta, accumulator loop, and resolution independent of display refresh rate.
  - 🏓 **Physics & collision** — vector velocity, speed escalation, circle-versus-rectangle collision, paddle-edge bounce mapping, and wall reflection.
  - 🧠 **AI design** — a shared perception/aim/move pipeline with per-tier reaction delays, speed limits, error windows, occasional miscalculation, and wall-aware trajectory prediction.
  - 🧭 **State management** — explicit menu/playing/paused/gameover phases, a serve sub-state, guarded input, score transitions, and match-point HUD states.
  - 🕹️ **Multi-source input** — shared keyboard/touch routing, flexible PvC key sets, pointer-captured hold buttons, multi-touch canvas drag, and lifecycle input cleanup.
  - 📱 **Responsive UI** — a neon touch deck that switches between solo and dual-pad layouts, respects 44 px touch targets, and avoids page scroll or overflow.
  - 🎨 **Canvas presentation** — DPR-aware scaling, neon gradients and shadows, ball trail, paddle impact flashes, scanlines, and animated overlays.
  - ♿ **Accessibility** — labelled canvas, live region, focus-trapped dialogs, `inert` overlays, `aria-pressed` selections, and reduced-motion support.
  - 🧪 **Validation** — syntax gate plus headless-browser suites for full matches, all AI tiers, both keyboard schemes, touch buttons, multi-touch drag, pause/resume, focus, and responsive layout.

---

## 🛠️ Tech Stack

- **HTML5** — semantic header, scoreboard, Canvas arena, mode/difficulty menu, touch control deck, pause dialog, victory dialog, live region
- **CSS3** — custom properties, gradient/glow design system, scanlines, keyframe animations, aspect-ratio layout, touch-deck media queries, responsive and short-viewport rules, `prefers-reduced-motion`
- **Vanilla JavaScript (ES6+)** — fixed-step game loop, 2D vector physics, AABB/circle collision, wall-aware AI prediction, keyboard/touch state, multi-touch drag routing, match state machine, Canvas 2D rendering, DPR-aware resizing

---

## 🌐 Live Demo

🔗 **Live Site:** [View Project 11 Live](https://nilmerosorio.github.io/My-AI-Engineering-Journey/project-11-pong/)

---

## 📝 Notes

- The arena is a fixed `1000 × 600` logical space; only the display size changes.
- Ball speed rises on every paddle hit and is capped so late rallies stay playable.
- In PvP, both players share one keyboard; `W`/`S` control Player 1 and the arrow keys control Player 2. In PvC, Player 1 can use either set.
- On touch screens, the on-screen pads and direct court drag both work. Switching to a foreground keyboard is optional, not required.
- The computer recentres while the ball moves away, so it does not mirror the player's every move.
- The game pauses automatically when the tab is hidden, but does **not** resume automatically.
- There is no sound, online play, or persistent storage — the spec's non-goals exclude servers and external frameworks, and this version stays a local arcade cabinet.
- The match always ends at 5 points; there is no win-by-two rule.

---

*Part of my AI Engineering Portfolio — learning to build software with AI, understand the code, and ship with intention.* 🌟
