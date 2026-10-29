# 💣 Project 07 — Modern Multi-Difficulty Minesweeper

Welcome to the seventh project in my **AI Engineering Journey**! 🚀

A polished, responsive **Minesweeper** game built with pure HTML5, CSS3, and Vanilla JavaScript. It combines the classic rules with a modern arcade look: tactile cells, glowing counters, smooth reveal animations, first-click safety, and persistent best times for every difficulty.

Built with **Spec-Driven Development (SDD)** and an **OpenCode** AI coding agent.

---

## ✨ Features

- 🎚️ **Three difficulty modes** — Beginner, Intermediate, and Expert.
- 🛡️ **First-click safety** — mines are generated *after* the first reveal, excluding the clicked cell and its eight neighbours.
- 🌊 **Recursive flood fill** — opening a zero-neighbour cell cascades through the connected safe area.
- 🚩 **Flagging system** — right-click, long-press on touch, or use the Flag Mode toggle.
- 🔢 **Live mine counter** — remaining unflagged mines, with a negative over-flag warning.
- ⏱️ **Arcade dashboard** — timer, animated status face, difficulty readout, and best time.
- 🏆 **Persistent best times** — saved per difficulty in `localStorage`.
- 💥 **Clean win/loss states** — mines revealed on loss, fatal cell highlighted, wrong flags marked; all mines flagged on victory.
- ⌨️ **Keyboard support** — arrow keys navigate the grid and `F` flags the focused cell.
- 📱 **Responsive layout** — the board scales to the viewport; Expert mode scrolls horizontally on small screens.
- ♿ **Accessible touches** — focus outlines, ARIA labels, live status announcements, and reduced-motion support.
- ⚡ **Zero dependencies** — no frameworks, build tools, or backend.

---

## 🎮 Difficulty Modes

| Mode | Grid (columns × rows) | Mines | Vibe |
| --- | --- | --- | --- |
| 🟢 Beginner | 9 × 9 | 10 | Quick, forgiving warm-up |
| 🟡 Intermediate | 16 × 16 | 40 | The classic balanced challenge |
| 🔴 Expert | 30 × 16 | 99 | Wide, dense, high stakes |

Best times are tracked **separately for each mode**.

---

## 🗂️ Project Structure

```text
project-07-minesweeper/
├── index.html              # Semantic shell: hero, difficulty panel, dashboard, dynamic board
├── styles/
│   └── style.css           # Arcade theme, responsive grid, cell states, animations
├── js/
│   └── main.js             # Board matrix, first-click safety, recursion, timer, persistence
└── README.md               # Documentation and agent metadata
```

---

## 🚀 How to Run

1. Clone or download this repository.
2. Navigate to the `project-07-minesweeper` folder.
3. Open `index.html` directly in a modern browser (Chrome, Firefox, Edge, or Safari).
4. Optionally, serve it with **VS Code Live Server** or any static HTTP server.

No installation, package manager, or build step is required.

---

## 🕹️ How to Play

1. Pick a difficulty.
2. Reveal your first tile — it is guaranteed to be safe and will open a small starting area.
3. Use the numbers to deduce where the mines are:
   - `1` means one neighbouring mine.
   - `2` means two neighbouring mines, and so on.
4. Flag suspected mines to keep track of them.
5. Reveal every safe cell to win. Clicking a mine ends the game.

### Controls

| Action | Mouse / Keyboard | Touch |
| --- | --- | --- |
| Reveal a cell | Left click | Tap |
| Flag / unflag | Right click or `F` | Long-press |
| Switch tap behaviour | **Flag mode** toggle | **Flag mode** toggle |
| Move focus | Arrow keys | — |
| Restart | Click the face button | Tap the face button |
| Change difficulty | Difficulty buttons | Difficulty buttons |

The **face button** also shows the current mood: `😃` ready, `😮` holding a tile, `😎` victory, `💀` defeat.

---

## 🧠 Spec-Driven Development (SDD) Workflow

This project follows the same Spec-Driven Development loop used across the lab:

1. **Specification first** — `SPEC.md` defines the difficulty matrix, first-click safety, recursive reveal rules, flagging behaviour, dashboard states, persistence, and acceptance criteria *before* implementation.
2. **Contract-driven architecture** — the file structure and responsibilities are fixed by the spec: semantic HTML, a dedicated stylesheet, and one Vanilla JS engine.
3. **Implementation against the contract** — the board matrix, mine placement, flood fill, timer, and localStorage layer are built to satisfy each requirement.
4. **Validation** — the acceptance checklist is exercised against the spec: first-click safety, recursion, counter updates, win/loss transitions, and persistence.
5. **Documentation** — this README records how to run the game, the controls, and the agent configuration for traceability.

The goal is not just to generate code, but to make the requirements explicit, review the result against them, and keep the implementation understandable.

---

## 🤖 OpenCode AI Agent Metadata

Transparency matters when building with AI. Here is the agent setup used for this project:

- **Agent CLI Tool:** [OpenCode](https://opencode.ai)
- **AI Model:** `Big Pickle` *(OpenCode default reasoning model)*
- **Execution Mode:** `Build`
- **Workflow Methodology:** **Spec-Driven Development (SDD)**
- **Primary Input:** `SPEC.md` plus the repository's existing project conventions
- **Key Agent Capabilities Demonstrated:**
  - 📜 **Spec parsing** — translated the requirements into a concrete data model and acceptance checklist.
  - 🧠 **Algorithmic implementation** — first-click-safe mine generation, Fisher-Yates distribution, and recursive zero-cell flood fill.
  - ⚡ **State management** — clean ready → playing → won/lost transitions with timer and face-state synchronisation.
  - 💾 **Persistence** — per-difficulty best times with defensive `localStorage` handling.
  - 🎨 **UI engineering** — responsive CSS grid sizing, tactile cell states, and reduced-motion support.

---

## 🛠️ Tech Stack

- **HTML5** — semantic structure and accessible controls
- **CSS3** — custom properties, responsive grid, gradients, animations, `prefers-reduced-motion`
- **Vanilla JavaScript (ES6+)** — classes, recursion, event delegation, timers, `localStorage`

---

## 🌐 Live Demo

🔗 **Live Site:** [View Project 07 Live](https://nilmerosorio.github.io/My-AI-Engineering-Journey/project-07-minesweeper/)

---

## 📝 Notes

- Best times are stored under the key `minesweeper.bestTimes.v1` in `localStorage`.
- **Reset records** clears all saved best times after a confirmation prompt.
- Only best times are persisted; the current board state resets on reload.
- The game works fully offline after the page loads. The Google Fonts link is a progressive enhancement with local fallbacks.
- Expert mode may require horizontal scrolling on narrow phones to keep cells comfortably tappable.

---

*Part of my AI Engineering Portfolio — learning to build software with AI, understand the code, and ship with intention.* 🌟
