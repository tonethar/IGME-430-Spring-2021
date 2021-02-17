# Project 1 - API Powered App - DRAFT

##  I. Overview

- Individually, you need to make a rich web app that uses a web API of your design. This API will have BOTH read-only capabilities (ex. `/random-joke` AND write capabilities (ex. `suggest-joke/?q=...&a=...`). You may use an external API **in addition to your own**. The app should be engaging and aesthetically pleasing. Ideally it will be (or approach) portfolio quality.  The project should be scoped for just a couple of weeks.
- The actual project is fairly open-ended. The goal is to make a rich web app that uses backend (server) data from an API. The app should be aesthetically pleasing and provide a rich user experience. 
- Let the needs of app's users drive them capabilities of the app
- The static files (like HTML, CSS, Client JS, images, etc) may be sent normally, but the rest of the changes/updates for the app should be done through a custom AJAX API.

### I-A. Example
- Here is a (limited functionality) example of a web site/service - **jokester.bomb** - of what a possible project would look like:
- Landing page - https://p1-430-stub-2105.herokuapp.com/
- Functionality:
  - Users can view a random joke via an Ajax call (use `XHR` or `fetch()` - we already covered this in 330 and in Week 4)
  - Users can submit a joke via a `<form>` and an Ajax POST request (we are covering this week 5)
  - Administrators can view user submitted jokes (this is just an AJAX call)
  - Required endpoints (MINIMUM) - here are examples:
    - TWO data endpoints:
      - https://p1-430-stub-2105.herokuapp.com/random-joke
      - https://p1-430-stub-2105.herokuapp.com/random-jokes?limit=10
    - FOUR HTML pages:
      - https://p1-430-stub-2105.herokuapp.com/
      - https://p1-430-stub-2105.herokuapp.com/app
      - https://p1-430-stub-2105.herokuapp.com/suggest
      - https://p1-430-stub-2105.herokuapp.com/admin
    - ONE error page (which is also an HTML page):
      - https://p1-430-stub-2105.herokuapp.com/bad-link
    - ONE CSS file:
      - https://p1-430-stub-2105.herokuapp.com/default-styles.css
    - ONE image:
      - https://p1-430-stub-2105.herokuapp.com/joke-image.jpg

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

<hr>

## III. Development Requirements

1) Must use Git for version control in a repo I can access. You may make the repo *private* if you wish, just be sure to send me an invite to collaborate ASAP

2) Must have `nodemon` installed. I will test this by typing `npm run nodemon`

3) Must have a "test" script that uses ESLint with the Airbnb spec. Must pass tests when I run `npm test`

4) Must use CircleCI for testing - the "test" script will be run by CircleCI, and a green checkmark will appear on the GitHub repo

5) Other code standards:

    - code must be well-commented. Every function/method must have a comment describing its purpose
    - *Separation of Concern* - There should be a clear separation of purpose and classes. Do not put everything in the same file/module
    - **D.R.Y.** - *Don't Repeat Yourself*. Repeated blocks of nearly identical code must be factored out and placed in a separate function
    - any borrowed code or fragments (e.g. from Stack Overflow) must be credited in both your code comments, and in the final documentation of the project

6) Must be deployed to Heroku. The "Wait for CI to pass before deploy" checkbox must be checked in the dashboard

<hr>

## IV. Functional Requirements
1) Must provide an engaging and rich user experience

2) Users must be able to add data to the API (with limitation). For example, maybe your app is a collection of images and keywords. You might then have a way for the user to add an image url and keywords to your API

3) Users will be able to view API data that others have posted. For example, a list of images and keywords that 

4) The application must be performant and run as expected. There must not be any hiccups or performance issues when the server is under a light load. Common user errors must be handled gracefully on both the client-side and server-side:
  
    - example: the user forgets to type in their last name (a required form field)
      - the *client* (the HTMK page, utilizing JavaScript) will not allow the data to be submitted to the server
      - the *server* will return an error message if a value for required field is not iven
      
5) All of these information "calls"  (getting data, posting data, checking for updates, etc) must all be done through Ajax and your web API
 
6)  It is okay to keep your API data in memory for this project (NB - we will be learning MongoDB for the next project). That does mean user added data will go away after each server reload. (roughly 30 minutes on Heroku)


Static files (such as HTML, CSS, Client JS, Images, Videos, etc) should be delivered from the server.

Direct calls to GET requests should work correctly. As in: going straight to the Ajax URL in the browser (including parameters).


<hr>

## V. Programming Requirements

1) Server API must support the following status codes: 200, 201, 204, 400, 404, 500 (only necessary if applicable)

2) Server API must support the following methods:

    - HEAD (must be supported on the JSON calls that get data back)
    - GET
    - POST
    
3) At least one GET request type will support query parameters (both in AJAX and directly). These could be used to filter results, sort results or something else.

