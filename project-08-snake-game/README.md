# 🐍 Project 08 — Neon Snake: Retro Arcade

Welcome to the eighth project in my **AI Engineering Journey**! 🚀

A sleek, responsive **Snake** game built with pure **HTML5 Canvas**, **CSS3**, and **Vanilla JavaScript**. It pairs classic grid-based snake mechanics with a neon arcade aesthetic, smooth interpolated movement, custom sound effects for scoring and losing, and persistent high scores.

Built with **Spec-Driven Development (SDD)** and an **OpenCode** AI coding agent.

---

## ✨ Features

- 🎮 **Classic snake mechanics** — grid movement, growth on every fruit, and precise wall / self-collision detection.
- 🕹️ **Smooth controls** — Arrow keys or `WASD`, with a two-step input buffer and anti-reverse logic so the snake can never turn into itself.
- 🌀 **Interpolated rendering** — the game steps on a fixed grid tick but renders between cells, so movement looks fluid instead of jumpy.
- 🍊 **Random food spawning** — fruit only appears on free cells, with a spawn pop animation and a particle burst when eaten.
- ⚡ **Progressive speed** — the snake gets faster with every fruit, down to a playable minimum interval.
- 🏆 **Persistent high score** — personal best saved in `localStorage` and shown on the start screen, HUD, and game-over card.
- 🔊 **Custom audio FX** — a scoring clip on every fruit and a game-over clip on collision, with pooled playback, mute toggle, and saved preference.
- 🖥️ **Clean game states** — Start, Playing, Paused, and Game Over overlays with keyboard and pointer support.
- ⏸️ **Pause & auto-pause** — press `P` to pause, or let the game pause itself when the tab loses focus.
- 📱 **Responsive + touch** — the board scales to the viewport and supports swipe gestures on touch devices.
- ♿ **Accessible touches** — focus management, `aria-live` announcements, `inert` hidden overlays, and reduced-motion support.
- ⚡ **Zero dependencies** — no frameworks, build tools, or backend.

---

## 🕹️ How to Play

1. Press **Start Game** (or `Space`).
2. Steer the snake with the **Arrow keys** or **WASD**.
3. Eat the glowing fruit to score **+10 points** and grow by one segment.
4. Avoid the walls and your own tail.
5. Beat your best score — it is saved automatically.

### Controls

| Action | Keyboard | Touch |
| --- | --- | --- |
| Move | Arrow keys / `W` `A` `S` `D` | Swipe on the board |
| Start / restart | `Space` or `Enter` on the focused button | Tap **Start** / **Play Again** |
| Pause / resume | `P` | Tap **Resume** |
| Mute / unmute | `M` or the **SFX** button | Tap the **SFX** button |

### Scoring & speed

| Event | Effect |
| --- | --- |
| Eat fruit | `+10` points, `+1` body segment |
| Each fruit | Grid step speeds up by `4 ms` (from `140 ms` down to `72 ms`) |
| Wall or tail collision | Run ends, loss sound plays, game-over card appears |

---

## 🗂️ Project Structure

```text
project-08-snake-game/
├── index.html              # Canvas stage, HUD, start / pause / game-over overlays
├── styles/
│   └── style.css           # Neon arcade theme, scanlines, responsive layout, animations
├── js/
│   └── main.js             # Game loop, snake physics, food, collisions, audio, persistence
├── assets/
│   └── audio/
│       ├── scoring_points.mp3   # Played when the snake eats fruit
│       └── game_over.mp3        # Played on wall / self collision
└── README.md               # Documentation and AI agent workflow metadata
```

---

## 🚀 How to Run

1. Clone or download this repository.
2. Navigate to the `project-08-snake-game` folder.
3. Open `index.html` directly in a modern browser (Chrome, Firefox, Edge, or Safari).
4. Optionally, serve it with **VS Code Live Server** or any static HTTP server:

No installation, package manager, or build step is required.

> **Audio note:** browsers only allow sound after a user gesture. The game unlocks the audio clips on the first **Start** / **Play Again** press, so the first fruit and collision sounds play normally.

---

## 🔊 Audio System

The game uses the two pre-existing clips in `assets/audio/`:

| Clip | Trigger | Behaviour |
| --- | --- | --- |
| `scoring_points.mp3` | Snake eats fruit | Pool of 3 players so rapid pickups never cut each other off |
| `game_over.mp3` | Wall or self collision | Single player, fired the moment the run ends |

