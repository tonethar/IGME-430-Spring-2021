# Skill #11 - Creating CommonJS Code Modules


## I. Overview 

- https://nodejs.org/docs/latest/api/modules.html
- `module.exports`
- `require()`
- Dispatch table - https://en.wikipedia.org/wiki/Dispatch_table

## II. Creating our own code modules

### II-A. Get Started

- Go ahead and `git clone <url>` your **first-web-service** repository:
  - `cd` into it, and `npm i` to download all your dependencies

### II-B. Create the jsonResponses.js module
- Create a new file named in the **src** directory named **jsonResponses.js**, and move the following code into it:
  - `const getRandomNumberJSON = ...`
  
### II-C.  Create a response handling function

- Add the following *response handler* to **jsonResponses.js**

```js
const responseRandomNumber = (request,response,params) ={
  response.writeHead(200, { 'Content-Type': 'application/json' });
  response.write(getRandomNumberJSON(max)); // send content
  response.end(); // close connection
}
```

### II-D.  Create a *public interface* for the **jsonResponses.js** module

- We need to make the  `responseRandomNumber()` function "public" (i.e. *visible*) outside of this file
- The ` getRandomNumberJSON()` function can stay "private"
- Here's the code to do so - add it to the bottom of **jsonResponses.js**:
  - `module.exports.responseRandomNumber = responseRandomNumber;`
  
**Common JS Modules:**

- This is a module syntax known as CommonJS:
  - This is an *older* module syntax than the ES6 Module syntax we used in 330
  - Does Nodejs have access to ES6 module syntax? YES
  - So why are we still using this older syntax?
    - as of this writing, not all Node.js libraries support the newer syntax
    - the vast majority of existing Node projects still use the older CommomJS syntax - so it is good to know!

### II-E.  "Import" the *jsonResponses.js* module

- Over in **index.js**


<hr> 

### III-X. Create the htmlResponses.js module
- Create a new file named **src/htmlResponses.js**, and move the following code into it:
  - `const indexPage = ...`
  - `const errorPage = ...`
- to the bottom of **src/htmlResponses.js** add:




<hr><hr>

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
|   [Skill #10 - Debugging Node](10-debugging-node.md) |  [**IGME-430**](../) | [Skill #12 - "Serving" a Rich Client Page](12-serving-rich-client-and-ajax.md)
