# Homework - Random Jokes Plus

## I. Overview
- In this HW assignment you will add substantial capability to your **random-joke** app
- This will take a bit of time, so get started early
- This HW will make a great "starter" for project 1, so it will be time well spent!

<hr>
  
## II. Get Started
- Your start code should be where you left off on **random-joke** as of [Random Joke with tooling - checkoff](../checkoff-notes/random-joke-with-tooling-checkoff.md)
  - the above assignment added `nodemon`, `eslint` and CircleCI to your project
- You can work off of your existing GitHib repository and Heroku app, or you can create a new one, it's up to you. If you are going to go "new", you could have:
  - a new GitHub repository named **random-jokes-plus** (which is what we are going to call it in this exercise going forward)
  - a new Heroku app named `abc1234-random-jokes-plus`
  - if you don't remember how to initialize a new GitHub respository, head to [Skill #5 - First Node Web Server](../core-skills/5-first-node-web-server.md) - Part IV.

<hr>

## III. Phase #1. - add your own modules

1) You are going to create 2 external modules for **random-jokes-plus**, similar to how we did so in  [Skill #11 - Creating CommonJS Code Modules](/core-skills/11-creating-commonjs-code-modules.md) 

    - create **htmlResponses.js**
      - move `const errorPage = ...` into it 
      - create a function named `const get404Response = (request, response) => {...}` and "export" it
      - import **htmlResponses.js** (as `htmlHandler`) into **index.js**
      - call the `htmlHandler.get404Response` function in the `onRequest` method of **index.js**
    - **jsonResponses.js**
      - 
