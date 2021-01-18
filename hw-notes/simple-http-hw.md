# Simple HTTP HW Notes

## I. Overview

- The PDF for this HW is in myCourses
- *In this assignment, you will use Node.js to build a simple HTTP server to server HTML, text and JSON. The server will accept several different URLs and make a choice of what to return based on the URL.*
- This HW assignment walks though building an HTTP server similar to what we did in Core Skills #1-#7, and should reinforce much of what we covered there
- It also adds the following - we will elaborate on much of this in class:
  - rather than building a Node.js project from scratch, there is substantial start code that you will *fork* from an existing repository
  - you will be installing *developer dependencies* (e.g. packages) to your node project:
    - this will allow us to run ESLint - https://www.npmjs.com/package/eslint - which will periodically (whenever we type `npm test`) check our code for code quality issues
    - we will be following the Airbnb's base JS Style Guide:
      - https://www.npmjs.com/package/eslint-config-airbnb-base
      - https://github.com/airbnb/javascript
  - you will write "test" and "pretest" scripts in your **package.json** file
  - you will periodically run `npm test` to validate your code
  - rather than have all of the JS code in 1 file like we have been doing, you will split it up logically, into 4 separate files (modules):
    - **server.js**, **htmlResponses.js**, **jsonResponses.js** and **textResponses.js**
    - you will use `module.exports` to give each module a "public" interface
    - you will then `require()` them where their functions are needed
  - rather than having your HTML pages hard-coded in the JS, you will instead use `fs.readFileSync()` to load them from separate files
  - this HW uses CircleCI (Continuous Integration, see handout in myCourses)
- This HW also DID NOT cover some of the things we did in Core Skills #1-#7, including:
  - how to create a new local GitHub repository and link it to a remote repository
  - how to install regular npm libraries such as `nanoid`
  - how to return a "404 - file not found" page
  - how to pass parameters to a web service
     
<hr>

## II. Tips & Hints

1) You will be ***forking*** the start code:

    - https://github.com/IGM-RichMedia-at-RIT/Simple-HTTP-Assignment-Start
    - the **fork** button is in the upper right corner of the repository screen
    - when you fork an existing repository, you create a copy of it in your own GitHub account
    - once you have created this new (forked) repository you can `git clone` it
    - we covered git cloning in [Skill #3 - Command-line Git & Cloning Repositories](../core-skills/3-command-line-git.md)
    
2) After you have forked and then cloned the start code to your local hard drive

    - to update the remote repository (and to update the app on Heroku, once everything is connected):
      - you just have to do the `git add .`, `git commit -m`, and `git push` commands
      - you DO NOT have to `git init` OR `git remote add origin http://...` or any of that because it is unnecessary when you have previously "git cloned" a repository
    
3) Here is the "live" running version:

    - https://acjvks-simple-http-server.herokuapp.com/
    - https://acjvks-simple-http-server.herokuapp.com/page2
    - https://acjvks-simple-http-server.herokuapp.com/hello
    - https://acjvks-simple-http-server.herokuapp.com/time
    - https://acjvks-simple-http-server.herokuapp.com/helloJSON
    - https://acjvks-simple-http-server.herokuapp.com/timeJSON
    - https://acjvks-simple-http-server.herokuapp.com/fake
    - https://acjvks-simple-http-server.herokuapp.com/dankmemes
    
    
