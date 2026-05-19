---
layout: post
codemirror: true
title: API Integration
description: API Integration - CS111 Review
permalink: /API-Integration
---

| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |


---

# 🌐 API Integration  
Implementing a Leaderboard API (POST/GET scores)

## What Is API Integration?
An **API (Application Programming Interface)** allows your game to communicate with a server.  
For a leaderboard, this means your game can:

- **Send** a player’s score (POST)  
- **Retrieve** the leaderboard (GET)  

This lets you store scores online instead of only locally.

---

## Why Use a Leaderboard API?
A leaderboard API allows:

- Global high scores  
- Competition between players  
- Persistent score storage  
- Cross‑device syncing  
- Server‑side validation  

It’s a common feature in modern games.

---

## GET Request  
A **GET** request retrieves data from the server — in this case, the leaderboard.

Example:

```js
async function getLeaderboard() {
    const response = await fetch("https://example.com/api/leaderboard");
    const data = await response.json();
    return data;
}
```

### What this does:
- Contacts the server  
- Downloads the leaderboard  
- Converts it from JSON into usable JavaScript data  

---

## POST Request  
A **POST** request sends data to the server — usually the player’s name and score.

Example:

```js
async function submitScore(name, score) {
    await fetch("https://example.com/api/leaderboard", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ name, score })
    });
}
```

### What this does:
- Sends a JSON object to the server  
- Stores the score in the leaderboard database  

---

## Example: Integrating Into a Game

```js
class Game {
    constructor() {
        this.playerName = "Ironhook";
        this.score = 0;
    }

    async endGame() {
        await submitScore(this.playerName, this.score);
        const leaderboard = await getLeaderboard();
        console.log("Leaderboard:", leaderboard);
    }
}
```

This demonstrates:

- Submitting the score when the game ends  
- Fetching the updated leaderboard  
- Displaying it in the console  

---

## JSON Format  
Most leaderboard APIs use JSON.

Example request body:

```json
{
    "name": "Ironhook",
    "score": 1200
}
```

Example response:

```json
[
    { "name": "Ironhook", "score": 1200 },
    { "name": "Silentscar", "score": 950 }
]
```

---

## Why Teachers Assign This
API integration shows that you understand:

- How to communicate with servers  
- How to use `fetch()` for GET and POST  
- How to send and receive JSON  
- How to store and retrieve game data online  
- How to integrate backend services into a game  

This is a key skill for modern web‑based games and applications.

---
<div style="display: flex; flex-wrap: wrap; gap: 10px; justify-content: center;">
    <a href="http://captainsam12.opencodingsociety.com/A-I-O" style="text-decoration: none;">
        <div style="background-color: #f9ff86; color: black; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
            Asynchronous I/O

        </div>
    </a>
</div>
---