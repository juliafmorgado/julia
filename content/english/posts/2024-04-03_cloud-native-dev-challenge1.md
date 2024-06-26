---
title: "Cloud Native Dev - Challenge 1 Building a Web App"
author: 'Julia Furst Morgado'
date: 2024-04-03T06:46:05.964Z
draft: false
image: https://blog-imgs-23.s3.amazonaws.com/cloud-native-dev-1challenge.png
tags:
categories: 
    - Tech
slug: /cloud-native-dev-challenge-1-building-web-app
---

It's been some time since I engaged in a conversation with [Mauricio Salatino](https://www.salaboy.com/about/), widely known as Salaboy, about embarking on a mentor-mentee journey to enhance my Cloud Native skills. After much anticipation, we've finally launched the "program" (if I can call it a program)!

Excitingly, it's structured into challenges, and I invite you to join me on this learning journey!

## Challenge 1
The first challenge can be found [here](https://github.com/salaboy/cloud-native-dev/tree/main/1) and is about building a simple web application. My repo can be found [here](https://github.com/juliafmorgado/cloudnative-dev). Of course, I used chatGPT to help me, and Salaboy said it was allowed! The end goal is to understand what I'm building. So here I'm going to explain what does what.

## Step 1: Setting up the Environment
**1. Install Node.js**
Since we are going to build the web app with Node.js we need to install it on our machine. You can install it using [Homebrew](https://formulae.brew.sh/formula/node) with the command `brew install node`.

**2. Create and Navigate to Project Directory**
After installing Node.js, create a directory for your project (in your case, cloud-native-dev) and navigate into it.
```
mkdir cloud-native-dev
cd cloud-native-dev
```
**3. Initialize Node.js Project**
Once inside your project directory (cloud-native-dev), initialize a Node.js project using `npm init -y`. The `-y` flag automatically generates a `package.json` file with default values.

**4. Install Express**
After initializing the Node.js project, install Express using npm: `npm install express`.

This command installs Express locally in the cloud-native-dev directory and updates your `package.json` file with the dependency.

At this point, we're all set to start writing our code. You can start by creating the directories and files that you're going to need or create them as you go, but basically, our directory structure will be as follows (notice I'm following best practices for separating concerns by keeping static files in a `public` directory):

```
cloud-native-dev/
└── challenge-1/
    ├── README.md
    └── app/
        ├── public/
        │   ├── index.html
        │   └── app.js
        └── server.js
    ├── node_modules/  (created after npm install express)
    ├── package.json   (created after npm init -y)
    └── package-lock.json  (created after npm install express)
```

## Step 2: Writing the Backend Code
Inside the `app` directory, run the following command on your terminal:

```
cat <<EOF >server.js
const express = require('express');
const path = require('path');
const app = express();
const PORT = 3000;

// Middleware to parse JSON bodies
app.use(express.json());

// Serve static files from the 'public' directory
app.use(express.static(path.join(__dirname, 'public')));

// In-memory store
const texts = [];

// Endpoint to save text
app.post('/save', (req, res) => {
  const { text } = req.body;
  texts.push(text);
  res.status(201).send({ message: 'Text saved successfully' });
});

// Endpoint to get all texts
app.get('/all', (req, res) => {
  res.status(200).json(texts);
});

app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
EOF
```
This command creates a file named server.js and writes the provided JavaScript code into it.

> This script essentially sets up a basic Express.js server with two endpoints (/save for saving text and /all for retrieving all saved texts) and serves static files from a public directory.


## Step 3: Setting Up The Frontend
Create a new file named index.html inside a public folder by running the command `mkdir -p public && touch public/index.html`. 

Paste the following code:

```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>To-Do App</title>
</head>
<body>
<h2>My To-Do List</h2>
<textarea id="textArea"></textarea><br>
<button onclick="saveText()">Save Text</button>
<ul id="textsList"></ul>

<script src="app.js"></script>
</body>
</html>
```
> This HTML file sets up a simple user interface for a To-Do List application that allows inputting, saving and displaying text.

Now create a new file named app.js in the project directory (again, I'm keeping my static files under a public folder) by running the command `touch public/app.js`.

Paste the following code:

```
// Function to save text
async function saveText() {
    const text = document.getElementById('textArea').value;
    await fetch('/save', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ text }),
    });
    fetchAllTexts(); // Refresh the list after saving
  }
  
  // Function to fetch all texts
  async function fetchAllTexts() {
    const response = await fetch('/all');
    const texts = await response.json();
    const list = document.getElementById('textsList');
    list.innerHTML = ''; // Clear existing list
    texts.forEach((text) => {
      const item = document.createElement('li');
      item.textContent = text;
      list.appendChild(item);
    });
  }
  
  // Load all texts on initial load
  document.addEventListener('DOMContentLoaded', fetchAllTexts);
```

> These JavaScript functions complement the HTML code provided above. They implement the functionality to save texts via the `/save` endpoint and fetch them from the `/all` endpoint. This facilitates the interaction between our frontend and backend.

## Step 4: Running the Application
Let's start our Node.js server by running `node server.js` and then navigating to http://localhost:3000 in our web browser. You should see your To-Do application user interface, ready to accept input. 

Here's what you should do next to test the full functionality:

1. Type some text into the text area.
2. Click the "Save Text" button. This sends your text to the server, saving it in memory.
3. The page should automatically update to list your saved text below the text area.

![](https://blog-imgs-23.s3.amazonaws.com/web-server-1challenge.png)

To stop running the server just press `ctl+C`

## Understanding What We Built
- **Backend (Node.js + Express):** Our server handles HTTP requests, serves static files, and provides two API endpoints. One endpoint saves text sent in a POST request; the other returns all saved texts in a GET request.
- **Frontend (HTML + JavaScript):** The user interface where users can input text to be saved. It interacts with the backend via API calls to save and retrieve texts.

## Why This Matters
Building this simple application demonstrates several foundational concepts in web development and cloud-native applications, including:

- Client-server architecture: Understanding how the frontend (client) interacts with the backend (server) is crucial for web development.
- RESTful API design: Our endpoints follow REST principles, making them predictable and easy to use.
- State management: We manage application state (saved texts) in memory, which while not persistent across server restarts, teaches the basics of data handling.

## Conclusion
Through challenges like these, we're not only learning about technology but also about structuring projects and thinking critically about design and architecture. Feel free to clone the repository, try out the challenge yourself, and share your thoughts and suggestions!

Happy coding, and see you in the next challenge!

***

If you liked this article, follow me on [Twitter](https://twitter.com/juliafmorgado) (where I share my tech journey daily), connect with me on [LinkedIn](https://www.linkedin.com/in/juliafmorgado/), check out my [IG](https://www.instagram.com/juliafmorgado/), and make sure to subscribe to my [Youtube](https://www.youtube.com/c/JuliaFMorgado) channel for more amazing content!!
