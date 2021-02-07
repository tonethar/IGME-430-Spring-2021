# Streaming Media HW Notes

## I. Overview

- The PDF for this HW is in myCourses
- *In this assignment, you will use Node.js to stream basic video and audio content.*
- Topics that we have seen before on this assignment:
  - *forking* the start files to your own GitHub repository, and then *cloning* them to your local hard drive
  - installing the ESLint developer dependencies:
    - the **.eslintrc** is already created for you in the start files
    - you will have to add a "pretest" key to **package.json**
  - using `require()` to import your own modules of code ex. **htmlResponses.js**
  - setting up a basic HTTP server and an `onRequest` handler
  - loading in static HTML files with the `fs` module and `fs.readFileSync()`
- Topics that are new on this assignment:

<hr>

## II. Tips & Hints

1) Here are endpoints you will need to implement:
    - `/` - sends **client.html** (this HTML page displays a `<video>` tag for **party.mp4**)
    - `/page2` - sends **client2.html** (this HTML page displays an `<audio>` tag for **bling.mp3**)
    - `/page3` - sends **client3.html** (this HTML page displays a `<video>` tag for **bird.mp4**)
    - `/bird.mp4` - sends **bird.mp4** 
    - `/bling.mp3` - sends **bling.mp3** 
    - `/party.mp4` - sends **party.mp4** 
    - `all-other-endpoints` - also sends **client.html**  (there is NOT a customized 404 page)
    
2) In class we will discuss the most common mistakes that students make while completing this assignment
