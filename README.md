# IGME-430-01 (Spring 2021)

## I. Mission

<blockquote>
"Students will create and deploy <i>full-stack</i> web apps that are <i>secure</i> and <i>persistent</i>, while following <i>industry standard development practices</i>"
</blockquote>
  
- *Full-stack* means that the app has both client-side and server-side components
- *Secure* means that the apps will utilize a login system, encryption, and data validation
- *Persistent* means that app data will be cached both locally and in "the cloud" so that it can be recovered by the user at a later date
- *Industry standard development practices* means utilizing common build tools and workflows (automatic server rebooting, automatic code analysis aka linting, continuous integration, transpiling et al), testing, version control, and implementing MV* software design patterns both "from scratch" and by using current popular frameworks

<hr>

## II. Projects

### Project 1 - API Portal

- Functionality
  - JSON Custom Web API (Read only):
    - uses HTTP `GET` method
    - public facing, and CORS is turned on
    - takes at least 2 parameters
    - example: 
      - *"Get Jokes" API with `limit` and `minrating` parameters*
      - endpoint: `/get-jokes?limit=5&minrating=3`
  - JSON "write" API
    - uses HTTP `POST` method
    - takes at least 2 body parameters
    - stores data in hard-coded array of object literals - let's call it `dataArray` for now 
    - sends back proper HTTP status codes
    - example: 
      - *"Suggest Joke" API with `q` and `a` parameters*
  - HTML Home Page
    - documentation of API functionality
    - simple demonstration of API usage
    - example: 
      - *shows a random joke from the "Get Jokes" API, the `q` only, every time the page is reloaded*
  - HTML Suggestion Page
    - HTML `<form>` for users to input data and send it to the **JSON "write" API** above  - example: *users can suggest data for the API by submitting a setup and punchline for a joke*
  - HTML Admin Page
    - login functionality not required
    - shows the 
  - Server Code
    - multiple CommonJS code modules
    - all pages/files "served" by your Node.js server
  - Client Code
    - VanillaJS
    - ES6 Modules
    - Global Navgation System (HTML)
    - External CSS file(s)
- Client-side Technologies
  - VanillaJS
- Server-side technologies
  - ephemeral server-side data
- Developer Tools
  - `eslint`
  - `nodemon`
  - Continuous Integration via CircleCI

### Project 2 - Product/Service App VueJS

- Functionality
- Client-side Technologies
  - Vue.js
- Server-side technologies
  - Express
  - MongoDB (NoSQL)
- Developer Tools

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
