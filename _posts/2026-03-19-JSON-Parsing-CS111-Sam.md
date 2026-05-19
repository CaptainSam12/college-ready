---
layout: post
codemirror: true
title: JSON Parsing
description: JSON Parsing - CS111 Review
permalink: /JSON-Parsing
---

| MainHub | Lessons | Game Overview |
| ------- | ------ | ------ |
| [Let's Go!](https://CaptainSam12.github.io/college-ready/MainHub) | [Let's Go!](https://CaptainSam12.github.io/college-ready/Lessons) | [Let's Go!](https://CaptainSam12.github.io/college-ready/PGO) |


---

# 📦 JSON Parsing  
Parse API responses (leaderboard data, AI responses)

## What Is JSON?
**JSON (JavaScript Object Notation)** is a lightweight data format used by almost every API.  
It represents data using:

- **Objects** → `{ }`  
- **Arrays** → `[ ]`  
- **Strings, numbers, booleans**  

Example JSON:

```json
{
    "name": "Ironhook",
    "score": 1200
}
```

APIs send data in JSON because it’s easy for both humans and programs to read.

---

## Why Parse JSON?
When your game makes an API call, the server sends back **raw JSON text**.  
You must **parse** it to turn it into usable JavaScript objects.

Parsing JSON allows you to:

- Display leaderboard scores  
- Read AI responses  
- Load game settings  
- Process server data  
- Update UI elements  

Without parsing, the data is just a string.

---

## Parsing JSON From an API (GET Request)

When you fetch data from an API:

```js
const response = await fetch("https://example.com/api/leaderboard");
const data = await response.json();
```

### What’s happening?

- `fetch()` downloads the raw JSON  
- `.json()` converts it into a JavaScript object  
- `data` now contains usable values  

Example response:

```json
[
    { "name": "Ironhook", "score": 1200 },
    { "name": "Silentscar", "score": 950 }
]
```

After parsing, you can loop through it:

```js
data.forEach(entry => {
    console.log(entry.name, entry.score);
});
```

---

## Parsing AI Responses  
AI APIs often return structured JSON like:

```json
{
    "reply": "Your next quest awaits!",
    "confidence": 0.92
}
```

Parsing it:

```js
const response = await fetch("https://example.com/api/ai");
const data = await response.json();

console.log(data.reply);
```

This lets your game:

- Display dialogue  
- Trigger events  
- Adjust difficulty  
- Respond to player actions  

---

## Example: Parsing Leaderboard Data in a Game

```js
async function loadLeaderboard() {
    const response = await fetch("https://example.com/api/leaderboard");
    const leaderboard = await response.json();

    leaderboard.forEach(entry => {
        console.log(`${entry.name}: ${entry.score}`);
    });
}
```

This demonstrates:

- Fetching JSON  
- Parsing JSON  
- Using the parsed data  

---

## Handling Invalid JSON  
Sometimes APIs return malformed or unexpected data.  
Use `try/catch` to avoid crashes:

```js
try {
    const data = await response.json();
} catch (error) {
    console.error("Failed to parse JSON:", error);
}
```

This is important for real‑world reliability.

---

## Why Teachers Assign This
JSON parsing shows that you understand:

- How APIs send data  
- How to convert JSON into usable objects  
- How to integrate server responses into gameplay  
- How to handle asynchronous data  
- How to work with modern web APIs  

JSON is the universal language of web‑based games and applications.

---
<div style="display: flex; flex-wrap: wrap; gap: 10px; justify-content: space-between;">
    <a href="http://captainsam12.opencodingsociety.com/MainHub" style="text-decoration: none;">
        <div style="background-color: #f91d1d; color: black; padding: 10px 20px; border-radius: 5px; font-weight: bold;">
            Back To MainHub
        </div>
    </a>
</div>
---