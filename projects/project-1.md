# Project 1 - API Powered App

##  I. Overview

- Individually, you need to make a rich web app that uses a backend (server) web API of your design:
  - this API will have BOTH read-only capabilities (ex. `/random-joke` AND write capabilities (ex. `suggest-joke/?q=...&a=...`)
  - you may use an external API **in addition to your own**
  - the app should be engaging and aesthetically pleasing, ideally it will be (or approach) portfolio quality
  - the app should do something useful for its target audience
  - the project features should be scoped for just a couple of weeks
- The actual project is fairly open-ended - let the needs of app's users drive them capabilities of the app
- The static files (like HTML, CSS, Client JS, images, etc) may be sent normally, but the rest of the changes/updates for the app should be done through a custom AJAX API.

<hr>

## II. Ideas

Here are some loose ideas that would warrant a server side API. Be creative! Make a good portfolio piece!

- https://www.pokedex.org/ (loads page with overall list, but then calls to an individual one when clicked. Your API should work directly from the URL returning JSON.)
- https://naramsim.github.io/Colosseum/ (similar to above, with individual calls to certain objects. Note: this app uses a hash reference in the URL instead of query parameters, which does not quite fit the requirements. The overall app itself is similar to the idea of the assignment though.)
- https://sii.im/playground/notes/ (Note system where users can create a note and then use a query parameter through some UI ability or unique url to recall that particular note. Then the user could edit their note again.)
- https://trello.com/ (similar to above, a shared task board people could add tasks to or update.)
- https://asana.com (Similar to Trello. A task board people can add tasks to or update.)
- https://www.meetup.com (App for creating meetups based on a topic, area and time.)
- https://www.pinterest.com/ (board or boards people could add images, text, keywords to and add more later. To avoid uploading images, the user could submit a URL instead).
- https://deanhume.github.io/beer/ (App indexing some topic, such as board games, heartstone cards, music, etc and letting the user click on individuals for more info, go through categories or even search).
- https://hellosunapp.com (App that shows positions of the sun and moon in different times zones throughout the world.)
- https://getkana.com/app/ (Another tutorial type app that users could add to).
- http://flateric.columba.uberspace.de/canvas/ (Visualization of user collected messages, links, etc).
- http://idiots.win/ (quiz type app users could add questions to or create their own unique quiz).
- https://www.google.com/forms/about (A survey & survey creation system.)
- https://www.instapaper.com (A link and article manager. For users to store links for later.)
- https://www.getpennies.com (A personal financial tracker. Users can add their own data. DO NOT COLLECT REAL USER FINANICAL DATA IN THIS COURSE.)

<a id="functional-requirements" />

<hr>

## III. Functional Requirements (with an example)
- Here is a (limited functionality) example of a web site/service - **jokester.bomb** - of what a possible project would look like - here is the landing page --> https://p1-430-stub-2105.herokuapp.com/
- Your site will likely have a different structure (because ideally you are not building a "Random Joke" clone) - if you have any questions about your app meeting these requirements, ask in class or send me an email ASAP
  
  **1) Users can view a random joke via a `GET` Ajax call:**
  
    - use [`XHR`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) or [`fetch()`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)     - we already covered this in 230/235/330, in the "Accept Headers" demo, and in [Random Jokes Plus an Ajax Client](../hw-notes/HW-random-jokes-plus-an-ajax-client.md)
    - here is the (non functional) example: https://p1-430-stub-2105.herokuapp.com/app
    - *in your project, users must be able to access at least 2 endpoints of your API via Ajax calls, with a variety of controls depending on the needs of your users (this could be the 1st of the 2 required endpoint "viewers")*


  **2) Administrators can view user submitted jokes (this is just a `GET` Ajax call):**
  
    - note: we don't need to worry about an admin being "logged in" for this project
    - here is the (non functional) example: https://p1-430-stub-2105.herokuapp.com/admin
    - *in your project, you MUST have an admin page where all of the site data (user submitted and otherwise) can be viewed*
    - *in your project, users must be able to access at least 2 endpoints of your API via Ajax calls, with a variety of controls depending on the needs of your users (this could be the 2nd of the 2 required endpoint "viewers")*
  
  
  **3) Users can submit a joke via a `<form>` and an Ajax `POST` request:**
  
    - see the "Body Parse" examples and video
    - see the "POST-demo-start" example
    - here is the (non functional) example: https://p1-430-stub-2105.herokuapp.com/suggest
    - *in your project, use the "hijacked `<form>`" version*
    - *in your project, this functionality could be performed by a user, an admin, or both*
    - *a user, probably an admin, will also have the ability to update (edit) information on the server*
    
 
  **4) Required endpoints (MINIMUM) - your project needs ALL of these - here are examples:**

    - TWO data endpoints, one of which must take at least 1 parameter in the query string:
      - https://p1-430-stub-2105.herokuapp.com/random-joke
      - https://p1-430-stub-2105.herokuapp.com/random-jokes?limit=10
      - BOTH of these endpoints MUST:
        - Send back data as XML if (and only if) an HTTP `Accept` request header with a value of "text/xml" is sent by the client (we did this in [Random Jokes Plus - Phase 3](../hw-notes/HW-random-jokes-plus.md#phase3))
        - Send back the HTTP response headers ONLY (including `Content-Length`) when a HEAD request is send by the client (we did this in [Random Jokes Plus - Phase 4](../hw-notes/HW-random-jokes-plus.md#phase4))
    - ONE `POST` endpoint where a user will be able to add data to the app via a form. This form MUST send a minimum of 2 fields (ex `name` and `age` in the request):
      - the appropriate HTTP status codes will be returned when content is either created or updated on the server, or if insufficient parameters are included in the request
    - FOUR HTML pages:
      - https://p1-430-stub-2105.herokuapp.com/
      - https://p1-430-stub-2105.herokuapp.com/app
      - https://p1-430-stub-2105.herokuapp.com/suggest
      - https://p1-430-stub-2105.herokuapp.com/admin
    - ONE error page (which is an *additional* HTML page):
      - https://p1-430-stub-2105.herokuapp.com/bad-link
    - ONE CSS file:
      - https://p1-430-stub-2105.herokuapp.com/default-styles.css
    - ONE image:
      - https://p1-430-stub-2105.herokuapp.com/joke-image.jpg

   **5) Required HTTP status codes:**
     - Your app is required to send the following HTTP status codes at the appropriate time:
       - `200`, `201`, `204`, `400`, `404`
     - In your documentation, tell us where & when in the app these status codes are sent, example:
        - "`200` is sent for all successful HTML requests, and when the `/get-joke` endpoint is called"
        - "`201` is sent when the user creates a new joke with the POST `/add-joke` endpoint"
        - "`204` is sent when the admin edits an existing joke"
        - "`400` is sent when the user calls `/add-joke` with out all of the required parameters"
        - "`404` is sent when the server can't find a resource at the requested endpoint"
 
 <hr>
 
   **6) Other:**
   
- All of these information "calls"  (getting data, posting data, checking for updates, etc) must be done through Ajax and your web API
- It is okay to keep your API data in "memory only" for this project:
  - this does mean that user added data will go away after each server reload, which is roughly 30 minutes on Heroku
  - NB - we will be learning MongoDB for the next project
- Static files (such as HTML, CSS, Client JS, Images, Videos, etc) MUST be delivered from your Nodejs server (For example, NOT hosted on banjo, and delivered via a link)
- Direct calls to GET requests in the browser location box or via Postman must work correctly:
  - We will be testing `POST` requests with your `<form>` and via Postman
  - We will be testing `HEAD` requests via Postman


<a id="experience-requirements" />

<hr>

## IV. User Experience Requirements
1) Must provide an engaging and rich user experience

2) Users must be able to add data to the API via `POST` requests (with limitation). For example, maybe your app is a collection of images and keywords. You might then have a way for the user to add an image url and keywords to your API

