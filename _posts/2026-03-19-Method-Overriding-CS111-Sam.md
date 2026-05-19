---
layout: post
codemirror: true
title: Method Overriding
description: Method Overriding - CS111 Review
permalink: /m-o
---

| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |

---

# 🔄 Method Overriding  
Changing or extending behavior inherited from a parent class

## What Is Method Overriding?
**Method overriding** happens when a subclass replaces a method it inherited from its parent class.

The subclass provides its **own version** of the method, usually because:

- It needs different behavior  
- It needs to add extra behavior  
- It needs to specialize how something works  

Overriding is a core part of object‑oriented programming because it lets you customize behavior while still using a shared base structure.

---

## Why Override Methods?
Overriding lets you:

- Change how an object updates  
- Change how it draws itself  
- Change how it handles collisions  
- Add new logic while still keeping the base behavior  
- Make subclasses behave differently without rewriting everything  

This is especially important in games, where different objects share the same basic structure but behave uniquely.

---

## Example: Base Methods to Override
Many game engines use common methods like:

- **`update()`** → runs every frame  
- **`draw()`** → renders the object  
- **`handleCollision(other)`** → reacts to collisions  

A base class might define simple versions of these, and subclasses override them to add custom behavior.

---

## Example Code (Simple & Clear)

```js
// Base class
class GameObject {
    update() {
        // default update behavior
    }

    draw() {
        // default drawing behavior
    }

    handleCollision(other) {
        // default collision behavior
    }
}

// Subclass that overrides methods
class Character extends GameObject {
    update() {
        // custom movement logic
    }

    draw() {
        // custom character rendering
    }

    handleCollision(other) {
        // character-specific collision response
    }
}

// More specific subclass
class Player extends Character {
    update() {
        super.update(); // keep Character behavior
        // add player input handling
    }

    handleCollision(other) {
        // player-specific collision logic
    }
}
```

This demonstrates:

- A **3‑level hierarchy**  
- Each level overriding methods  
- Use of `super.update()` to keep parent behavior  

---

## Why Teachers Assign This
Method overriding shows that you understand:

- How inheritance works in practice  
- How to customize behavior in subclasses  
- How to structure game logic cleanly  
- How to extend parent functionality without rewriting it  
- How to use `super` to build layered behavior  

It’s a key skill in object‑oriented programming and game development.

---
