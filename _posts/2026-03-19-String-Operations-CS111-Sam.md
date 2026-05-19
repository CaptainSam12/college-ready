---
layout: post
codemirror: true
title: String Operations
description: String Operations - CS111 Review
permalink: /String-Operations
---
| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |

---

# 🔤 String Operations  
Path concatenation, text display, and working with text in games

## What Are String Operations?
A **string** is text in programming — anything inside quotes:

```js
"Hello"
"player.png"
"Level 1 Complete!"
```

**String operations** are actions you perform on text, such as:

- Combining strings  
- Formatting text  
- Displaying text on screen  
- Building file paths  
- Creating messages for the player  

Strings are essential for UI, debugging, file loading, and game logic.

---

## Path Concatenation  
Games often need to load assets like:

- Images  
- Sounds  
- Level files  
- Animations  

These files are usually stored in folders, so you build paths using strings.

### Example:
```js
const basePath = "assets/images/";
const fileName = "pirate.png";

const fullPath = basePath + fileName;
```

`fullPath` becomes:

```
"assets/images/pirate.png"
```

This is **path concatenation** — combining strings to form a complete file path.

### Why it matters:
- Lets you organize assets cleanly  
- Allows dynamic loading (e.g., load a sprite based on character type)  
- Avoids hard‑coding every path manually  

---

## Text Display  
Strings are also used to show information to the player.

Examples:

- Score  
- Health  
- Dialogue  
- Notifications  
- Debug messages  

### Example:
```js
const scoreText = "Score: " + this.score;
```

Or using template strings:

```js
const scoreText = `Score: ${this.score}`;
```

Template strings are cleaner and easier to read.

---

## Example Code (Simple & Clear)

```js
class Player {
    constructor(name) {
        this.name = name;
        this.score = 0;
    }

    getSpritePath() {
        const base = "assets/sprites/";
        return base + this.name.toLowerCase() + ".png";
    }

    getScoreText() {
        return `Score: ${this.score}`;
    }
}

const p = new Player("Ironhook");

console.log(p.getSpritePath());  // "assets/sprites/ironhook.png"
console.log(p.getScoreText());   // "Score: 0"
```

This demonstrates:

- Path concatenation  
- Text display  
- Template strings  
- Using strings inside class methods  

---

## Why Teachers Assign This
String operations show that you understand:

- How to build file paths dynamically  
- How to format text for UI  
- How to combine variables with text  
- How to use template strings  
- How to integrate text into game logic  

Strings are everywhere in game development — menus, HUDs, dialogue, debugging, and asset loading all rely on them.

---
<div style="display: flex; flex-wrap: wrap; gap: 10px; justify-content: center;">
    <a href="http://captainsam12.opencodingsociety.com/Boolean-Expressions" style="text-decoration: none;">
        <div style="background-color: #59ff4d; color: black; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
            Boolean Expressions
        </div>
    </a>
</div>
---
