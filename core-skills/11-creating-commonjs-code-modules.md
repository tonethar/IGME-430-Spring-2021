# Skill #11 - Creating CommonJS Code Modules


## I. Overview 

- https://nodejs.org/docs/latest/api/modules.html
- `module.exports`
- `require()`
- Dispatch table - https://en.wikipedia.org/wiki/Dispatch_table

<hr>

## II. Creating our own code modules

### II-A. Get Started

- Go ahead and `git clone <url>` your **first-web-service** repository:
  - `cd` into it, and `npm i` to download all your dependencies
  - `npm run nodemon` to boot up the server
  - head to `http://localhost:3000/` to be sure that the app functions as before
  - now let's start refactoring this code!

<hr>

### II-B. Create the jsonResponses.js module

- Create a new file named in the **src** directory named **jsonResponses.js**, and move the following code into it:
  - `const getRandomNumberJSON = ...`

<hr>

### II-C.  Create a response handling function

- Add the following *response handler* to **jsonResponses.js**

```js
const randomNumberResponse = (request,response,params) => {
  response.writeHead(200, { 'Content-Type': 'application/json' });
  response.write(getRandomNumberJSON(params.max));
  response.end(); // close connection
}
```

- Note that this is similar code to handle the `/random-number` endpoint what we have over in **index.js**, except:
  - that `params` is an object that is getting passed in
  - and we need to grab the `max` property from params and pass that to our `getRandomNumberJSON()` helper function so that it functions as before

<hr>

### II-D.  Create a *public interface* for the **jsonResponses.js** module

- We need to make the  `randomNumberResponse()` function "public" (i.e. *visible*) outside of this file
- The ` getRandomNumberJSON()` function can stay "private"
- Here's the code to do so - add it to the bottom of **jsonResponses.js**:
  - `module.exports.randomNumberResponse = randomNumberResponse;`
 
**Common JS Modules:**

- This is a module syntax known as [CommonJS](https://nodejs.org/api/modules.html#modules_module_exports):
  - This is an *older* module syntax than the ES6 Module syntax we used in 330
  - Does Nodejs have access to ES6 module syntax? YES
  - So why are we still using this older syntax?
    - as of this writing, not all Node.js libraries support the newer syntax
    - the vast majority of existing Node projects still use the older CommomJS syntax - so it is good to know!

<hr>

### II-E.  "Import" the *jsonResponses.js* module

- Over in **index.js**, add the following line of code to the top of the file:
  - `const jsonResponses = require('./jsonResponses.js')`

<hr>

### II-F.  Use the module 
- replace the 3 lines of "response" code in the `else if (pathname === '/random-number') {` block with:
  - `jsonResponses.randomNumberResponse(request,response,params);`
  - the above code will call the `randomNumberResponse()` function over in **jsonResponses.js**, and pass in the 3 parameters it needs

<hr>

### II-G.  Test it
- If you have running `nodemon` (as we asked you to at the beginning, when you first tested the app), you have probably noticed that the app has been rebuilding and crashing as you made changes, this is normal!
- But once you save the last line of new code above it should be running correctly
- Head to the browser and test these endpoints, everything should work as before:
  - http://localhost:3000/
  - http://localhost:3000/random-number
  - http://localhost:3000/random-number?max=10000

<hr> 

## III. Create the htmlResponses.js module
- Now let's look at moving our HTML responses to a separate file

### III-A. Create the htmlResponses.js module
- Create a new file named **htmlResponses.js** (in the **src** folder, obviously), and move the following code (found in **index.js**) into it:
  - `const indexPage = ...`
  - `const errorPage = ...`
- to the bottom of **htmlResponses.js** add:




<hr><hr>

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
|   [Skill #10 - Debugging Node](10-debugging-node.md) |  [**IGME-430**](../) | [Skill #12 - "Serving" a Rich Client Page](12-serving-rich-client-and-ajax.md)