3) Users will be able to view API data that others have posted. For example, a list of images and keywords 

4) The application must be performant and run as expected. There must not be any hiccups or performance issues when the server is under a light load. Common user errors must be handled gracefully on BOTH the client-side and server-side:
  
    - example: the user forgets to type in their last name (a required form field)
      - the *client* (the HTML page, utilizing JavaScript) will not allow the data to be submitted to the server
      - the *server* will return an error message and a status code of `400` if a value for required field is not given
      - we will test the API via the provided `<form>` AND by using Postman

<a id="development-requirements" />

<hr>

## V. Development Requirements

1) Must use Git for version control in a repo I can access. The repo will be named **abc1234-430-project-1** (where *abc1234* is your actual RIT web account name). You may make the repo *private* if you wish, just be sure to send me an invite to collaborate ASAP

2) Must use **HW - Random Jokes Plus** as a starting point for the project. You may NOT use any of the other demos in this way (for example, the "accept headers" or "HEAD requests" or "Body Parsing" demos that are zipped in myCourses). You may also NOT utilize any "routing" libraries such as [express](https://www.npmjs.com/package/express) (FYI - we will be covering express soon, and will use it on Project 2)

3) Must have `nodemon` installed. I will test this by typing `npm run nodemon`

4) Must have a "test" script that uses ESLint with the Airbnb spec. Must pass tests when I run `npm test`