Client should use accept header (only needs to support JSON, but other formats would count as extra).
Client should submit a body in a POST request to add or update data.

### V-A. Web Services (3)

1) Custom Web API (Read-only)
      
    - uses HTTP `GET` method
    - returns data in JSON format by default:
      - returns data in XML format if `accepts` request header has a value of "text/xml"
    
    - takes at least 2 parameters
    - example: 
      - *"Get Jokes" API with `limit` and `minrating` parameters*
      - endpoint: `/get-jokes?limit=5&minrating=3`
      - data stored in hard-coded array of object literals - `allJokes`
      
    - #2 - User submitted data API (Write):
      - uses HTTP `POST` method
      - CORS is turned OFF (the default)
      - takes at least 2 body parameters
      - response:
          - sends back proper HTTP status codes ex. `201 Created`
          - sends back created resource ex. `{"q": "I invented a new word!", "a": "Plagiarism!"}`
      - example: 
        - *"Suggest Joke" API with `q` and `a` and `username` parameters*
        - endpoint: `POST /suggest-joke?q=setup&a=punchline&username=abc1234`
        - adds the submitted data to a `userSuggestions` array - the data is in object literal format
    - #3 - User submitted data API (Read):
      - uses HTTP `GET` method
      - takes at least 1 parameter
      - example:
        - returns contents of `userSuggestions` array
        - endpoint: `/get-suggestions?sort=latest`
    - ALL Web Services:
      - send back data in either JSON or XML depending on the value of the `accept` HTTP request header of a client
      - send back correct HTTP status code (`200`,`201`,`404` etc)
      - send back correct `content-type` response header
      - for HTTP `HEAD` requests from a client, the service will NOT send the response content, and instead send only the headers (and status code):
        - adding a `content-size` response header to such responses would be a nice touch, but is not required - https://stackoverflow.com/questions/2219526/how-many-bytes-in-a-javascript-string/29955838
  - <ins>HTML Pages (5):</ins>
    - #1 - Home Page:
      - "landing page" for API - should look nice
      - describes API
      - has documentation of API functionality
      - simple demonstration of API usage
      - example: 
        - **home.html**
        - gives examples of `/get-jokes` endpoints, with and without parameters
        - *shows a random joke from the "Get Jokes" API, the `q` only, every time the page is reloaded*
    - #2 - Input Page
      - HTML `<form>` for users to input data and send it to the **JSON "write" API** above
      - example: 
        - **suggestion.html**
        - *users can suggest data for the API by submitting a setup and punchline for a joke*
    - #3 - Admin Page
      - login functionality not required
      - shows the entire contents of the **User submitted data API (Read)** above
      - example:
       - **admin.html**
       - calls and displays `/get-suggestions?sort=latest`
    - #4 - App Page
      - demonstrates API (Web Service #1) in action
      - has controls to show all features of API
      - example:
        - **app.html**
        - calls `/get-jokes?limit=5&minrating=3`
    - #5 - Error Page
      - returned for no-existent endpoints
      - be sure to send the `404` HTTP status code
      - example:
        - **error.html**
  - <ins>Other Pages (3+):</ins>
    - at least one client-side JS page
    - at least one client-side CSS page
    - at least one client-side image
  - <ins>Server Code Style</ins>
    - multiple CommonJS code modules
    - all pages/files "served" by your Node.js server
    - all HTML/CSS/JS are in external files (i.e. loaded by the `fs` module, NOT hard-coded in code via `const`)
  - <ins>Client Code Style</ins>
    - VanillaJS
    - ES6 Modules
    - Global Navgation System (HTML)
    - External CSS file(s)


<hr>

## VI. Rubric

- App should go above and beyond in order to get an A.

<hr>

## VII. Deliverables

### VII-A. Prototype

- Should at least be the core experience with some of the API working. The full API might not be ready and the app may not be finished, but the main part of the experience should be testable
- Submission:
  - Working version must be accessible online through Heroku
  - Final code must be pushed to Git repo
  - Final code must be zipped and submitted to the dropbox (without **node_modules**)
  - The following links in the submission comments

### VII-A. Final Version

- Final code must be pushed to Git repo
- Final code must be zipped and submitted to the dropbox (without node_modules)

Link to the Git repo (add me if necessary).
Link to CircleCI Build.
Link to cloud deployed app (Heroku).
Final:

Documentation:
README.md

Hand in documentation explaining the following:

What your site does and its purpose.
What part of your app does the API handle?
What went right and what went wrong?
If you were to continue, what would you do to improve your app?
How did you go above and beyond?
Code:

Must be accessible online through Heroku (unless special arrangements have been made).
Final code should be submitted to Git repo.
Final code should be zipped and submitted to the dropbox (without node_modules).
The following links in the submission comments
Link to the Git repo (add me if necessary).
Link to CircleCI Build.
Link to cloud deployed app (Heroku).








