# 🧠 Project 02 - Interactive General Knowledge Quiz & Dashboard

> 🌐 **Live Demo:** [View Live Site](https://nilmerosorio.github.io/My-AI-Engineering-Journey/project-02-quiz-app/)

A sleek, responsive single-page quiz application with real-time feedback, interactive score analytics, and customizable background music 🎧. Built with pure HTML5, CSS3, and Vanilla JavaScript.

---

## ✨ Features

- ❓ **10-Question General Knowledge Quiz:** Covers history, science, geography, tech, and astronomy.
- 📊 **Dynamic Results Dashboard:** Calculates accuracy percentage, correct vs. incorrect breakdown, and detailed answer summaries.
- 🎵 **Background Music Toggle:** Integrated local player for Bensound's *"Hey! (Happy Cheerful)"* with play/pause controls.
- 📱 **Modern Glassmorphism UI:** Responsive dark gradient design with smooth animations and progress tracking.
- ⚡ **Zero Dependencies:** Client-side state management without heavy external libraries.

---

## 🤖 AI Agent & Spec-Driven Development (SDD)

This project was built following **Spec-Driven Development (SDD)** principles in collaboration with an autonomous AI coding agent.

- **AI Agent CLI:** [OpenCode](https://opencode.ai) (`v2.1.4`)
- **Model:** `Big Pickle` *(OpenCode Default Reasoning Model)*
- **SDD Workflow:**
  1. 📄 **Specification (`SPEC.md` / `questions.md`):** Defined user stories, non-goals, non-functional requirements, and the 10-question bank upfront.
  2. 🏗️ **Autonomous Scaffolding:** Guided OpenCode to build the modular file architecture (`styles/`, `js/`, `assets/`).
  3. 🛠️ **Iterative Refinement:** Addressed web browser autoplay restrictions by hosting local `.mp3` assets and explicit playback handlers.

---

## 📂 Project Structure

```text
project-02-quiz-app/
├── index.html          # Quiz container & results dashboard views
├── assets/
│   └── bensound-hey.mp3# Local audio track
├── styles/
│   └── style.css       # UI styling, dark gradients, card grid layout
├── js/
│   └── main.js         # State machine, score calculator, audio controls
└── README.md           # Project documentation
```

---

## 🎧 Credits & Acknowledgments
- **Music:** [Hey! (Happy Cheerful) by Bensound](https://www.bensound.com/royalty-free-music/track/hey-happy-cheerful)
- **Typography:** [Inter Font](https://fonts.google.com/specimen/Inter) by Google Fonts.
- **Journey:** Part of the *My AI Engineering Journey* repository.
