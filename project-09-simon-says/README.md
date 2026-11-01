# 🎛️ Project 09 — Simon Says: Neon Memory Arcade

Welcome to the ninth project in my **AI Engineering Journey**! 🚀

A polished, browser-based **Simon Says** memory game wrapped in a retro neon arcade cabinet. The computer plays a growing sequence of colored flashes and synthesized tones; you repeat it exactly. One wrong step ends the run.

Built with **plain HTML, CSS, and Vanilla JavaScript**, with every sound generated live through the **Web Audio API** — no audio files, frameworks, or build tools.

Created with **Spec-Driven Development (SDD)** and an **OpenCode** AI coding agent.

---

## ✨ Features

- 🎛️ **Four-quadrant neon pad board** — Green, Red, Yellow, and Blue pads with glowing idle states, hover/focus feedback, and a bright press animation.
- 🎵 **Web Audio synthesis** — a unique musical pitch per pad (`E4`, `C4`, `G4`, `G3`), a warm envelope, plus an error buzz and success arpeggio.
- 🧠 **Async sequence playback** — the computer flashes a growing pattern in a dedicated **Watch** phase, then hands control to the **Your Turn** phase.
- ⚡ **Real-time validation** — every press is checked immediately; correct steps advance the progress pips, a wrong step ends the run.
- 🏆 **Persistent high score** — your best run is saved in `localStorage` and updated after every cleared round.
- 🖥️ **Three clean UI states** — Start overlay, a live Playing hub/status bar, and a Game Over card with your mistake and final stats.
- 🔁 **Session-safe timers** — a cancellation token prevents stale playback or flashes when you restart mid-run.
- 🎹 **Full keyboard support** — `G`/`R`/`Y`/`B`, number keys `1`–`4`, `Space`, and `M` for mute.
- ♿ **Accessible touches** — real buttons, `aria-keyshortcuts`, `aria-live` announcements, focus management, and reduced-motion support.
- 📱 **Responsive** — the square board scales cleanly from small phones to desktop with no horizontal overflow.

---

## 🕹️ How to Play

1. Press **Start Game**.
2. Watch the pads flash and listen to their tones — that is the pattern.
3. When the hub says **YOUR TURN**, click or tap the pads in the same order.
4. Clear the round to extend the sequence by one color.
5. Miss a step and the run ends. Beat your personal best!

### Score model

| Event | Effect |
| --- | --- |
| Complete a round | **+1 score**, sequence grows by one color |
| Wrong pad | Run ends immediately, error buzz, Game Over card |
| New best | Saved to `localStorage`, gold badge on Game Over |

### Controls

| Action | Keyboard | Pointer |
| --- | --- | --- |
| Green pad | `G` or `1` | Click / tap |
| Red pad | `R` or `2` | Click / tap |
| Yellow pad | `Y` or `3` | Click / tap |
| Blue pad | `B` or `4` | Click / tap |
| Start / retry | `Space` / `Enter` | Start / Play Again button |
| Mute / unmute | `M` | SFX button |

---

## 🗂️ Project Structure

```text
project-09-simon-says/
├── index.html              # Semantic cabinet, HUD, pad board, overlays
├── styles/
│   └── style.css           # Neon arcade theme, pad states, overlays, responsiveness
├── js/
│   └── main.js             # State machine, sequence engine, Web Audio, storage, events
└── README.md               # Run instructions, SDD workflow, agent metadata
```

---

## 🚀 How to Run

1. Clone or download this repository.
2. Navigate to the `project-09-simon-says` folder.
3. Open `index.html` directly in a modern browser (Chrome, Firefox, Edge, or Safari).
4. Or serve it with **VS Code Live Server** (or any static server) for the same result.

No installation, package manager, or build step is required.

> **Audio note:** browsers require a user gesture before audio can start. The game creates/resumes its `AudioContext` on the first **Start Game**, pad press, or unmute click.

---

## 🔊 Audio System

All audio is synthesized at runtime — there are no media files in this project.

| Sound | Trigger | Character |
| --- | --- | --- |
| Green `329.63 Hz` (E4) | Green pad lights | Triangle + sine octave, warm low-pass tone |
| Red `261.63 Hz` (C4) | Red pad lights | Same voice, lower pitch |
| Yellow `392.00 Hz` (G4) | Yellow pad lights | Same voice, brighter pitch |
| Blue `196.00 Hz` (G3) | Blue pad lights | Same voice, lowest pitch |
| Success arpeggio | Round cleared | `C5 → E5 → G5 → C6` rising chime |
| Error buzz | Wrong pad | Detuned sawtooth sweep falling to 68 Hz |

