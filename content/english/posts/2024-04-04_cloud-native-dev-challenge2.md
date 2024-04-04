---
title: "Cloud Native Dev - Challenge 2"
author: 'Julia Furst Morgado'
date: 2024-04-04T06:46:05.964Z
draft: false
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
Switch to a new branch named sql from the main branch by running the command `git checkout -b sql`

### Set up PostgreSQL
1. Install PostgreSQL with Homebrew by running `brew install postgresql@15` or through [this documentation](https://www.postgresqltutorial.com/postgresql-getting-started/install-postgresql-macos/)
2. Start PostgreSQL with the brew command `brew services start postgresql@15`
3. Add PostgreSQL client tools (binaries) to your system's PATH so you can use the `psql` command, otherwise the command is not recognized.

You can add them to your PATH by adding the following line to your shell profile file `echo 'export PATH="/opt/homebrew/opt/postgresql@15/bin:$PATH"' >> ~/.zshrc`. 

This command appends the specified directory to your ~/.zshrc file, which is the configuration file for the Z shell (assuming you are using the Z shell). It ensures that every time you open a new terminal session, the PostgreSQL binaries will be included in your PATH, allowing you to use commands like `psql`.

After running this command, remember to restart your terminal or source the `~/.zshrc` file to apply the changes by running `source ~/.zshrc`.

4. Access the PostgreSQL
Access the command line interface by running `psql postgres`. This command connects you to the PostgreSQL database server, and you'll be logged into the `postgres` database by default as the `postgres` user. The `postgres` database is a default database meant for administrative purposes.

5. Create a New PostgreSQL Database
From the PostgreSQL CLI, create a new database for your application by running the command `CREATE DATABASE your_database_name;`. Replace `your_database_name` with your preferred database name, I've named it challenge2.

6. Connect to Your New Database
To connect to the database you just created, use the following command `psql challenge2`.

7. Create a Table
Now that you're connected to your new database, you can create a table to store texts. Here’s an example command to create a simple table:
```
CREATE TABLE texts (
    id SERIAL PRIMARY KEY,
    content TEXT NOT NULL,
    created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP
);
```

This table has three columns:
- id: A unique identifier for each text, which automatically increments for each new row.
- content: A text column to store the text content.
- created_at: A timestamp column that records when each text was saved.

8. Verify the Table Creation
To ensure your table was created successfully, use the `\d` command to list all tables in your current database. You should see the `texts` table listed.

### Connect to PostgreSQL from Node.js
1. In our project directory we have to install the `pg` package by running `npm install pg`.
2. At this point I should have created a username and password to connect to it, but I'm afraid of getting confused in the process creation and after will have to create a `.env` file to save them so I'll try to skip it and use my operating system's current username, and no password for local connections.
3. Then we can set up the database connection in our `server.js`.
Here's the adjusted server.js:

```
const express = require('express');
const path = require('path');
const { Pool } = require('pg');

const app = express();
const PORT = 3000;

// Configure PostgreSQL connection
// This configuration assumes your PostgreSQL server allows you to connect using the default method.
const pool = new Pool({
  database: 'challenge2', // Ensure this database exists in your PostgreSQL server
});

// Middleware to parse JSON bodies
app.use(express.json());

// Serve static files from the 'public' directory
app.use(express.static(path.join(__dirname, 'public')));

// Endpoint to save text
app.post('/save', async (req, res) => {
  const { text } = req.body;
  try {
    const result = await pool.query('INSERT INTO texts (content) VALUES ($1) RETURNING *', [text]);
    res.status(201).send({ message: 'Text saved successfully', text: result.rows[0] });
  } catch (err) {
    console.error(err);
    res.status(500).send({ message: 'Failed to save text' });
  }
});

// Endpoint to get all texts
app.get('/all', async (req, res) => {
  try {
    const result = await pool.query('SELECT * FROM texts ORDER BY created_at DESC');
    res.status(200).json(result.rows);
  } catch (err) {
    console.error(err);
    res.status(500).send({ message: 'Failed to retrieve texts' });
  }
});

app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
```

### Run the Node.js Application
Now that our PostgreSQL server is up and running and we've modified our Node.js app we can run the command `node server.js`. You should see the message "Server running on http://localhost:3000" logged into the console.
Open the browser and interact with the application.
![](https://blog-imgs-23.s3.amazonaws.com/web-server-challenge2.png)

### Verify Data has been Saved
To verify that your data has been saved in the PostgreSQL database, you can use the `psql` command-line interface to query the database directly.
1. Connect to the PostgreSQL database by running the command `psql -d challenge2`
2. Once connected, you can run SQL queries directly. To see the contents of the texts table (assuming that's the name of your table where texts are stored), execute `SELECT * FROM texts;`
You should see this on the terminal:
![](https://blog-imgs-23.s3.amazonaws.com/web-server-challenge2-terminal.png)

3. After checking your data, you can exit the `psql` interface by typing `\q`.

Remember, every time your application handles a POST request to the `/save` endpoint and successfully processes it, a new record should be inserted into your database. You can keep the `psql` interface open and run the `SELECT` command as many times as you like to see new records as they are added.
