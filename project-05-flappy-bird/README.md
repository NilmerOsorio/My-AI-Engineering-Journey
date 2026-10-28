# 🐦 Project 05: Modern Flappy Bird Arcade Game

Welcome to the fifth project in my **AI Agent Engineering Journey**! 🚀

A sleek, responsive **Flappy Bird** web arcade game built with pure HTML5 Canvas, CSS3, and Vanilla JavaScript. Features smooth physics simulation, procedurally generated obstacles, persistent high scores, and a modern neon arcade UI. Architected using **Spec-Driven Development (SDD)** with an autonomous AI coding agent.

---

## 🤖 AI Agent & Workflow Metadata

Transparency is key when building with AI! Here are the details of the agent configuration used to create this project:

- **Agent CLI Tool:** [OpenCode](https://opencode.ai) (`v2.1.4`)
- **AI Model:** `Big Pickle` *(OpenCode Default Reasoning Model)*
- **Execution Mode:** `Build`
- **Workflow Methodology:** **Spec-Driven Development (SDD)**
- **Key Agent Capabilities Demonstrated:**
  - 📜 **Spec-Driven Execution:** Parsed physics requirements, collision mechanics, and game state management directly from `SPEC.md`.
  - 🎮 **Game Physics Implementation:** Built a custom gravity/impulse physics engine with smooth 60fps game loop using `requestAnimationFrame`.
  - 🎨 **Canvas Rendering:** Implemented procedural graphics for bird, pipes, ground, and UI overlays with gradients and effects.
  - 💾 **State Persistence:** Integrated `localStorage` for high score tracking across sessions.
  - 🎯 **Collision Detection:** Engineered robust axis-aligned bounding box collision detection for all game elements.

---

## ✨ Features

- 🐦 **Customizable Bird Selection:** Choose from 4 unique bird characters on the start screen before playing - Crimson Flame, Cyber Neon Bluejay, Arctic Penguin, or Emoji Sprite Bird.
- 🕹️ **Classic Flappy Bird Gameplay:** Gravity-based flight with satisfying flap mechanics.
- 🎮 **Multi-Input Controls:** Support for mouse click, screen tap (mobile), Spacebar, and Arrow Up keys.
- 🏗️ **Procedural Obstacles:** Dynamically generated pipes with randomized vertical gap positions.
- 💥 **Precise Collision Detection:** Bounding-box collision for ground, ceiling, and pipe obstacles (consistent across all bird types).
- 🏆 **Score Tracking:** Live score counter that increments when passing pipe pairs.
- 💾 **High Score Persistence:** Best score saved to browser `localStorage`.
- 🎨 **Modern Neon UI:** Cyberpunk-inspired dark theme with glowing accents and smooth animations.
- 📱 **Responsive Design:** Optimized for desktop and mobile browsers.
- ⚡ **Zero Dependencies:** Pure Vanilla JS, CSS3, and HTML5 Canvas—no frameworks or libraries.

---

## 📁 Project Architecture

```text
project-05-flappy-bird/
├── index.html          # Main container with Canvas, HUD, and overlay screens
├── styles/
│   └── style.css       # Neon arcade styling, animations, and responsive design
├── js/
│   └── main.js         # Game engine: physics, collision, pipe generation, state machine
└── README.md           # Project documentation & AI agent workflow metadata
```

---

## 🕹️ How to Play & Run

### 🚀 Running Locally

1. Clone or download this repository.
2. Navigate to the `project-05-flappy-bird` folder.
3. Open `index.html` directly in your web browser, or run using VS Code Live Server for best results.
4. Click "START GAME" or press any control to begin!

### 🎮 Game Rules

1. **Select Character:** Choose your favorite bird from 4 options on the start screen (Crimson Flame, Cyber Neon, Arctic Penguin, or Emoji Bird).
2. **Start:** Click the "START GAME" button or tap/click/press keys on the start screen.
3. **Fly:** Tap, click, or press Spacebar/Arrow Up to flap and gain altitude.
4. **Navigate:** Guide your selected bird through the gaps between pipes without hitting them.
5. **Avoid Obstacles:** Don't crash into pipes, the ground, or go above the ceiling.
6. **Score:** Earn 1 point for each pair of pipes successfully passed.
7. **Game Over:** Collision triggers game over - see your score and beat your best!
8. **Restart:** Click "PLAY AGAIN" to start a new round with your selected bird.

---

## 🌐 Live Demo

🔗 **Live Site:** [View Project 05 Live](https://nilmerosorio.github.io/My-AI-Engineering-Journey/project-05-flappy-bird/)

---

## 💡 Key Learnings & Agent Insights

- **Spec-Driven Game Development:** Using a detailed `SPEC.md` enabled the agent to implement complex game mechanics (physics, collision, state machine) cohesively.
- **Canvas Mastery:** Built custom 2D rendering with gradients, rotations, emoji sprites, and procedural shapes without image assets.
- **Dynamic Character System:** Implemented flexible bird rendering system supporting multiple visual styles while maintaining consistent physics.
- **Game Loop Architecture:** Implemented proper update/draw cycle with `requestAnimationFrame` for smooth performance.
- **State Machine Design:** Clean separation between Start, Playing, and Game Over states with proper UI transitions.
- **Physics Simulation:** Realistic gravity and impulse mechanics create engaging, skill-based gameplay.
- **Performance Considerations:** Pipe cleanup and efficient collision detection maintain smooth framerates.

---

*Part of my AI Engineering Portfolio — documenting my transition to agentic software development.* 🌟
