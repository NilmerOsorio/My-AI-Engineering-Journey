# Project 06 - Custom Asset Pixel Art Dino Runner

A sleek, responsive browser-based side-scrolling endless runner inspired by the classic Chrome Dino game. Built with pure HTML5 Canvas, Vanilla JavaScript, and CSS — using custom pixel art assets.

## 🎮 Features

- **Custom Pixel Art Assets**: Uses the provided `assets/images/` for the dinosaur, scrolling background, and obstacles.
- **Static Pixel Art Sprite**: Clean, static dinosaur sprite with vertical jump/fall physics only.
- **Smooth Physics**: Gravity, ground collision, and crisp jumps (Spacebar, Arrow Up, or touch/tap).
- **Endless Runner Gameplay**: Procedurally spawned obstacles with progressive speed scaling and increasing spawn frequency/difficulty acceleration over time applied continuously (even mid-jump), with minimum interval cap and max speed cap, reset on restart.
- **Precise Collision Detection**: Bounding-box collision detection triggers the Game Over state.
- **Score & High Score**: Live distance-based scoring with persistent high scores saved in `localStorage`.
- **Game States**: Clean transitions between Start Screen, Playing, and Game Over / Restart.
- **Retro-Modern UI**: Sleek arcade styling with responsive layout and pixel-perfect rendering.

## 🗂️ Project Structure

```
project-06-dino-runner/
├── index.html              # Canvas host with HUD and UI overlays
├── styles/
│   └── style.css           # Arcade styling, responsive design, overlays
├── assets/
│   └── images/             # Custom pixel art (background.jpg, dinosaur.png, obstacle.png)
├── js/
│   └── main.js             # Asset loading, animation, physics, collisions, scoring
└── README.md               # Project documentation
```

## 🚀 How to Run

1. Clone or download this repository.
2. Open `index.html` directly in a modern web browser (Chrome, Firefox, Edge, Safari), or run using VS Code Live Server for best results.
3. Press **Start Game** or hit **Space / Arrow Up / Tap** to jump and begin!
4. Try to beat your high score - it's saved automatically in your browser.

---

## 🌐 Live Demo

🔗 **Live Site:** [View Project 06 Live](https://nilmerosorio.github.io/My-AI-Engineering-Journey/project-06-dino-runner/)

---

## 🎯 Controls

- **Spacebar** / **Arrow Up** - Jump
- **Mouse Click / Touch Tap** - Jump
- **Start/Restart Buttons** - Navigate game states

## 🧠 Spec-Driven Development (SDD) Workflow

This project follows a Spec-Driven Development approach:

1. **Specification First** (`SPEC.md`): Define core intent, requirements, constraints, and acceptance criteria before writing code.
2. **Asset & Structure Alignment**: Work with pre-existing files and custom assets, ensuring implementation strictly follows the spec.
3. **Implementation**: Build features to match the contract - physics, animation, procedural generation, collisions, and persistence.
4. **Validation**: Test game states, controls, collisions, scoring, and localStorage behavior against the specification.
5. **Documentation**: Update README with usage instructions and workflow metadata for traceability.

## 🛠️ Tech Stack

- **HTML5** - Structure and Canvas element
- **CSS3** - Styling, animations, responsive design
- **Vanilla JavaScript (ES6+)** - Game loop, physics, logic, localStorage

## 📝 Notes

- All scores and state are managed locally (no backend required).
- Uses pure HTML5 Canvas with no external game engines.
- Optimized for pixel art with `image-rendering: pixelated`.
