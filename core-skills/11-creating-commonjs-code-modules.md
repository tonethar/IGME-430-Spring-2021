# Skill #11 - Creating CommonJS Code Modules


## I. Overview 

- https://nodejs.org/docs/latest/api/modules.html
- `module.exports`
- `require()`

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
  - \*\*IMPORTANT: rename this function to `randomNumberJSON` \*\*

<hr>

### II-C.  Create a response handling function

- Add the following *response handler* to **jsonResponses.js**

```js
const getRandomNumberResponse = (request,response,params) => {
  response.writeHead(200, { 'Content-Type': 'application/json' });
  response.write(randomNumberJSON(params.max));
  response.end();
};
```

- Note that this is similar code to handle the `/random-number` endpoint what we have over in **index.js**, except:
  - that `params` is an object that is getting passed in
  - and we need to grab the `max` property from params and pass that to our `randomNumberJSON()` helper function so that it functions as before

<hr>

### II-D.  Create a *public interface* for the **jsonResponses.js** module

- We need to make the  `getRandomNumberResponse()` function "public" (i.e. *visible*) outside of this file
- The ` randomNumberJSON()` function can stay "private"
- Here's the code to do so - add it to the bottom of **jsonResponses.js**:
  - `module.exports.getRandomNumberResponse = getRandomNumberResponse;`
 
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
  - `const jsonHandler = require('./jsonResponses.js')`

<hr>

### II-F.  Use the module 
- In `onRequest()`, replace the 3 lines of "response" code in the `else if (pathname === '/random-number') {` block with:
  - `jsonHandler.getRandomNumberResponse(request,response,params);`
  - the above code will call the `getRandomNumberResponse()` function over in **jsonResponses.js**, and pass in the 3 parameters it needs

<hr>

### II-G.  Test it
- If you have running `nodemon` (as we asked you to at the beginning, when you first tested the app), you have probably noticed that the app has been rebuilding and crashing as you made changes, this is normal!
- But once you save the last line of new code above it should be running correctly
- Head to the browser and test these endpoints, everything should work as before:
  - http://localhost:3000/
  - http://localhost:3000/random-number
  - http://localhost:3000/random-number?max=10000
  - http://localhost:3000/fake-file-name

<hr> 

## III. Create the htmlResponses.js module
- Now let's look at moving our HTML responses to a separate file (i.e. module)

### III-A. Create the htmlResponses.js module
- Create a new file named **htmlResponses.js** (in the **src** folder, obviously), and move the following code (found in **index.js**) into it:
  - `const indexPage = ...`
  - `const errorPage = ...`
  
<hr>

### III-B. Create the "index response" function

```js
const getIndexResponse = (request,response) => {
  response.writeHead(200, { 'Content-Type': 'text/html' });
  response.write(indexPage);
  response.end();
};
```

- Note that we do not have a `params` parameter like in `getRandomNumberResponse(request,response,params)`, as we don't need one because we are not apssing any parameters to the index page

<hr>

### III-C. Create a *public interface* for the **htmlResponses.js** module
- so we don't need to export `indexPage` or `errorPage`, but we do need to export `getIndexResponse`
- to the bottom of **htmlResponses.js** add:
  - `module.exports.getIndexResponse = getIndexResponse;`

<hr>

### III-D. "Import" the htmlResponses.js module
- Over in **index.js**, go ahead and `require()` **htmlResponses.js** like we did with **jsonResponses.js** -and name this import `htmlHandler`

<hr>

### III-E. Use the *htmlResponses* module 
- In `onRequest()`, replace the 3 lines of "response" code with a call to `getIndexResponse()` - and don't forget to pass over the `request` and `response` parameters

<hr>

### III-F. Test it!

- Head to the browser and test these endpoints, everything should work as before, except the last link (the 404 page), which will cause a crash:
  - http://localhost:3000/
  - http://localhost:3000/random-number
  - http://localhost:3000/random-number?max=10000
  - http://localhost:3000/fake-file-name

<hr>

### III-G. Get the `404` page working

- Over in **htmlResponses.js**, name the function `get404Response()`
- Move the appropriate code over from `onRequest()` 
- export it, of course
- in **index.js**, use it in the right place in `onRequest()`
- once everything is working, move on

<hr>

## IV. One last thing, a dispatch table

- https://en.wikipedia.org/wiki/Dispatch_table

<hr><hr>

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
|   [Skill #10 - Debugging Node](10-debugging-node.md) |  [**IGME-430**](../) | [Skill #12 - "Serving" a Rich Client Page](12-serving-rich-client-and-ajax.md)
