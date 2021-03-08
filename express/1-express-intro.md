# Intro to express
- *Fast, unopinionated, minimalist web framework for node:*
  - https://www.npmjs.com/package/express
  - http://expressjs.com/
- Considered the defacto package for Node.js and apps that utilize HTTP, routing and server-side view rendering 
- Has easy hooks for *middleware*:
  - https://expressjs.com/en/guide/using-middleware.html
  - https://expressjs.com/en/resources/middleware.html

<hr>

## I. Set up project and tooling

1) Create a folder named **first-express-app** and `cd` into it

2) Install packages

    - `npm init -y`
    - `npm i express`
    - `npm i --save-dev nodemon`

3) Add the following to the "scripts" key of **package.json**
- `"nodemon": "nodemon --watch src src/server.js"`

<hr>

## II. Start coding your express server

### II-A. Start Code

- Rather than CommonJS modules (`require()` & `module.exports`) like we used in Project 1, let's instead use ES6 modules (`import` & `export`)

**src/server.js**

![screenshot](_images/express-1.png)

- `npm run nodemon` // FAIL

### II-B. Node uses CommonJS (CJS) modules by default
- You can tell Node.js to use ES6 modules by either:
  -  chnaging the file extension of the JS files from `.js` to `.mjs` OR
  -  adding a `"type": "module"` key to **package.json**

<hr>

## III. Create some hard-coded data

<hr>

## IV. Make sure that it's loaded

<hr>

## V. Create some `GET` routes

<hr>

## VI. Create some `POST`, `PUT`, and `DELETE` routes

<hr>

## VII. Create a `GET` endpoint `/all-users`

<hr>

## VIII. Submission


<hr><hr>
