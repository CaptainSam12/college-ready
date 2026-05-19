---
layout: post
codemirror: true
title: Writing Classes
description: Writing Classes - CS111 Review
permalink: /m-p
---

| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |



---

# ⚙️ Methods & Parameters  
Understanding how functions inside classes receive information

## What Are Methods?
A **method** is a function that belongs to a class.  
It describes something the object *can do*.

Example:
```js
class Pirate {
    attack(target) {
        // method logic
    }
}
```

Here, `attack` is a **method** of the `Pirate` class.

---

## What Are Parameters?
**Parameters** are the input values a method needs in order to work.

They allow your method to react differently depending on what is passed in.

Example:
```js
attack(target)
```

- `target` is a **parameter**
- It tells the method *who* the pirate is attacking

Without parameters, methods would always do the same thing.

---

## Why Use Methods With Parameters?
Parameters let you:

- Pass information into a method  
- Control behavior dynamically  
- Handle interactions between objects  
- Reuse the same method for many situations  

This is essential in games, simulations, and object‑oriented programming.

---

## Example: collisionHandler(other, direction)
A common pattern in games is a method that handles collisions.

```js
class Player {
    collisionHandler(other, direction) {
        // `other` = the object we collided with
        // `direction` = where the collision came from
    }
}
```

### What the parameters mean:
- **other** → the object the player bumped into  
- **direction** → `"left"`, `"right"`, `"up"`, `"down"`  

This lets the method respond differently depending on the situation.

---

## Why?

Using methods with parameters shows that you understand:

- How objects interact  
- How to pass data between objects  
- How to design flexible, reusable code  
- How to structure game logic cleanly  

It’s a core skill in object‑oriented programming.

