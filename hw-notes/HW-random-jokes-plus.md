# Homework - Random Jokes Plus

## I. Overview
- In this HW assignment you will add substantial capability to your **random-joke** app
- This will take a bit of time, so get started early
- ***This HW will make a great "starter" for project 1, so it will be time well spent!***

<hr>
  
## II. Get Started
- Your start code should be where you left off on **random-joke** as of [Random Joke with tooling - checkoff](../checkoff-notes/random-joke-with-tooling-checkoff.md)
  - the above assignment added `nodemon`, `eslint` and CircleCI to your project
- You can work off of your existing GitHib repository and Heroku app, or you can create a new one, it's up to you. If you are going to go "new", you could have:
  - a new GitHub repository named **random-jokes-plus** (which is what we are going to call it in this exercise going forward)
  - a new Heroku app named `abc1234-random-jokes-plus`
  - if you don't remember how to initialize a new GitHub respository, head to [Skill #5 - First Node Web Server](../core-skills/5-first-node-web-server.md) - Part IV.
- Don't forget to `npm run nodemon` rather than `npm start` so that you won't have to re-boot the server all of the time
- Also be sure to run `npm test` on occassion - and whenever you run into an issue with your code - it might flag a problem for you early - that's what it's for:
  - Tip: Because `nodemon` is running in your terminal window, you can set up a second terminal window to periodically run `npm test`

<hr><hr>

<a id="phase1" />

## III. Phase #1. - add your own modules

1) You are going to create 2 external modules for **random-jokes-plus**, similar to how we did so in  [Skill #11 - Creating CommonJS Code Modules](/core-skills/11-creating-commonjs-code-modules.md) 

    - create **htmlResponses.js**
      - move `const errorPage = ...` into it 
      - create a function named `const get404Response = (request, response) => {...}` and "export" it
      - import **htmlResponses.js** (as `htmlHandler`) into **index.js**
      - call the `htmlHandler.get404Response()` function in the `onRequest` method of **index.js** (in the correct part of the `if`)
    - create **jsonResponses.js**
      - move `jokes` and `getRandomJoke()` into it
      - create a function named `const getRandomJokeResponse = (request, response) => {...}` and "export" it
      - import **jsonResponses.js** (as `jsonHandler`) into **index.js**
      - call the `jsonHandler.getRandomJokeResponse()` function in the `onRequest` method of **index.js** (in the correct part of the `if`)
     - your `if` statement - the one in `onRequest()` - should look something like this:
     
     <hr>
  
     ![screenshot](_images/hw-1.png)
     
     <hr>
      
    - test both endpoints in a web browser, they should work as before
    
<hr> 

2) Create `urlStruct` and use it
    
    - here you go, see below!
    
     <hr>
  
     ![screenshot](_images/hw-2.png)
     
     <hr>
     
    - test both endpoints in a web browser, they should work as before

<a id="phase2" />

<hr><hr>

## IV. Phase #2. - Add a `/random-jokes` endpoint
    
- The `/random-jokes` endpoint will return an array of jokes, defaulting at `1`
- The returned data will look like this:

<hr>

```json
[ 
 {
    "q": "What do you call a very small valentine?",
    "a": "A valen-tiny!"
  },
  {
    "q": "What did the dog say when he rubbed his tail on the sandpaper?",
    "a": "Ruff, Ruff!"
  }
]
```
<hr>

- If a `limit` parameter is also passed in to `/random-jokes`, that will be the number of jokes returned instead:
  - be sure to validate the `limit` parameter so that it is neither too large or to small - it should be constrained to integer values (use `Math.floor()`) between 1 and the `.length` of the `jokes` array, inclusive
  - for help with this, check out how we handled the `max` parameter in the "random number" HW
- Notes:
  - you will probably want to "shuffle" your array of jokes, and then grab the first `limit` number of items
  - if you borrow any array shuffling code from the Internet, be sure to credit your source both in the source code, and in the dropbox comments section
  - another alternative is to use npm's [underscore
](https://www.npmjs.com/package/underscore) package - which has a function named `shuffle()`
- Also, you will need to pass in a `params` object to the "random jokes response handler" - here's what it could look like:

<hr>

![screenshot](_images/hw-4.png)
    
 <hr>
  
- When you are done, add a working link to the 404 page that references this new endpoint - see below:

<hr>

![screenshot](_images/hw-3.png)
    
<a id="phase3" />

<hr><hr>


## V. Phase #3. - Send back both XML & JSON
    
- the default data type returned by both the `/random-joke` and `/random-jokes` endpoints is JSON
- but if the client sends an [HTTP `Accept` header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept) of `text/xml` in the request phase, then the application will return the joke data in XML format, and will send it back with a `content-type` of `text/xml`:
  - make sure that you handle the possibility that the client might not send any `accept` headers. You can easily test this in the Postman app.
- the joke XML data shall be formed like this:

**`/random-joke`**

```xml
<joke>
  <q>What is a frog's favorite outdoor sport?</q>
  <a>Fly Fishing!"</a>
</joke>
```

**`/random-jokes?limit=2`**

```xml
<jokes>
  <joke>
    <q>What is a frog's favorite outdoor sport?</q>
    <a>Fly Fishing!"</a>
  </joke>
  <joke>
    <q>I hate jokes about German sausages...</q>
    <a>They're the wurst!"</a>
  </joke>
</jokes>
```

- **When you test the app endpoints in Postman, and send `text/xml` for an `accept` header, you will see the following:

<hr>

![screenshot](_images/hw-5.png)

![screenshot](_images/hw-6.png)

<a id="phase4" />

<hr><hr>
    
## VI. Phase #4. - Send back headers only, NOT content,  when `HEAD` requests are made
