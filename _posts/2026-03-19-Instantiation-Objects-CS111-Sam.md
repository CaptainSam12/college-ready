---
layout: post
codemirror: true
title: Instantiation & Objects
description: Instantiation & Objects - CS111 Review
permalink: /i-o
---

| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |

---

# 🧱 Instantiation & Objects  
Creating actual game objects inside your GameLevel configuration

## What Is Instantiation?
**Instantiation** means creating a real, usable object from a class.

A class is just a blueprint.  
Instantiation is the moment you *build* something from that blueprint.

Example:
```js
const player = new Player("Ironhook");
```

Here:

- `Player` is the class (the blueprint)
- `new Player(...)` **instantiates** a new object
- `player` is the actual object you can use in the game

---

## What Is an Object?
An **object** is the thing created from a class.

It has:

- **Properties** (data it stores)
- **Methods** (things it can do)

Example:
```js
player.name      // property
player.attack()  // method
```

Objects are the “living” pieces of your game world.

---

## Why Instantiation Matters in Games
Games rely on many objects:

- The player  
- Enemies  
- Platforms  
- Items  
- Hazards  
- Projectiles  
- NPCs  

Each one is created (instantiated) from a class.

Without instantiation, your game would have **no actual entities** — only blueprints.

---

## Instantiating Objects in a GameLevel
In many game engines or custom frameworks, a **GameLevel** has a configuration section where you create all the objects that should appear in that level.

Example:
```js
class GameLevel {
    constructor() {
        this.objects = [
            new Player(100, 200),
            new Enemy(300, 200),
            new Platform(0, 350, 600, 40)
        ];
    }
}
```

### What’s happening here?

- `new Player(...)` creates the player object  
- `new Enemy(...)` creates an enemy  
- `new Platform(...)` creates a platform  
- All of them are stored in `this.objects` so the game engine can update and draw them

This is **instantiation inside level configuration**.

---

## Why?
Understanding instantiation shows that you can:

- Build real objects from your classes  
- Populate a game world with entities  
- Organize objects inside a level or scene  
- Use constructors and parameters correctly  
- Structure your game logic cleanly  

It’s a core part of object‑oriented game development.

---

## Small Example (Simple & Clear)
```js
class Pirate {
    constructor(name, x, y) {
        this.name = name;
        this.x = x;
        this.y = y;
    }
}

class GameLevel {
    constructor() {
        this.objects = [
            new Pirate("Ironhook", 100, 200),
            new Pirate("Silentscar", 300, 200)
        ];
    }
}

const level1 = new GameLevel();
console.log(level1.objects);
```

This demonstrates:

- A class (`Pirate`)
- Instantiation (`new Pirate(...)`)
- Level configuration (`objects` array)
- A real level object (`level1`)

---
