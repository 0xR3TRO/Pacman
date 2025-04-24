# Pacman

> **Website created by [0xR3TR0](https://github.com/0xr3tro). All rights reserved.**

---

## 📖 Overview

A classic Pac-Man clone built with vanilla JavaScript, HTML5 Canvas and CSS. Eat all the pellets, avoid ghosts, and rack up your high score!

---

## ✨ Features

-   **Responsive Canvas**: 500×500px HTML5 canvas for smooth rendering
-   **Sprite Animations**: Frame-based Pac-Man and ghost sprites
-   **Classic Map**: 21×23 grid with walls, pellets and corridors
-   **AI Ghosts**: Ghosts chase you when in range; otherwise roam to corner targets
-   **Lives & Scoring**: Three lives, score counter, “Game Over” alert
-   **Keyboard Controls**: Arrow keys or WASD for movement
-   **Modular Code**: Separated into `game.js`, `pacman.js` and `ghost.js`

---

## 🚀 Getting Started

### Prerequisites

-   A modern browser (Chrome, Edge, Firefox, Safari…)
-   No build tools or servers required—just open `index.html`

### Installation

1. **Clone the repo**

    ```bash
    git clone https://github.com/0xR3TR0/pacman.git
    cd pacman
    ```

2. **Open** `index.html` in your browser
3. **Play** and enjoy!

---

## 📂 Project Structure

```
pacman/
├── index.html
├── Directories/
│   ├── style.css
│   ├── game.js
│   ├── pacman.js
│   └── ghost.js
├── Media & Images/
│   ├── animations.gif
│   └── ghost.png
└── README.md
```

-   **index.html** – Main HTML scaffold and `<canvas>` element
-   **style.css** – Centering, full-screen background, font settings
-   **game.js** – Initialization, game loop (`update()` & `draw()`), collision handling
-   **pacman.js** – `Pacman` class: movement, eating logic, sprite animation
-   **ghost.js** – `Ghost` class: AI pathfinding (BFS), range detection, sprite drawing
-   **Media & Images** – Sprite sheets for Pac-Man and ghosts

---

## 🔧 How It Works

### index.html

-   Defines a `<canvas id="canvas" width="500" height="500">` inside a centered container
-   Preloads two `<img>` elements for sprite sheets (hidden via CSS)
-   Hooks scripts in order: `ghost.js` → `pacman.js` → `game.js`

### style.css

```css
body {
    margin: 0;
    background: black;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}
#game-container {
    position: relative;
}
```

### game.js

-   **Constants & Globals**: `fps`, `oneBlockSize`, `map[][]`, `lives`, `score`, etc.
-   **`createRect()`**: Helper to draw walls and pellets
-   **`gameLoop()`**: Calls `update()` then `draw()` at `fps` intervals
-   **`update()`**:
    -   `pacman.moveProcess()` & `pacman.eat()`
    -   `updateGhosts()`
    -   Collision check → `onGhostCollision()`
-   **`draw()`**:
    -   Clears canvas, draws background
    -   Renders walls, pellets, ghosts, Pac-Man, score and lives

### pacman.js

```js
class Pacman {
    constructor(x, y, w, h, speed) {
        /* init position, size, speed, animation */
    }
    moveProcess() {
        /* try nextDirection, move, rollback if collision */
    }
    eat() {
        /* scan map for pellets, increment score */
    }
    draw() {
        /* translate & rotate sprite based on direction */
    }
    /* ...helper methods: getMapX/Y, collision checks, animation... */
}
```

-   **Movement**: Uses `direction` & `nextDirection`; prevents reversing into walls
-   **Eating**: Sets `map[i][j] = 3` when pellet consumed
-   **Animation**: Frame index cycles every 100 ms

### ghost.js

```js
class Ghost {
    constructor(x, y, w, h, speed, imgX, imgY, imgW, imgH, range) {
        /* init */
    }
    moveProcess() {
        /* choose target (Pac-Man or corner), BFS path, move */
    }
    isInRange() {
        /* Euclidean distance ≤ range */
    }
    calculateNewDirection(map, destX, destY) {
        /* BFS to find next move */
    }
    draw() {
        /* draw correct sprite frame */
    }
    /* ...helper methods: map coords, collision detection... */
}
```

-   **AI Behavior**:
    -   If Pac-Man is within `range`, chase him
    -   Otherwise cycle through 4 corner targets
    -   Recalculates path every 10 s or when in range
-   **Pathfinding**: Simple BFS on the grid, marks visited

---

## 🎮 Controls

-   **Left**: ← or `A`
-   **Up**: ↑ or `W`
-   **Right**: → or `D`
-   **Down**: ↓ or `S`

---

## ⚙️ Configuration

You can tweak key constants in `game.js`:

```js
const fps = 30; // Game speed
let lives = 3; // Starting lives
let ghostCount = 4; // Number of ghosts (max 4)
let oneBlockSize = 20; // Size of each grid cell
let wallInnerColor = "black"; // Wall inner color
```

To modify the map layout, edit the 2D `map` array (1 = wall, 2 = pellet, 0 = empty).

---

## 🤝 Contributing

1. Fork the repo
2. Create a feature branch (`git checkout -b feature/foo`)
3. Commit your changes (`git commit -m "Add foo"`)
4. Push to the branch (`git push origin feature/foo`)
5. Open a Pull Request

Please keep code modular and well-commented.

---

## 📄 License

© [0xR3TR0](https://github.com/0xr3tro). All rights reserved.  
This code is proprietary. Do **not** use or distribute without permission.

```

```
