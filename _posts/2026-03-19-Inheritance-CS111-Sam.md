---
layout: post
codemirror: true
title: Inheritance
description: Inheritance - CS111 Review
permalink: /inheritance
---

| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |

---

# 🧬 Inheritance (Basic)  
Building a class hierarchy with multiple levels

## What Is Inheritance?
**Inheritance** is an object‑oriented programming feature that lets one class build on top of another.

It allows you to create:

- A **base class** (general)
- One or more **subclasses** (more specific)
- Additional subclasses that extend those subclasses (even more specific)

This forms a **class hierarchy**.

---

## Why Use Inheritance?
Inheritance helps you:

- Avoid repeating code  
- Share common behavior across many classes  
- Organize your game objects logically  
- Build more complex systems from simple foundations  

It’s one of the core pillars of object‑oriented programming.

---

## Example Hierarchy  
A common pattern in games is:

```
GameObject → Character → Player
```

### **GameObject**  
The most general class.  
Everything in the game world is a GameObject.

It might define:

- Position  
- Size  
- Update logic  

### **Character** (inherits from GameObject)  
A more specific type of GameObject.

It might add:

- Health  
- Movement  
- Collision behavior  

### **Player** (inherits from Character)  
A specific type of Character controlled by the user.

It might add:

- Input handling  
- Inventory  
- Abilities  

---

## Example Code (Simple & Clear)

```js
// Base class: the most general object
class GameObject {
    constructor(x, y) {
        this.x = x;
        this.y = y;
    }
}

// Level 2: a character that exists in the world
class Character extends GameObject {
    constructor(x, y, health) {
        super(x, y);
        this.health = health;
    }
}

// Level 3: a specific type of character
class Player extends Character {
    constructor(x, y, health, name) {
        super(x, y, health);
        this.name = name;
    }
}
```

This demonstrates:

- **2+ levels of inheritance**
- A clear hierarchy  
- How each class becomes more specific  

---

## Why?
Creating a class hierarchy shows that you understand:

- How to structure code from general → specific  
- How to reuse behavior through inheritance  
- How to design scalable game systems  
- How to think in terms of object families  

It’s a foundational skill in object‑oriented programming and game development.


<div style="display: flex; flex-wrap: wrap; gap: 10px; justify-content: center;">
    <a href="http://captainsam12.opencodingsociety.com/m-o" style="text-decoration: none;">
        <div style="background-color: #8bfa9b; color: black; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
            Method Overriding
        </div>
    </a>
</div>
