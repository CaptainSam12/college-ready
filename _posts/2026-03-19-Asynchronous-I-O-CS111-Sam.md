---
layout: post
codemirror: true
title: Asynchronous
description: Asynchronous - CS111 Review
permalink: /A-I-O
---

| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |


---

# ⏳ Asynchronous I/O  
Using async/await or Promises for API calls

## What Is Asynchronous I/O?
**Asynchronous I/O** allows your game to perform tasks (like API calls, loading files, or waiting for data) *without freezing the game loop*.  
Instead of stopping everything until the data arrives, JavaScript continues running and handles the result later.

This is essential for:

- Leaderboards  
- Saving/loading game data  
- Fetching assets  
- Online multiplayer  
- Cloud saves  

JavaScript handles async operations using:

- **Promises**  
- **async/await** (a cleaner way to write Promises)

---

## Why Games Need Async I/O
Games often need to:

- Send scores to a server  
- Load leaderboard data  
- Fetch player profiles  
- Download assets  
- Save progress  

These operations take time, so they must run **asynchronously** to avoid freezing gameplay.

---

## Promises (Basic Form)

A Promise represents a value that will be available **later**.

Example:

```js
fetch("https://example.com/api/leaderboard")
    .then(response => response.json())
    .then(data => console.log(data));
```

This means:

- Start the request  
- When it finishes, run the `.then()`  
- When the JSON is ready, run the next `.then()`  

---

## async/await (Cleaner Syntax)

`async/await` makes asynchronous code look like normal synchronous code.

Example:

```js
async function loadLeaderboard() {
    const response = await fetch("https://example.com/api/leaderboard");
    const data = await response.json();
    return data;
}
```

### What’s happening?

- `await` pauses *only inside this function*  
- The rest of the game continues running  
- When the data arrives, the function resumes  

This is the preferred modern way to write async code.

---

## Example: GET Request (async/await)

```js
async function getScores() {
    const response = await fetch("https://example.com/api/scores");
    return await response.json();
}
```

---

## Example: POST Request (async/await)

```js
async function submitScore(name, score) {
    await fetch("https://example.com/api/scores", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ name, score })
    });
}
```

---

## Integrating Async I/O Into a Game

```js
class Game {
    constructor() {
        this.playerName = "Ironhook";
        this.score = 0;
    }

    async endGame() {
        // send score
        await submitScore(this.playerName, this.score);

        // load leaderboard
        const leaderboard = await getScores();

        console.log("Updated Leaderboard:", leaderboard);
    }
}
```

This demonstrates:

- Async API calls  
- Using async/await inside game logic  
- Non‑blocking operations  
- Clean integration with gameplay  

---

## Why?
Asynchronous I/O shows that you understand:

- How to work with async operations  
- How to use Promises and async/await  
- How to integrate APIs into a game  
- How to avoid blocking the game loop  
- How modern JavaScript handles network requests  

This is a core skill for any web‑based game or application.

---
