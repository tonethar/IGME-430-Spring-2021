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

4) Create a **src** folder for your program files

<hr>

## II. Start coding your express server

### II-A. Start Code

- Rather than CommonJS modules (`require()` & `module.exports`) like we used in Project 1:
  - let's instead use ES6 modules (`import` & `export`)
  - here's the code to start you off

**src/server.js**

![screenshot](_images/express-1.png)

- Now run the app with `npm run nodemon`
- ***FAIL!***

<hr>

### II-B. Node uses CommonJS (CJS) modules by default
- You can tell Node.js to use ES6 modules by either:
  -  changing the file extension of the JS files from `.js` to `.mjs` OR
  -  adding a `"type": "module"` key to **package.json** (we will do it this way)

<hr>

## III. Create some hard-coded data

- You can get some fake JSON data from https://www.mockaroo.com/
- Just use the `id`, `first_name` & `last_name` fields - delete the others
- Now export the JSON - 50 or 100 records is enough
- We will store this hard-coded data as just a regular JS array of object literals
- Create **src/data/user-data.js** file:

```js
const users = [{
  "id": 1,
  "first_name": "Jere",
  "last_name": "Reay"
},...];

// default export
export default users
```

- make sure that the **data** folder is inside the **src** folder so that the path to the file **src/data/user-data.js**:
  - of course, you can put this file where ever you want to, just be sure to `import` it properly!
- note we are doing an ES6 `export default` at then end of the **user-data.js** module

<hr>

## IV. Make sure that the data is loaded

- Add the following to **src/server.js**

```js
// default ES6 import
import users from './data/user-data.js';

...

console.log(users);
```

- Test it - the `users` array should log out

<hr>

## V. Create some `GET` routes

- Here is the code that will listen and respond for the `/` route
- Note that similar to the the `http` librbary, we ue the `response` object to send a message back to the requesting client

![screenshot](_images/express-2.png)

- Test this both in the browser and in Postman - WOW that's not a lot of code to send a response compared to using just the `http` library!
- Here are the express docs for `response` - http://expressjs.com/en/4x/api.html#res.send
- If we test this in the browser and check the headers, we will see that a HTTP status code of `200` (or `304`) and the "text/html" content type were sent by default. But we can explictly set both of these like this (not the method chaining):
  - `res.status(200).type('text/plain').send(`A GET request on route '/'`);`
- You can also set the response headers using the `http` library (BEFORE calling `res.send()`:
  - `res.setHeader('content-type', 'text/plain');`
- And here are the docs for the `app` object - be sure to check out all that it can do: http://expressjs.com/en/4x/api.html#app

<hr>

## VI. Create some `POST`, `PUT`, and `DELETE` routes for `/`

- Listen for `POST`, `PUT`, and `DELETE` requests for the `/` route 
- Pause the video, see if you can figure these out on your own
- Hint: `app.post()`, `app.put()` etc
- When you are done, test them with Postman

<hr>

## VII. Create a `GET` endpoint `/all-users`

- Now send back the entire contents of the the `users` array for the 

<hr>

## VIII. Submission


<hr><hr>