Implementation details:

- **Pooled playback** — each clip has its own `Audio` player pool, reset to `currentTime = 0` before every trigger.
- **Gesture unlock** — a muted play/pause pass on the first user gesture satisfies autoplay policies.
- **Mute toggle** — the `SFX` button and the `M` key toggle sound; the choice is stored in `localStorage`.
- **Path resilience** — clips load from `assets/audio/` first, then fall back to the flat `assets/` folder for backwards compatibility.
- **Fail-safe** — missing or blocked audio never interrupts gameplay; playback errors are swallowed.

---

## 💾 Persistence

| Key | Value |
| --- | --- |
| `snake.highScore.v1` | Best score across sessions |
| `snake.muted.v1` | Saved sound preference (`true` / `false`) |

All reads and writes are wrapped in `try/catch`, so private-mode or blocked storage degrades gracefully to an in-memory best score.

---

## 🧠 Spec-Driven Development (SDD) Workflow

This project follows the same Spec-Driven Development loop used across the lab:

1. **Specification first** — `SPEC.md` fixes the scope: grid movement, anti-reverse controls, food/growth rules, collision handling, audio triggers, high-score persistence, and the Start / Playing / Game Over states.
2. **Contract-driven architecture** — the file structure and responsibilities are defined before implementation: markup for the stage and overlays, one stylesheet for the neon theme, and one Vanilla JS engine.
3. **Implementation against the contract** — the engine is built as an explicit state machine with a fixed-step update and interpolated render, buffered input, pooled audio, and defensive persistence.
4. **Validation** — the acceptance checklist is exercised against the spec: start/restart transitions, growth and scoring, anti-reverse, wall and self collisions, sound triggers, pause/resume, high-score writes, and responsive layout.
5. **Documentation** — this README records how to run the game, the controls, the audio behaviour, and the agent configuration for traceability.

The goal is not just to generate code, but to make the requirements explicit, review the result against them, and keep the implementation understandable.

---

## 🤖 OpenCode AI Agent Metadata

Transparency matters when building with AI. Here is the agent setup used for this project:

- **Agent CLI Tool:** [OpenCode](https://opencode.ai)
- **AI Model:** `Big Pickle` *(OpenCode default reasoning model)*
- **Execution Mode:** `Build`
- **Workflow Methodology:** **Spec-Driven Development (SDD)**
- **Primary Input:** `SPEC.md`, the pre-existing `assets/audio/` clips, and the repository's project conventions
- **Key Agent Capabilities Demonstrated:**
  - 📜 **Spec parsing** — translated the contract into a concrete state machine, data model, and acceptance checklist.
  - 🧠 **Game-loop engineering** — fixed-timestep updates with `requestAnimationFrame`, delta clamping, and interpolated grid rendering.
  - 🕹️ **Input design** — direction queueing with duplicate and 180° turn rejection, plus keyboard, pointer, and swipe support.
  - 🔊 **Audio integration** — pooled playback, autoplay unlock, mute persistence, and path fallback for the custom clips.
  - 💾 **Persistence** — defensive `localStorage` handling for high scores and sound preference.
  - 🎨 **UI engineering** — neon arcade theme, animated overlays, responsive canvas sizing, and reduced-motion support.
  - ✅ **Automated validation** — headless logic tests plus a real-browser DevTools pass covering start, game over, restart, anti-reverse, pause, audio loading, and layout overflow.

---

## 🛠️ Tech Stack

- **HTML5** — semantic structure, Canvas stage, accessible overlays and live status region
- **CSS3** — custom properties, gradients, scanlines, responsive layout, keyframe animations, `prefers-reduced-motion`
- **Vanilla JavaScript (ES6+)** — class-based engine, `requestAnimationFrame`, event handling, `Audio`, `localStorage`

---

## 🌐 Live Demo

🔗 **Live Site:** [View Project 08 Live](https://nilmerosorio.github.io/My-AI-Engineering-Journey/project-08-snake-game/)

---

## 📝 Notes

- Only the high score and mute preference persist; the board itself resets on reload.
- The Google Fonts link is a progressive enhancement — the game falls back to system fonts offline.
- The canvas renders at device-pixel resolution (capped at 2×) for crisp lines on high-DPI screens.
- `P` pauses mid-run; the game also auto-pauses when the tab or window loses focus.

---

*Part of my AI Engineering Portfolio — learning to build software with AI, understand the code, and ship with intention.* 🌟