5) Must use CircleCI for testing - the "test" script will be run by CircleCI, and a green checkmark will appear on the GitHub repo

6) Must have this "chromeinspect" script for debugging:

    - `"chromeinspect": "node --inspect ./src/index.js & echo \"Now in DEBUG mode. Head to 'chrome://inspect'\""`
    - I will test this by typing `npm run chromeinspect`

7) Other code standards:

    - code must be well-commented. Every function/method must have a comment describing its purpose
    - *Separation of Concern* - There should be a clear separation of purpose and classes. Do not put everything in the same file/module
    - **D.R.Y.** - *Don't Repeat Yourself*. Repeated blocks of nearly identical code must be factored out and placed in a separate function
    - any borrowed code or fragments (e.g. from Stack Overflow) must be credited in both your code comments, and in the final documentation of the project
    - all HTML & CSS pages must pass validation (warnings are OK)
    - all other media (images etc) must be *optimized* - meaning they have been re-sized to appropriate dimensions, and saved via 

8) Must be deployed to Heroku. The "Wait for CI to pass before deploy" checkbox must be checked in the dashboard

9) Borrowed code fragments MUST be cited in the code comments AND in the documentation - failing to do so constitutes plagiarism

10) BTW - [stackoverflow.com](https://stackoverflow.com/) is a fantastic resource that many of us use on a weekly or even daily basis. Please consider creating an account so that you can upvote answers, and maybe even comment or answer questions yourself. This also might also help you to remember to cite any related sources that you used

<hr>

## VI. Deliverables

### VI-A. Prototype

- Should at least be the core experience with some of the API working. The full API might not be ready and the app may not be finished, but the main part of the experience should be testable
- Submission:
  - Working version must be accessible online through Heroku
  - Final code must be pushed to Git repo
  - Final code must be zipped and submitted to the dropbox (without **node_modules**)
  - The following links in the submission comments

### VI-B. Final Version

- Final code must be pushed to Git repo
- Final code must be zipped and submitted to the dropbox (without node_modules)
- Link to the Git repo (add me if necessary).
- Link to cloud deployed app (Heroku).

### VI-C. Final Version Documentation

- Hand in documentation explaining the following:
  - What your site does and its purpose.
  - What part of your app does the API handle?
  - What went right and what went wrong?
  - If you were to continue, what would you do to improve your app?
  - How did you go above and beyond?
- Code:
  - Must be accessible online through Heroku (unless special arrangements have been made).
  - Final code should be submitted to Git repo.
  - Final code should be zipped and submitted to the dropbox (without node_modules).
  - The following links in the submission comments:
    - Link to the Git repo (add me if necessary).
    - Link to cloud deployed app (Heroku).
- A 1 to 2-minute narrated "demo reel" of the completed project will be required - post it to YouTube & put the URL in the comments field. If you decide to upload a video file instead, it must be in the MP4 format
  - The easiest way to record a demo reel is to use Zoom - here is a 2-minute video on how to do this: https://www.youtube.com/watch?v=D617OXKhSYw
    - don't forget to "Share Screen" so that I can see you interacting with the project
    - please don't stress out over this requirement - I am the only one who will see the video - I won't be sharing or posting these
    - 10% deducted from project 1 grade if the video requirement is not completed

<a id="rubric" />

<hr>

## VII. Rubric

- Do all of the above and get an 89%
- App must go "above and beyond" in order to get an A (be sure to document this)

### VII-A. Deductions

1) (-5% each) App is missing any of the individual requirements listed under [**III. Functional Requirements**](#functional-requirements) - Examples:

    - **III. Functional Requirements  4) Required endpoints** - *missing a GET API parameter*, *not sending back XML when requested*, *not sending back headers only when requested*, *not having 2 params sent in POST Body requests*, *not sending back a `201` status code at the proper time*, *not sending back a `400` status code at the proper time*a and so on
   
2) (up to -30% if not fully implemented) Users must be able to access at least 2 endpoints of your API via Ajax calls, with a variety of controls depending on the needs of your users 

3) (-25%) Missing page with `<form>` and ability to POST data with at least 2 parms to the server  

4) (-10% each) Missing any of the required HTML/CSS/Image endpoints

4) (-25% each) Missing GET endpoints

5) (-25% each) Missing POST endpoint

6) (-5% each) Does not meet **IV. User Experience Requirements** above

7) (-10% each) Not meeting the **V. Development Requirements** above 

8) (-10% each) Missing documentation or video

9) (-100%) Used express or similar framework 

10) (-100%) Code must be based on the "HW - Random Jokes Plus" assignment - i.e. do not use any "DONE" versions of demos from this or the other section or previous semesters as a starting point 
