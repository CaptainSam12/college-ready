---
layout: post
codemirror: true
title: Writing Classes
description: Writing Classes - CS111 Review
permalink: /wc
---

| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |

---

# 🏴‍☠️ What Does “Writing Classes” Mean?

**Writing classes** means creating your own custom data types in code — blueprints that describe how something in your program should behave.

A class defines two main things:

1. **What the thing *is*** → its data (properties)  
2. **What the thing *does*** → its behavior (methods)

Once you write a class, you can create many objects from it.  
Each object follows the rules defined by the class.

---

## Why We Write Classes

Classes help you:

- Organize your code  
- Reuse logic  
- Model real things (characters, items, enemies, ships, etc.)  
- Build larger systems in a clean, scalable way  

They bundle **data + behavior** together so your program stays structured and easy to expand.

---

## Inheritance (The Key Part of Your Assignment)

Inheritance lets you create a **specialized version** of an existing class.

Example idea:

- **Base class:** Pirate → has name, health, attack()  
- **Subclass:** Buccaneer → a stronger pirate with heavy melee  
- **Subclass:** Sea Witch → a magic pirate with spells  

Subclasses inherit everything from the base class but can add:

- New abilities  
- Different stats  
- Custom behavior  

This avoids rewriting the same code over and over.

---

## A Simple Analogy

Think of a base class as:

> “All pirates have names, health, and can attack.”

Then a subclass says:

> “A Sea Witch is a pirate, but she also casts spells.”

Same foundation, different flavor.

---


Writing classes teaches you:

- How to structure programs  
- How to think in terms of objects  
- How to reuse and extend code  
- How to model real‑world or game‑world systems  

It’s one of the core skills in object‑oriented programming.

# How is this demonstrated in our game?

When we see lines like this:

class Player extends Character {

It shows how "Player" inherits traits from an already established class such as character. In our pirate themed game. we see:

class Rival-Pirate extends Skeleton-Guard

Skeleton-Guard is a level 1 enemy, which we can extend upon and make a level 2 enemy such as Rival-Pirate. We can now give Rival-Pirate more traits such as higher XP and more attack damage.

And you can play the game here:

<div style="display: flex; flex-wrap: wrap; gap: 10px; justify-content: center;">
    <a href="https://aashihegu1-stack.github.io/SAR/gamify/PirateMegaGame" style="text-decoration: none;">
        <div style="background-color: #ff002f; color: black; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
        Methods & Parameters
        </div>
    </a>
</div>