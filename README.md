# IGME 430-01 - *Rich Media Web App Development II.*

- Spring 2021

## I. Mission

<blockquote>
"Students will create and deploy <i>full-stack</i> web apps that are <i>secure</i> and <i>persistent</i>, while following <i>industry standard development practices</i>"
</blockquote>
  
- *Full-stack* means that the app has both client-side and server-side components
- *Secure* means that the apps will utilize a login system, encryption, and data validation
- *Persistent* means that app data will be cached both locally and in "the cloud" so that it can be recovered by the user at a later date
- *Industry standard development practices* means utilizing common build tools and workflows (automatic server rebooting, automatic code analysis aka linting, continuous integration, transpiling et al), testing, version control, and implementing MV* software design patterns both "from scratch" and by using current popular frameworks

<hr><hr>

## II. Projects

### Project 1 - API Portal

- **A - Functionality**
  - <ins>Web Services (3):</ins>
    - #1 - Custom Web API (Read):
      - uses HTTP `GET` method
      - returns data in JSON format
      - public facing, and CORS is turned on
      - takes at least 2 parameters
      - example: 
        - *"Get Jokes" API with `limit` and `minrating` parameters*
        - endpoint: `/get-jokes?limit=5&minrating=3`
        - data stored in hard-coded array of object literals - `allJokes`
    - #2 - User submitted data API (Write):
      - uses HTTP `POST` method
      - takes at least 2 body parameters
      - response:
          - sends back proper HTTP status codes ex. `201 Created`
          - send back created resource
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
      - sends back data in either JSON or XML depending on `accept` request header of client
      - sends back correct HTTP status code (`200`,`201`,`404` etc)
      - sends back correct `content-type` response header
      - for HTTP `HEAD` requests from a client, will NOT send the response content, and instead send only the headers (and status code):
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
- **B - Client-side Technologies**
  - VanillaJS
- **C - Server-side technologies**
  - "stock" Node.js - Express or similar NOT allowed
  - ephemeral server-side data
- **D - Developer Tools**
  - `eslint`
  - `nodemon`
  - Continuous Integration via CircleCI

<hr>

### Project 2 - Product/Service App VueJS

- Functionality
- Client-side Technologies
  - Vue.js
- Server-side technologies
  - Express
  - MongoDB (NoSQL)
- Developer Tools
- Server Code Style:
  - MVC - router style

<hr>

### Project 3 - Product/Service App ReactJS

- Functionality
- Client-side Technologies
  - React
- Server-side technologies
  - Express
  - MongoDB + Mongoose
  - User Authentication
  - In Memory Datastore/caching - Redis
- Developer Tools
  - Testing (Assertions)

<hr>

## III. Tools

- Node.js / npm:
  - https://nodejs.org/en/download/
  - https://www.npmjs.com/
- Chrome Developer Tools - https://developers.google.com/web/tools/chrome-devtools
- JSONViewer - https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh?hl=en-US
- Console App:
  - Terminal (Mac OS)
  - GitBash - https://gitforwindows.org/
  - Powershell
- Text Editor:
  - BBEdit (Mac OS)
  - Notepad++
- IDE:
  - Visual Studio Code

<hr>

## IV. Course Expectations

- Be on time to the Zoom meetings:
  - we only have 50 minutes of meeting time
  - a 2:30PM start is 2:30:00, NOT 2:30:59
  - recommendation: start logging into Zoom about 5 minutes before class
- Be prepared to participate in class
- Be prepared to *work* on assignments during class time:
  - you CAN get a lot done in even 20 minutes, so long as you are prepared
  - I WILL stay after every class meeting for questions, until 4:00PM, so that is another good time to work on HW
- The Professor has limited availability late at night and on the weekends:
  - that means if you anticipate there is any chance you will have questions, you should start assignments *early*
