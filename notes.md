<!-- MERN AUTH -->

<!-- creating a simple server -->
Step 1: open a new folder and inside it run npm init -y

**the -y will ignore the questions asked when running this

Step 2: create a folder called backend, and inside it create a file called server.js (entry point for our api/backend)

Step 3: install the following;
npm i express dotenv mongoose bcryptjs jsonwebtoken cookie-parser

**express - web framework
**dotenv - load environment variables from .env file
**mongoose - interact with our mongo db database
**bcryptjs - hashing password
**jsonwebtoken - jwt for auth
**cookie-parser - for storing http only cookie

!!** to use ES modules, open package.json and add
"type": "module"

so instead of 
const express = require('express')
we use
import express from 'express'

<!-- server.js -->
import express from 'express'

const port = 5000

const app = express()

app.get('/', (req, res) => res.send('server is ready'))

app.listen(port, () => console.log(`server is started on port ${port}`))


<!-- start the server from the terminal -->
node backend/server.js

in package.json
add inside "scripts": {
    "start": "node backend/server.js",
    "server": "nodemon backend/server.js"
}
<!-- instead of typing "node backend/server.js" in the terminal, this script will let you run "npm run server"  -->

add npm i nodemon -D (as a dev dependency)

now we have to implement the .env file

add NODE_ENV=development, PORT=5000
on .env
<!-- replace in server.js -->
const PORT = 5000
<!-- with -->
const PORT = process.env.PORT

<!-- what is express js? -->
It's a layer built on the top of the Node js that helps manage servers and routes

npm i express-async-handler


<!-- EXAMPLE OF A  CONTROLLER SETUP -->

// @desc    Get User Profile
// route    GET /api/users/profile
// @access  Private
const userProfile = asyncHandler(async (req, res) => {
    res.status(200).json({ message: 'User Profile' })
})


// @desc    Update User Profile
// route    PUT /api/users/profile
// @access  Private
const updateUserProfile = asyncHandler(async (req, res) => {
    res.status(200).json({ message: 'Update User Profile' })
})

