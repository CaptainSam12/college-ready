---
layout: post
codemirror: true
title: Constructor Chaining
description: Constructor Chaining - CS111 Review
permalink: /m-o
---

| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |

---

# 🧱 Constructor Chaining  
Using `super()` to connect constructors across a class hierarchy

## What Is Constructor Chaining?
**Constructor chaining** happens when a subclass calls the constructor of its parent class using `super()`.  
This ensures that all the properties defined in the parent class are properly initialized before the subclass adds its own.

In other words:

- The **base class** sets up the shared data  
- The **subclass** extends that setup with its own data  
- `super()` connects the two  

Without `super()`, the subclass would not inherit the parent’s initialization.

---

## Why Use `super()`?
`super()` allows you to:

- Reuse the parent class’s constructor logic  
- Avoid rewriting the same initialization code  
- Ensure all inherited properties are set correctly  
- Build clean, layered class hierarchies  

It’s required in JavaScript when a subclass has its own constructor.

---

## Example Hierarchy  
```
GameObject → Character → Player
```

Each level adds more information.

---

## Example Code (Simple & Clear)

```js
// Level 1: Base class
class GameObject {
    constructor(x, y) {
        this.x = x;
        this.y = y;
    }
}

// Level 2: Character extends GameObject
class Character extends GameObject {
    constructor(x, y, health) {
        super(x, y);     // calls GameObject constructor
        this.health = health;
    }
}

// Level 3: Player extends Character
class Player extends Character {
    constructor(x, y, health, name) {
        super(x, y, health);  // calls Character constructor
        this.name = name;
    }
}
```

### What’s happening?

- `Player` calls `super(x, y, health)`  
- That triggers the `Character` constructor  
- `Character` calls `super(x, y)`  
- That triggers the `GameObject` constructor  

This forms a **constructor chain** from most specific → most general.

---

## Why Teachers Assign This
Constructor chaining shows that you understand:

- How inheritance works under the hood  
- How to properly initialize subclasses  
- How to use `super()` to reuse parent logic  
- How to build multi‑level class hierarchies  
- How to structure game objects cleanly  

It’s a core skill in object‑oriented programming.

---

## Small Example (Easy to Read)

```js
const p = new Player(100, 200, 150, "Ironhook");
console.log(p);
```

This creates a fully initialized object using all three constructors in the chain.

---