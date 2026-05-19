---
layout: post
codemirror: true
title: GameEnv Configuration
description: GameEnv Configuration - CS111 Review
permalink: /GameEnv-Configuration
---

| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |

---

# ⚙️ GameEnv Configuration  
Setting canvas size, difficulty levels, and global game settings

## What Is Game Environment Configuration?
**Game environment configuration** refers to all the global settings that define how your game runs.  
These settings are usually created once at the start of the game and used everywhere else.

Common configuration tasks include:

- Setting the **canvas size**  
- Defining **difficulty levels**  
- Storing **game settings** (speed, gravity, volume, etc.)  
- Managing **global constants**  

This keeps your game organized, scalable, and easy to adjust.

---

## Canvas Size  
The canvas defines the visible area of your game.

You typically set it in HTML:

```html
<canvas id="game" width="800" height="450"></canvas>
```

Or dynamically in JavaScript:

```js
canvas.width = 800;
canvas.height = 450;
```

### Why it matters:
- Controls how much of the world the player sees  
- Affects performance  
- Determines layout and scaling  

---

## Difficulty Levels  
Difficulty settings adjust how challenging the game is.

Common difficulty variables:

- Enemy speed  
- Enemy spawn rate  
- Player health  
- Gravity strength  
- Platform spacing  
- Score multipliers  

Example configuration:

```js
const Difficulty = {
    easy: {
        enemySpeed: 2,
        gravity: 0.5,
        playerHealth: 200
    },
    normal: {
        enemySpeed: 3,
        gravity: 0.7,
        playerHealth: 150
    },
    hard: {
        enemySpeed: 5,
        gravity: 0.9,
        playerHealth: 100
    }
};
```

You can switch difficulty when starting a level:

```js
let currentDifficulty = Difficulty.normal;
```

---

## Game Settings  
Game settings define how the game behaves overall.

Examples:

- **Gravity**  
- **Friction**  
- **Max speed**  
- **Background theme**  
- **Volume**  
- **Tile size**  
- **Debug mode**  

Example:

```js
const GameSettings = {
    gravity: 0.7,
    friction: 0.85,
    tileSize: 32,
    debug: false
};
```

These values are used throughout the game:

```js
this.vy += GameSettings.gravity;
```

---

## Example: GameEnv Class (Simple & Clear)

```js
class GameEnv {
    constructor() {
        this.canvasWidth = 800;
        this.canvasHeight = 450;

        this.settings = {
            gravity: 0.7,
            friction: 0.85,
            tileSize: 32
        };

        this.difficulty = Difficulty.normal;
    }
}
```

This centralizes all environment configuration in one place.

---

## Why Teachers Assign This
Game environment configuration shows that you understand:

- How to organize global game settings  
- How to control difficulty and gameplay balance  
- How to manage canvas size and rendering space  
- How to structure your game for scalability  
- How to separate configuration from logic  

This is a key part of building clean, maintainable game architecture.

---
