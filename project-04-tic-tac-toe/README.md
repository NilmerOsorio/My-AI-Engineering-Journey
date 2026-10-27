# 🎮 Project 04: Modern Tic Tac Toe (PvP & PvC)

Welcome to the fourth project in my **AI Agent Engineering Journey**! 🚀

A sleek, responsive **Tic Tac Toe** web application built with pure HTML5, CSS3, and Vanilla JavaScript. Features a modern dark gradient theme with glowing neon accents, dynamic AI opponent logic, and smooth animations. Architected using **Spec-Driven Development (SDD)** with an autonomous AI coding agent.

---

## 🤖 AI Agent & Workflow Metadata

Transparency is key when building with AI! Here are the details of the agent configuration used to create this project:

* **Agent CLI Tool:** [OpenCode](https://opencode.ai) (`v2.1.4`)
- **AI Model:** `Big Pickle` *(OpenCode Default Reasoning Model)*
- **Execution Mode:** `Build`
- **Workflow Methodology:** **Spec-Driven Development (SDD)**
- **Key Agent Capabilities Demonstrated:**
  * 📜 **Spec-Driven Execution:** Parsed game rules, grid mechanics, and AI decision hierarchy directly from `SPEC.md`.
  * 🧠 **Strategic AI Logic:** Built a decision algorithm (Win ➡️ Block ➡️ Center ➡️ Corners ➡️ Edges) with realistic thinking delays.
  * ⚡ **State & Win Engine:** Implemented algorithms for score tracking, dynamic round resets, and win/tie checking across rows, columns, and diagonals.

---

## ✨ Features

- 👥 **Dual Game Modes:** Toggle seamlessly between **Player vs. Player (PvP)** and **Player vs. Computer (PvC)**.
- 🤖 **Smart AI Opponent:** Strategic computer logic that blocks win attempts, claims high-value cells, and plays to win.
- 📊 **Session Score Tracker:** Keeps live count of Wins for X, Wins for O/Computer, and Ties.
- 📱 **Modern Neon UI:** Cyberpunk-inspired dark gradient design with smooth cell pop animations and winning glows.
- ⚡ **Zero Dependencies:** Built with pure Vanilla JS, CSS3, and HTML5—no external frameworks required.

---

## 📁 Project Architecture

```text
project-04-tic-tac-toe/
├── index.html         # Main app container & interactive grid UI
├── styles/
│   └── style.css      # Dark gradient layout, neon glows, and cell animations
├── js/
│   └── main.js        # Game state engine, AI logic, and DOM interaction
└── README.md          # Project documentation & AI agent workflow metadata
```

---

## 🕹️ How to Play & Run

### 🚀 Running Locally
1. Clone or download this repository.
2. Navigate to the `project-04-tic-tac-toe` folder.
3. Open `index.html` directly in your web browser (or run using VS Code Live Server / HTTP server).

### 🎮 Game Rules
1. Select your desired game mode: **PvP** (local 2-player) or **PvC** (vs. Smart Computer AI).
2. Click on any empty cell on the 3x3 grid to place your mark.
3. Get 3 marks in a row (horizontal, vertical, or diagonal) to win!
4. Use **Reset Round** to clear the board or **Clear Scores** to reset the counters.

---

## 🌐 Live Demo

🔗 **Live Site:** [View Project 04 Live](https://nilmerosorio.github.io/My-AI-Engineering-Journey/project-04-tic-tac-toe/)

---

## 💡 Key Learnings & Agent Insights

- **Spec-Driven Consistency:** Using `SPEC.md` allowed OpenCode to build the exact state engine and UI styling in a single execution pass.
- **Handling Asynchronous AI Moves:** Incorporating `setTimeout` delays during the computer's turn prevents instantaneous moves and gives a natural human-like feeling.

---

*Part of my AI Engineering Portfolio — documenting my transition to agentic software development.* 🌟