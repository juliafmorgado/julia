---
title: "Cloud Native Dev - Challenge 2"
author: 'Julia Furst Morgado'
date: 2024-04-04T06:46:05.964Z
draft: true
image: https://blog-imgs-23.s3.amazonaws.com/cloud-native-dev-2challenge.png
tags:
categories: 
    - Tech
slug: /cloud-native-dev-challenge-2
---

Ok, so challenge 2 was given to me one day after I submitted challenge 1. We're not beating around the bush here!

## Challenge 2
The second challenge can be found [here](https://github.com/salaboy/cloud-native-dev/tree/main/2) and is about adding persistency into my simple web application. My repo can be found [here](https://github.com/juliafmorgado/cloud-native-dev/tree/main/2-challenge).

## Step 1: Create 2-challenge directory and copy code
1. Create a new directory named 2-challenge
2. Copy all the files from your challenge-1 directory (server.js, index.html, app.js) into this new directory by running the command `cp -R 1-challenge/ 2-challenge/` (on MacOS).

## Step 2: Branching and Implementing Filesystem Persistence
1. Switch to a new branch named fs from the main branch by running the command `git checkout -b fs`
2. Modify the backend (server.js) to implement filesystem persistence so it saves texts into a file using filesystem APIs and reads from it, instead of using an in-memory store. This will involve changes primarily to our `/save` and `/all` endpoints.

The new `server.js` file should look like this:
```
const express = require('express');
const fs = require('fs');
const path = require('path');
const app = express();
const PORT = 3000;

// Middleware to parse JSON bodies
app.use(express.json());

// Serve static files from the 'public' directory
app.use(express.static(path.join(__dirname, 'public')));

// Define the file path for storing data
const FILE_PATH = path.join(__dirname, 'texts.json');

// Initialize the file with an empty array if it doesn't exist
if (!fs.existsSync(FILE_PATH)) {
    fs.writeFileSync(FILE_PATH, JSON.stringify([]), 'utf8');
}

// Helper function to read texts from file
function readTextsFromFile() {
    const fileContents = fs.readFileSync(FILE_PATH, 'utf8');
    return JSON.parse(fileContents);
}

// Helper function to save texts to file
function saveTextsToFile(texts) {
    fs.writeFileSync(FILE_PATH, JSON.stringify(texts, null, 2), 'utf8');
}

// Endpoint to save text
app.post('/save', (req, res) => {
    const { text } = req.body;
    const texts = readTextsFromFile();
    texts.push(text);
    saveTextsToFile(texts);
    res.status(201).send({ message: 'Text saved successfully' });
});

// Endpoint to get all texts
app.get('/all', (req, res) => {
    const texts = readTextsFromFile();
    res.status(200).json(texts);
});

app.listen(PORT, () => {
    console.log(`Server running on http://localhost:${PORT}`);
});
```

3. Save and push the changes to your GitHub

### Changes Made
- **File Path Definition:** Specified `FILE_PATH` using `path.join` for compatibility across different operating systems.
- **File Initialization:** Ensured the file exists at the start. If not, it creates an empty array in it.
- **Reading and Writing Helper Functions:** Created `readTextsFromFile` and `saveTextsToFile` to encapsulate file operations, making the code cleaner and more reusable.
- **Modified `/save` and `/all` Endpoints:** These now use the helper functions to read from and write to the file, respectively, instead of using an in-memory array.

### Testing the Application
1. Start the server with `node server.js`.
2. Open your web browser to view your front-end application or use tools like Postman to make requests to your server.
3. Use the `/save` endpoint to save texts and `/all` to retrieve them. You should see that texts persist across server restarts, as they're now stored in a file.

## Step 3: Branching and Implementing Database Persistence
1. Switch to a new branch named sql from the main branch by running the command `git checkout -b sql`
