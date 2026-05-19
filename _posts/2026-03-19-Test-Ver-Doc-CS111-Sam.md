---
layout: post
codemirror: true
title: Testing Verification + Documentation
description: Testing Verification + Documentation - CS111 Review
permalink: /tvd
---

<div style="display: flex; flex-wrap: wrap; gap: 10px; justify-content: center;">
    <a href="http://captainsam12.opencodingsociety.com/MLD" style="text-decoration: none;">
        <div style="background-color: #ff7a7a; color: black; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
            Mini Lesson Documentation
        </div>
    </a>
</div>

Rest is below in this order:

- Code Documentation + Code Highlights
- Gameplay Testing
- Integration Testing
- API Error Handling



## **1. Code Documentation — JSDoc Comments and Code Highlights**

Writing clear documentation ensures that anyone reading your code (including you months later) can understand how each part works.  
Below is an example of how JSDoc is used in the engine.  
From `Character.js`:

```js
/**
 * Represents any active entity in the game world, such as the player or NPCs.
 *
 * @property {Object} position  - Contains x/y coordinates.
 * @property {Object} velocity  - Movement vector applied each frame.
 * @property {number} size      - Render size of the entity.
 * @method draw     - Renders the entity on the canvas.
 * @method update   - Applies physics and updates position.
 * @method destroy  - Removes the entity from the game environment.
 */
class Character extends GameObject {
    /**
     * @param {Object|null} spriteInfo - Optional sprite configuration.
     * @param {Object|null} env        - Reference to the game environment.
     */
    constructor(spriteInfo = null, env = null) { ... }
}
```

From `Player.js`:

```js
/**
 * Handles key release events and updates movement state accordingly.
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

**Goal:** Maintain at least **10% comment density** across your code.

---

### **JSDoc Practice Task**

```js
%%js
/**
 * ScoreBoard keeps track of the player's current score and their personal record.
 *
 * @property {number} current   - Score for the active run.
 * @property {number} record    - Highest score achieved.
 * @property {string} username  - Player's display name.
 */
class ScoreBoard {

    /**
     * @param {string} username - Name shown on the leaderboard.
     */
    constructor(username) {
        this.username = username;
        this.current = 0;
        this.record = 0;
    }

    /**
     * Add points to the current score.
     *
     * @param {number} value - Amount of points to add.
     * @returns {number} Updated score.
     */
    add(value) {
        if (value > 0) this.current += value;
        if (this.current > this.record) this.record = this.current;
        return this.current;
    }

    /**
     * Reset the current score back to zero.
     *
     * @returns {void}
     */
    reset() {
        this.current = 0;
    }

    /**
     * Returns a formatted summary string.
     *
     * @returns {string} Summary of current and record scores.
     */
    summary() {
        return `${this.username} — Current: ${this.current}, Record: ${this.record}`;
    }
}

const sb = new ScoreBoard("Berry");
sb.add(100);
sb.add(250);
console.log(sb.summary());
sb.reset();
sb.add(50);
console.log(sb.summary());
```

---

## **2. Gameplay Testing — Level & Collision Verification**

Manual testing checklist for verifying core gameplay:

| Test | What to check | Expected behavior |
|------|---------------|------------------|
| Player movement | Arrow keys + WASD | Moves correctly, stops at edges |
| Jumping | Press W | Smooth upward motion + gravity fall |
| Coin pickup | Touch coin | Coin disappears, score increases |
| Enemy collision | Shark touches player | Explosion + level restart |
| Level completion | Reach goal | Next level loads |
| Boundary check | Move to edges | Player stays inside canvas |

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

## **3. Integration Testing**

```js
// Test: POST a score, then GET leaderboard to confirm it saved.
async function testLeaderboardFlow() {
    const payload = { playerName: "TestUser", score: 9999 };

    // POST request
    const post = await fetch(`${javaURI}/api/scores`, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        credentials: "include",
        body: JSON.stringify(payload)
    });
    console.log("POST status:", post.status);

    // GET request
    const get = await fetch(`${javaURI}/api/scores`, {
        credentials: "include"
    });
    const list = await get.json();

    const exists = list.some(
        entry => entry.playerName === "TestUser" && entry.score === 9999
    );

    console.log("Score saved:", exists);
}
```

---

## **4. API Error Handling**

```js
fetch(options.URL, requestOptions)
    .then(res => {
        if (!res.ok) {
            const msg = `Login failed — status ${res.status}`;
            console.log(msg);
            document.getElementById(options.message).textContent = msg;
            return;
        }
        options.callback();
    })
    .catch(err => {
        console.log("Network/CORS issue:", err);
        document.getElementById(options.message).textContent =
            "Network or CORS issue: " + err;
    });
```

---

### **Error Handling Test**

```js
%%js
async function fetchSafe(url, label) {
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
await fetchSafe(
    "https://official-joke-api.appspot.com/jokes/does_not_exist",
    "Bad endpoint"
);

// Test 2 — valid URL
await fetchSafe(
    "https://official-joke-api.appspot.com/random_joke",
    "Good endpoint"
);
```

---

## **Summary**

| Area | What to do | Tool |
|------|-------------|------|
| Documentation | Add JSDoc to all classes/methods | Code review |
| Gameplay testing | Verify movement, collisions, transitions | Manual playtest |
| Integration testing | POST → GET leaderboard | Network tab |
| API error handling | try/catch + response.ok checks | Code review |

---
