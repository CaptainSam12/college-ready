---
layout: post
codemirror: true
title: Boolean Expressions
description: Boolean Expressions - CS111 Review
permalink: /Boolean-Expressions
---
| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |

---

# 🔘 Boolean Expressions  
Compound conditions in game logic

## What Are Boolean Expressions?
A **Boolean expression** is anything that evaluates to either:

- **true**  
- **false**

Games rely on Boolean logic constantly — every decision the game makes is based on conditions:

- *Is the player touching the ground?*  
- *Is the enemy close enough to attack?*  
- *Is the score high enough to unlock the next level?*  

Boolean expressions are the foundation of all branching game logic.

---

## Simple Boolean Conditions
A simple condition checks **one thing**:

```js
if (player.y > groundLevel) { ... }
if (health <= 0) { ... }
if (keyPressed === "Space") { ... }
```

These are the building blocks of more complex logic.

---

## Compound Conditions  
Compound conditions combine multiple checks using:

- **&&** (AND)  
- **||** (OR)  
- **!** (NOT)

These allow your game to make smarter decisions.

---

## AND (&&)  
All conditions must be **true**.

Example: Player can jump only if they are **on the ground AND not stunned**.

```js
if (player.onGround && !player.isStunned) {
    player.jump();
}
```

---

## OR (||)  
At least **one** condition must be true.

Example: Player can move left using **A OR Left Arrow**.

```js
if (keys["ArrowLeft"] || keys["a"]) {
    player.x -= player.speed;
}
```

---

## NOT (!)  
Flips true → false or false → true.

Example: Enemy moves only when **not** frozen.

```js
if (!enemy.isFrozen) {
    enemy.updateMovement();
}
```

---

## Combining Multiple Conditions  
Game logic often needs several checks at once.

Example: Player takes damage only if:

- They collide with an enemy  
- AND they are not invincible  
- AND the enemy is active  

```js
if (player.collidesWith(enemy) &&
    !player.invincible &&
    enemy.active) {
    player.takeDamage(10);
}
```

This is a realistic compound condition used in many engines.

---

## Example: Platformer Movement Logic

```js
// Player can jump if:
// 1. W or Space is pressed
// 2. AND the player is on the ground
// 3. AND the player is not sliding

if ((keys["w"] || keys[" "]) &&
    player.onGround &&
    !player.isSliding) {
    player.jump();
}
```

This shows how Boolean expressions control gameplay flow.

---

## Example: Level Completion Logic

```js
if (player.x >= goal.x &&
    player.y <= goal.y + 20 &&
    score >= requiredScore) {
    level.complete();
}
```

The level only completes when **all** conditions are satisfied.

---

## Why?
Boolean expressions demonstrate that you understand:

- How to combine multiple conditions  
- How to control game behavior with logic  
- How to write readable, structured decision code  
- How to prevent bugs by checking all required states  
- How real game engines make decisions every frame  

Boolean logic is the backbone of gameplay programming.

---
<div style="display: flex; flex-wrap: wrap; gap: 10px; justify-content: space-between;">
    <a href="http://captainsam12.opencodingsociety.com/MainHub" style="text-decoration: none;">
        <div style="background-color: #f91d1d; color: black; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
            Back To MainHub
        </div>
    </a>
</div>
---