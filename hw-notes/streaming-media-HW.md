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
  - *refactoring* duplicated code into a reusable function (in this case the media loading code)
- Topics that are new on this assignment:
  - hosting a web page that requires multiple files, for example a page that consists of an HTML file AND an MP4 (don't "overthink" this, we'll talk about it in class!)
  - *streaming* very large files like MP3s and MP4s:
    - `fs.stat` will be used to get file information such as its length
    - `fs.createReadStream()`, the `'open'` event handler, and `.pipe()` are used to send just part of a file back to the browser (i.e. a *byte range*)
  - the status code of `206 Partial Content` - which tells the browser that is can request more of the content
  - the `range` *request* header, where a client requests a byte range of a file
  - the following *response* headers:
    - `Content-Range`
    - `Accept-Ranges`
    - `Content-Length`
    - `Content-Type` - we have seen this before

<hr>

## II. Tips & Hints

1) Here are endpoints you will need to implement:
    - `/` - sends **client.html** (this HTML page displays a `<video>` tag for **party.mp4**):
      - which means that the browser will render this page, and then make an *additional request* for **party.mp4**
    - `/page2` - sends **client2.html** (this HTML page displays an `<audio>` tag for **bling.mp3**):
      - which means that the browser will render this page, and then make an *additional request* for **bling.mp3**
    - `/page3` - sends **client3.html** (this HTML page displays a `<video>` tag for **bird.mp4**):
      - which means that the browser will render this, page, and then make an *additional request* for **bird.mp4**
    - `/bird.mp4` - sends **bird.mp4** 
    - `/bling.mp3` - sends **bling.mp3** 
    - `/party.mp4` - sends **party.mp4** 
    - *all-other-endpoints* - also sends **client.html** as the default page (there is NOT a customized 404 page)
    
2) In class we will discuss the most common mistakes that students make while completing this assignment
