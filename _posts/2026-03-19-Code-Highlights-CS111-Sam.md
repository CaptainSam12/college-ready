---
layout: post
codemirror: true
title: Testing Verification + Documentation
description: Testing Verification + Documentation - CS111 Review
permalink: /tvd
---


---

## 1. Code Documentation — JSDoc Usage

Clear documentation makes your code understandable and maintainable.  
Here’s an example of how JSDoc is used in the engine.  
From `Character.js`:

```js
/**
 * The Character class represents any moving entity in the game world,
 * including the player and AI-controlled creatures.
 *
 * @property {Object} position  - Current x/y coordinates.
 * @property {Object} velocity  - Current movement vector.
 * @property {number} size      - Render size of the object.
 * @method draw     - Renders the character.
 * @method update   - Applies physics and movement.
 * @method destroy  - Removes the character from the game.
 */
class Character extends GameObject {
    /**
     * @param {Object|null} spriteData - Optional sprite sheet information.
     * @param {Object|null} env        - Reference to the game environment.
     */
    constructor(spriteData = null, env = null) { ... }
}
```

And from `Player.js`:

```js
/**
 * Handles key release events and updates movement state.
 *
 * @param {Object} event - The keyup event containing keyCode.
 */
handleKeyUp({ keyCode }) {
    if (keyCode in this.pressedKeys) {
        delete this.pressedKeys[keyCode];
    }
    this.updateVelocity();
    this.updateDirection();
}
```

**Goal:** Maintain at least **10% comment density** across your codebase.

---

### JSDoc Practice Task (Rewritten)

```js
%%js
// Add JSDoc comments for each method in this class.

 /**
  * ScoreManager tracks the player's current score and personal best.
  *
  * @property {number} score      - Score for the active run.
  * @property {number} bestScore  - Highest score achieved.
  * @property {string} name       - Player's display name.
  */
class ScoreManager {

    /**
     * @param {string} name - Name to display on the leaderboard.
     */
    constructor(name) {
        this.name = name;
        this.score = 0;
        this.bestScore = 0;
    }

    /**
     * Increase the score by a given amount.
     *
     * @param {number} amount - Points to add.
     * @returns {number} Updated score value.
     */
    add(amount) {
        if (amount > 0) this.score += amount;
        if (this.score > this.bestScore) this.bestScore = this.score;
        return this.score;
    }

    /**
     * Reset the current score back to zero.
     *
     * @returns {void}
     */
    reset() {
        this.score = 0;
    }

    /**
     * Produce a formatted summary string for UI display.
     *
     * @returns {string} Summary of current and best scores.
     */
    summary() {
        return `${this.name} — Score: ${this.score}, Best: ${this.bestScore}`;
    }
}

const sm = new ScoreManager("Seonyoo");
sm.add(100);
sm.add(250);
console.log(sm.summary());
sm.reset();
sm.add(50);
console.log(sm.summary());
```

---

## 2. Gameplay Testing — Movement & Collision Checks

Manual testing checklist:

| Test | What to check | Expected behavior |
|------|---------------|------------------|
| Movement | WASD + arrows | Moves correctly, stops at edges |
| Jumping | Press W | Smooth rise + fall |
| Coin pickup | Touch coin | Coin disappears, score increases |
| Enemy hit | Shark touches player | Explosion + restart |
| Level finish | Reach goal | Loads next level |
| Boundaries | Move to edges | Player stays inside canvas |

Collision logic from `Shark.js`:

```js
handleCollisionEvent() {
    const player = this.gameEnv.gameObjects.find(obj => obj instanceof Player);
    this.velocity.x = 0;
    this.velocity.y = 0;

    this.explode(player.position.x, player.position.y);
    player.destroy();
    this.playerDestroyed = true;

    setTimeout(() => {
        this.gameEnv.gameControl.currentLevel.restart = true;
    }, 2000);
}
```

---

## 3. API Integration Testing

```js
// Test: POST a score, then GET the leaderboard to confirm persistence.
async function verifyLeaderboard() {
    const payload = { playerName: "TestUser", score: 9999 };

    // POST
    const postResponse = await fetch(`${javaURI}/api/scores`, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        credentials: "include",
        body: JSON.stringify(payload)
    });
    console.log("POST status:", postResponse.status);

    // GET
    const getResponse = await fetch(`${javaURI}/api/scores`, {
        credentials: "include"
    });
    const list = await getResponse.json();

    const exists = list.some(entry =>
        entry.playerName === "TestUser" && entry.score === 9999
    );

    console.log("Entry found:", exists);
}
```

---

## 4. API Error Handling

```js
fetch(options.URL, requestOptions)
    .then(res => {
        if (!res.ok) {
            const msg = `Login failed: ${res.status}`;
            console.log(msg);
            document.getElementById(options.message).textContent = msg;
            return;
        }
        options.callback();
    })
    .catch(err => {
        console.log("Network or CORS issue:", err);
        document.getElementById(options.message).textContent =
            "Network or CORS issue: " + err;
    });
```

---

### Error Handling Test (Rewritten)

```js
%%js
async function safeFetch(url, label) {
    try {
        const res = await fetch(url);

        if (!res.ok) {
            throw new Error(`HTTP ${res.status} — ${res.statusText}`);
        }

        const json = await res.json();
        console.log(`[${label}] OK:`, Object.keys(json));
        return json;

    } catch (err) {
        console.error(`[${label}] ERROR:`, err.message);
        return null;
    }
}

// Test 1 — invalid URL
await safeFetch(
    "https://official-joke-api.appspot.com/jokes/does_not_exist",
    "Bad endpoint"
);

// Test 2 — valid URL
await safeFetch(
    "https://official-joke-api.appspot.com/random_joke",
    "Good endpoint"
);
```

---

## Summary

| Area | Task | Tool |
|------|------|------|
| Documentation | Add JSDoc to all classes/methods | Code review |
| Gameplay testing | Verify movement, collisions, transitions | Manual playtest |
| Integration testing | POST → GET leaderboard | Network tab |
| Error handling | try/catch + response.ok checks | Code review |

---