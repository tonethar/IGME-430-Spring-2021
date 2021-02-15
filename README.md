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

## II. Projects (2 or 3)

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
      - send back data in either JSON or XML depending on the value of the `accept` HTTP request header of a client
      - send back correct HTTP status code (`200`,`201`,`404` etc)
      - send back correct `content-type` response header
      - for HTTP `HEAD` requests from a client, the service will NOT send the response content, and instead send only the headers (and status code):
        - adding a `Content-Length` response header to such responses would be a nice touch, but is not required - https://stackoverflow.com/questions/2219526/how-many-bytes-in-a-javascript-string/29955838
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

### Project 2 - Product/Service App VueJS (or BIG HW Assignments)

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

### Final Project - Product/Service App ReactJS

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
  - [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701)
- Text Editor:
  - BBEdit (Mac OS)
  - Notepad++
- IDE:
  - Visual Studio Code (later on in the semester we will use this exclusively)

<hr>

## IV. Course Expectations

***This course can be challenging-let's DISCUSS***

### IV-A. Be on time to the Zoom meetings:
  - we only have 50 minutes of meeting time
  - a 2:30PM start is 2:30:00, NOT 2:30:59
  - recommendation: start logging into Zoom about 5 minutes before class
  - Be prepared to participate in class
  - Be prepared to *work* on assignments during class time:
  - you CAN get a lot done in even 20 minutes, so long as you are prepared

### IV-B. Getting help/Communicating with Prof
  - this is not an easy course, and if you skip HW assignments and/or fall behind in the work you will likely find it difficult to catch up
  - which also means that if you have questions and/or are stuck on anything, ask for help ***immediately***
  - I WILL stay after the Monday & Wednesday class meetings for questions, until 4:00PM, so that is another good time to work on HW
  - I have limited availability late at night and on the weekends
    - that means if you anticipate there is any chance you will have questions, you should start assignments *early*
  - Discord is a great resource, but I won't be logged into in constantly, so the quickest way to contact me most of the time is via email

<a id="asking-questions" />

### IV-C. Asking Effective Questions
- The #1 rule in this class is to ASK QUESTIONS if you ever need clarification on anything. The #2 rule is to make the attempt to ask that question *effectively*
- What NOT to do:
  - "Professor, I tried to do the HW but I just get a blank screen when I run it. What did I do wrong?"
    - *With such a vague decription, it could be one of a thousand different things. At this point the prof will have to write you back and ask for more information. You should instead be more respectful of everyone's time and give more details in your first email*
  - "My code doesn't work. Here's the link to my GitHub repository - what did I do wrong?"
    - *Two issues here. It comes off as kind of lazy (what have you done to try to solve the problem yourself?), and sharing GitHub repository links on Discord is verboten*
  - "My code works fine on IE9 and Firefox Developer Edition, but not on Chrome, so it looks like a browser bug"
    - *More than likely it is YOUR code that is buggy, not the web browser*
- What you should DO:
  - Spend a reasonable amount of time debugging it yourself
    - https://www.cs.cornell.edu/courses/cs312/2006fa/lectures/lec26.html
  - Do a google search
  - Describe the problem, and document the observed behavior of the program with screen shots
  - Describe what fixes you attempted
  - In Discord, share only a *minimum* amount of your code - just enough to illustrate the issue
  - Let people know when and how you ended up fixing the issue!
- Answering Questions in Discord:
  - Be a good teacher - don't just give people the right answer - instead suggest debugging strategies or "gotchas"
- Links:
  - https://www.propublica.org/nerds/how-to-ask-programming-questions
  - https://www.freecodecamp.org/news/how-to-ask-good-questions-as-a-developer-9f71ff809b63/
  - http://www.catb.org/~esr/faqs/smart-questions.html
  - https://medium.com/@gordon_zhu/how-to-be-great-at-asking-questions-e37be04d0603
  
## V. Course Delivery

- ***Week 1 only:*** 
  - I am travelling and we will not meet on Zoom the rest of the week
  - I **WILL attempt** to be logged into Discord during our class time on Wednesday & Friday though, for questions
- The entirety of the Week 1 and Week 2 content has been prepared for you:
  - in myCourses look for the 9 "Core Skills" links, and the "Simple HTTP HW"
  - the Core Skills assignments have notes and short accompanying videos. Each one covers an important topic fundamental topic - we will go look at these now 
- ***Week 2:***
  - on MWF we will be reviewing the material from Core Skills #4 (*Intro to Node.js*) to Core Skills #9 (*Continuous Integration with CircleCI*), and getting you prepared for the "Simple HTTP HW":
    - IF you complete and post Core Skills #1-#9 early, I will *probably* excuse you from next Wednesday (2/3) and Friday's (2/5) classes (we'll talk about that Monday 2/1)
- Questions?

