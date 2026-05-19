---
layout: post
codemirror: true
title: Canvas Rendering
description: Canvas Rendering - CS111 Review
permalink: /canvas-rendering
---

| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |

---

# 🖼️ Canvas Rendering  
Draw sprites, backgrounds, and platforms using the Canvas API

## What Is Canvas Rendering?
The **HTML5 Canvas API** allows your game to draw graphics directly onto the screen.  
It’s used for:

- Sprites (characters, enemies, items)  
- Backgrounds  
- Platforms and terrain  
- UI elements  
- Animations  

Canvas gives you pixel‑level control over your game’s visuals.

---

## Setting Up the Canvas
You start with a `<canvas>` element in your HTML:

```html
<canvas id="game" width="640" height="360"></canvas>
```

Then get the drawing context in JavaScript:

```js
const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");
```

`ctx` is the object you use to draw everything.

---

## Drawing Backgrounds  
Backgrounds are usually large images drawn at position `(0, 0)`.

```js
const bg = new Image();
bg.src = "assets/backgrounds/level1.png";

ctx.drawImage(bg, 0, 0);
```

This draws the background across the entire canvas.

---

## Drawing Sprites  
Sprites are images representing characters or objects.

```js
const sprite = new Image();
sprite.src = "assets/sprites/player.png";

ctx.drawImage(sprite, this.x, this.y);
```

You can draw:

- Players  
- Enemies  
- Items  
- Projectiles  

Sprites can also be animated using sprite sheets.

---

## Drawing Platforms (Rectangles)  
Platforms are often simple shapes drawn with Canvas primitives:

```js
ctx.fillStyle = "#654321";
ctx.fillRect(this.x, this.y, this.width, this.height);
```

This draws a solid rectangle — perfect for:

- Ground  
- Walls  
- Ledges  
- Obstacles  

---

## Example: Rendering Inside a GameObject

```js
class GameObject {
    constructor(x, y, width, height, spritePath) {
        this.x = x;
        this.y = y;
        this.width = width;
        this.height = height;

        this.sprite = new Image();
        this.sprite.src = spritePath;
    }

    draw(ctx) {
        ctx.drawImage(this.sprite, this.x, this.y, this.width, this.height);
    }
}
```

This allows any object to draw itself using a sprite.

---

## Example: Rendering a Platform

```js
class Platform {
    constructor(x, y, width, height) {
        this.x = x;
        this.y = y;
        this.width = width;
        this.height = height;
    }

    draw(ctx) {
        ctx.fillStyle = "#238636";
        ctx.fillRect(this.x, this.y, this.width, this.height);
    }
}
```

This uses simple shapes instead of images.

---

## Why?
Canvas rendering shows that you understand:

- How to draw images and shapes  
- How to use the Canvas API  
- How to render game objects each frame  
- How to separate logic (`update`) from visuals (`draw`)  
- How to build a visual game loop  

Rendering is one of the core pillars of game development.

---