Implementation details:

- **Lazy context** — the `AudioContext` is only created after a user gesture, satisfying autoplay policies.
- **Shared master gain** — every voice routes through one gain node, so muting silences notes instantly and cleanly.
- **Envelope** — 14 ms attack, exponential decay, and a per-note low-pass filter for a soft arcade tone.
- **Graceful failure** — if the Web Audio API is unavailable or blocked, gameplay continues silently.

---

## 💾 Persistence

| Key | Value |
| --- | --- |
| `simon.highScore.v1` | Best number of completed rounds |
| `simon.muted.v1` | Sound preference (`true` / `false`) |

All reads and writes are wrapped in `try/catch`, so private-mode or blocked storage degrades gracefully to an in-memory best score.

---

## 🧠 Spec-Driven Development (SDD) Workflow

This project follows the same SDD loop used across the lab:

1. **Specification first** — `SPEC.md` fixes the scope: the pad layout, pitch table, async playback timing, step validation, scoring, persistence, overlay states, accessibility, and acceptance criteria.
2. **Contract-driven architecture** — file responsibilities are defined before implementation: semantic markup for the cabinet and overlays, one stylesheet for the neon theme, and one Vanilla JS engine.
3. **Implementation against the contract** — `main.js` implements an explicit `idle → watching → player → gameover` state machine with a cancellable async sequence player and a small Web Audio synth.
4. **Validation** — the acceptance checklist is exercised against the spec: start/restart transitions, locked input during playback, correct/incorrect press handling, round progression, high-score writes, mute persistence, keyboard control, and responsive layout.
5. **Documentation** — this README records how to run the game, the controls, the audio behaviour, and the agent configuration for traceability.

The goal is not just to generate code, but to make the requirements explicit, review the result against them, and keep the implementation understandable.

---

## 🤖 OpenCode AI Agent Metadata

Transparency matters when building with AI. Here is the agent setup used for this project:

- **Agent CLI Tool:** [OpenCode](https://opencode.ai)
- **AI Model:** `Big Pickle` *(OpenCode default reasoning model)*
- **Execution Mode:** `Build`
- **Workflow Methodology:** **Spec-Driven Development (SDD)**
- **Primary Input:** `SPEC.md`, the repository's project conventions, and the Project 08 arcade visual language
- **Key Agent Capabilities Demonstrated:**
  - 📜 **Spec parsing** — translated the requirements into a concrete state machine, timing model, data model, and acceptance checklist.
  - 🧠 **Async game engine** — session-token cancellation for sequence playback, round scheduling, and safe restarts.
  - 🎵 **Audio synthesis** — per-pad oscillator voices, envelopes, filters, success arpeggio, error sweep, and master-gain mute.
  - 🎨 **UI engineering** — neon pad states, animated overlays, responsive square board, scanlines, and reduced-motion support.
  - 💾 **Persistence** — defensive `localStorage` handling for the high score and muted preference.
  - ♿ **Accessibility** — real buttons, keyboard shortcuts, live announcements, focus management, and hidden-state handling.
  - ✅ **Validation** — syntax checks, spec-to-implementation review, and browser passes covering start, playback, correct/incorrect presses, restart, mute, and mobile layout.

---

## 🛠️ Tech Stack

- **HTML5** — semantic cabinet structure, button pads, overlay cards, live status region
- **CSS3** — custom properties, radial gradients, grid, neon glows, keyframe animations, responsive layout, `prefers-reduced-motion`
- **Vanilla JavaScript (ES6+)** — state machine, async/await timing, Web Audio API, `localStorage`, event delegation per pad

---

## 🌐 Live Demo

🔗 **Live Site:** [View Project 09 Live](https://nilmerosorio.github.io/My-AI-Engineering-Journey/project-09-simon-says/)

---

## 📝 Notes

- Only the high score and mute preference persist; the sequence resets on reload.
- The Google Fonts link is progressive enhancement — the game falls back to system fonts offline.
- The computer avoids three identical colors in a row so patterns stay readable.
- Restarting during playback invalidates the previous session token, so no stale flashes can appear.
- The central hub is the Playing overlay: it shows `WATCH`, `YOUR TURN`, `NICE!`, or `MISS` without blocking the pads.

---

*Part of my AI Engineering Portfolio — learning to build software with AI, understand the code, and ship with intention.* 🌟
