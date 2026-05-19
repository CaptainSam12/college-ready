---
layout: post
codemirror: true
title: Keyboard Input
description: Keyboard Input - CS111 Review
permalink: /k-i
---

| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |

---

# This code is found in Player.js which we use in our game to control our main character

```js
updateDirection() {       
        // Single-key movement
        if (this.pressedKeys[this.keypress.up]) {
            this.direction = "up";
        } else if (this.pressedKeys[this.keypress.down]) {
            this.direction = "down";
        } else if (this.pressedKeys[this.keypress.right]) {
            this.direction = "right";
        } else if (this.pressedKeys[this.keypress.left]) {
            this.direction = "left";
        }

        // Multi-key movement
        if (this.pressedKeys[this.keypress.left] && this.pressedKeys[this.keypress.up]) {
            this.direction = "upLeft";
        } else if (this.pressedKeys[this.keypress.left] && this.pressedKeys[this.keypress.down]) {
            this.direction = "downLeft";
        } else if (this.pressedKeys[this.keypress.right] && this.pressedKeys[this.keypress.up]) {
            this.direction = "upRight";
        } else if (this.pressedKeys[this.keypress.right] && this.pressedKeys[this.keypress.down]) {
            this.direction = "downRight";
        }
    }
```

# This is how this works, using a simpler broken down version to explain. 
---

# 🎮 Keyboard Input  
Arrow keys, Space, and WASD controls using event listeners

## What Is Keyboard Input?
Keyboard input allows the player to control characters, menus, and actions in your game.  
In JavaScript, this is usually done using **event listeners** that detect when keys are pressed or released.

Common controls include:

- **Arrow Keys** → movement  
- **WASD** → alternative movement  
- **Space** → jump or action  

Keyboard input is essential for interactive gameplay.

---

## Event Listeners  
JavaScript listens for keyboard events using:

- `keydown` → when a key is pressed  
- `keyup` → when a key is released  

These events tell your game **what the player is doing right now**.

Example:
```js
window.addEventListener("keydown", (event) => {
    console.log(event.key);
});
```

This prints the key the player pressed.

---

## Tracking Movement Keys  
Games usually track whether a key is currently held down.

Example:
```js
const keys = {
    ArrowLeft: false,
    ArrowRight: false,
    ArrowUp: false,
    ArrowDown: false,
    w: false,
    a: false,
    s: false,
    d: false,
    " ": false // space
};
```

Then update these values when keys change:

```js
window.addEventListener("keydown", (e) => {
    if (keys.hasOwnProperty(e.key)) {
        keys[e.key] = true;
    }
});

window.addEventListener("keyup", (e) => {
    if (keys.hasOwnProperty(e.key)) {
        keys[e.key] = false;
    }
});
```

---

## Using Input in the Game Loop  
Inside your update method, you check which keys are active:

```js
update() {
    if (keys.ArrowLeft || keys.a) {
        this.x -= 3;
    }
    if (keys.ArrowRight || keys.d) {
        this.x += 3;
    }
    if (keys.ArrowUp || keys.w) {
        this.y -= 3;
    }
    if (keys.ArrowDown || keys.s) {
        this.y += 3;
    }
    if (keys[" "]) {
        this.jump();
    }
}
```

This allows:

- Arrow keys **or** WASD  
- Spacebar for jumping  
- Smooth, continuous movement  

---

## Example Code (Simple & Clear)

```js
class Player {
    constructor() {
        this.x = 100;
        this.y = 200;
        this.speed = 3;
    }

    update() {
        if (keys.ArrowLeft || keys.a) this.x -= this.speed;
        if (keys.ArrowRight || keys.d) this.x += this.speed;
        if (keys.ArrowUp || keys.w) this.y -= this.speed;
        if (keys.ArrowDown || keys.s) this.y += this.speed;

        if (keys[" "]) {
            this.jump();
        }
    }

    jump() {
        console.log("Jump!");
    }
}
```

This demonstrates:

- Arrow key movement  
- WASD movement  
- Spacebar action  
- Event listeners  
- Real‑time input handling  

---

## Why?
Keyboard input shows that you understand:

- How to use event listeners  
- How to track key states  
- How to integrate input into a game loop  
- How to map keys to movement and actions  
- How to create responsive, interactive gameplay  

Keyboard input is one of the most important skills in game programming.

---
