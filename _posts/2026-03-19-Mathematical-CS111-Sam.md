---
layout: post
codemirror: true
title: Mathematical
description: Mathematical - CS111 Review
permalink: /mathematical
---
| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |

---

# 🧮 Mathematical  
Physics calculations (gravity, velocity, collision)

## Why Math Matters in Games
Math is the invisible engine behind almost every game mechanic.  
It controls how objects move, fall, bounce, collide, and react.

In game development, three of the most important physics concepts are:

- **Gravity**  
- **Velocity**  
- **Collision detection & response**

These allow your game world to feel dynamic, physical, and alive.

---

## Gravity  
Gravity is a constant downward force that accelerates objects over time.

Most games simulate gravity by increasing the object’s **vertical velocity** each frame:

```js
this.vy += this.gravity;
```

Then apply that velocity to position:

```js
this.y += this.vy;
```

### What this means:
- Objects fall faster the longer they fall  
- Jumping feels natural  
- Characters don’t float or stop mid‑air  

Gravity is usually a small number like `0.5` or `0.7`.

---

## Velocity  
Velocity is the **speed and direction** of an object’s movement.

Games typically track:

- `vx` → horizontal velocity  
- `vy` → vertical velocity  

Movement happens by adding velocity to position:

```js
this.x += this.vx;
this.y += this.vy;
```

Velocity can be changed by:

- Player input  
- Gravity  
- Collisions  
- Friction  
- Forces or impulses  

Velocity is the foundation of smooth, continuous motion.

---

## Collision  
Collision math determines:

- **When** two objects touch  
- **Where** they touch  
- **How** they should respond  

### Basic collision detection (AABB)
Axis‑Aligned Bounding Box (AABB) is the simplest method:

```js
if (this.x < other.x + other.width &&
    this.x + this.width > other.x &&
    this.y < other.y + other.height &&
    this.y + this.height > other.y) {
    // collision happened
}
```

### Collision response
Once a collision is detected, you adjust position or velocity:

- Stop falling when hitting the ground  
- Bounce off walls  
- Take damage  
- Trigger events  

Example:

```js
if (collidingFromTop) {
    this.vy = 0;       // stop falling
    this.y = other.y - this.height;
}
```

---

## Example Code (Simple & Clear)

```js
class GameObject {
    constructor(x, y) {
        this.x = x;
        this.y = y;
        this.vx = 0;
        this.vy = 0;
        this.gravity = 0.7;
    }

    update() {
        // apply gravity
        this.vy += this.gravity;

        // apply velocity
        this.x += this.vx;
        this.y += this.vy;
    }

    collidesWith(other) {
        return (
            this.x < other.x + other.width &&
            this.x + this.width > other.x &&
            this.y < other.y + other.height &&
            this.y + this.height > other.y
        );
    }
}
```

This demonstrates:

- Gravity  
- Velocity  
- Collision detection  
- Physics‑based movement  

---

## Why?
Physics calculations show that you understand:

- How movement works mathematically  
- How to simulate real‑world forces  
- How to detect and respond to collisions  
- How to update game objects each frame  
- How to combine math + code to create gameplay  

These are essential skills for building any interactive game.

---
<div style="display: flex; flex-wrap: wrap; gap: 10px; justify-content: center;">
    <a href="http://captainsam12.opencodingsociety.com/String-Operations" style="text-decoration: none;">
        <div style="background-color: #97e3ff; color: black; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
            String Operations
        </div>
    </a>
</div>

---