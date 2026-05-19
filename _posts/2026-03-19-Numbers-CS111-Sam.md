---
layout: post
codemirror: true
title: Numbers
description: Numbers - CS111 Review
permalink: /nn
---

| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |

---

# 🔢 Numbers  
Using numeric values to track position, velocity, and score in a game

## What Are Numbers Used For in Games?
Numbers are one of the most important data types in game development.  
They control almost everything that moves, updates, or changes over time.

Common uses include:

- **Position** (where an object is)
- **Velocity** (how fast it moves)
- **Score** (player progress)
- **Health**, **damage**, **timers**, **gravity**, etc.

Numbers make your game world dynamic and interactive.

---

## Position  
Position tells you **where** an object is in the game world.

Most games use:

- **x** → horizontal position  
- **y** → vertical position  

Example:
```js
this.x = 100;
this.y = 200;
```

Changing these values moves the object.

---

## Velocity  
Velocity tells you **how fast** and **in what direction** an object moves.

Example:
```js
this.vx = 3;   // move 3 units per frame horizontally
this.vy = -2;  // move upward 2 units per frame
```

Velocity is usually applied to position each frame:

```js
this.x += this.vx;
this.y += this.vy;
```

This is the foundation of movement in most games.

---

## Score Tracking  
Score is a number that represents the player’s progress or achievements.

Example:
```js
this.score = 0;
```

You update it as the player performs actions:

```js
this.score += 10;   // gained points
```

Score tracking is essential for:

- Level progression  
- Rewards  
- High scores  
- Win conditions  

---

## Example Code (Simple & Clear)

```js
class Player {
    constructor() {
        this.x = 100;     // position
        this.y = 200;
        this.vx = 3;      // velocity
        this.vy = 0;
        this.score = 0;   // score tracking
    }

    update() {
        // apply velocity to position
        this.x += this.vx;
        this.y += this.vy;
    }

    addScore(points) {
        this.score += points;
    }
}
```

This demonstrates:

- Numeric position  
- Numeric velocity  
- Numeric score  
- How numbers update over time  

---

## Why?
Working with numbers shows that you understand:

- How movement works  
- How to update game state each frame  
- How to track progress and gameplay events  
- How to use math to control game behavior  

Numbers are the backbone of almost every game mechanic.

---
