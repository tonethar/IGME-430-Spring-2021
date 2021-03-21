# Week 8B Notes (3/17/21)

## I. Review

- Any questions on?:
  - [1 - Intro to express](../express/1-express-intro.md)
  - [2 - Express - Serving Static Files](../express/2-express-serving-static-files.md)
  - [3 - Express - POST requests](../express/3-express-post-requests.md)

<hr>

## II. Express Application Generator

### II-A. Get started
- The express application generator tool can be used to create an application skeleton:
  - docs --> https://expressjs.com/en/starter/generator.html
  - commands:
      - `express -h` - shows the help screen
      - `npx express-generator --view hbs` - generates the app skeleton, in this instance using https://handlebarsjs.com as the view rendering engine
      - if this doesn't work for you, there is a copy of the generated template in myCourses
 - let's install nodemon:
   - `npm i nodemon`
   - `"nodemon" : "nodemon -w . -e js,hbs ./bin/www"`

<hr>

### II-B. Creating service endpoints

- New endpoints are easy:

**routes/users.js**

```js
const users = [
  {
    first_name: "Betty",
    last_name: "Smith",
    id: 1
  },
  {
    first_name: "Bob",
    last_name: "Smith",
    id: 2
  },
  {
    first_name: "Billy",
    last_name: "Smith",
    id: 3
  }
];
/* GET users listing. */
router.get('/', function(req, res, next) {
  //res.send('respond with a resource');
  res.json(users);
});

router.get('/random', function(req, res, next) {
  res.json(users[Math.floor(Math.random() * users.length)]);
});
```

- To see these endpoints, check out:
  - http://localhost:3000/users/
  - http://localhost:3000/users/random

<hr>

### II-C. Server-side rendering

- In this app we are going to do server-side rendering via https://handlebarsjs.com
- Head to **routes/index.js** and **views/index.hbs** - we'll do this together


<hr>

## III. HW - First Express MVC

- [HW - First Express MVC](https://github.com/tonethar/IGME-430-Spring-2021/blob/main/hw-notes/HW-first-express-mvc.md)
- This is our "custom toolchain" - similar to what we just demoed above, but with differences
- There's a lot to talk about regarding this walkthrough/HW assignment

1) New *middleware* (mostly used in future examples):

    - https://www.npmjs.com/package/compression
    - https://www.npmjs.com/package/serve-favicon
    - https://www.npmjs.com/package/cookie-parser
    - and some middleware we've already seen:
      - http://expressjs.com/en/resources/middleware/serve-static.html
      - http://expressjs.com/en/resources/middleware/body-parser.html

2) Design Patterns
    - *dependency injection* in **router.js**:
      - [here is a good explanation of both *dependency injection* and *inversion of control*](https://www.freecodecamp.org/news/a-quick-intro-to-dependency-injection-what-it-is-and-when-to-use-it-7578c84fa88f/)
    - **router.js** also has all of our `app.get()` and `app.post()` routes defined:
      - but the code that is "controlling" each page is in **controllers/index.js**
      - and as we saw last time, POSTing data is now easy thanks to `body-parser`!
    - MVC:
      - **controllers/index.js** obviously contains the *controller* code
      - **views/** contains the *view* code (HTML in this case) - we will be doing server-side rendering of these pages next week
      - there's no *model* objects yet (soon!)
 

<hr>

## IV. HW
- [HW - First Express MVC](../hw-notes/HW-first-express-mvc.md):
  - due Friday night
  - completing it by Thursday night is the "get out of jail free" for this Friday's class
- HTTP Server Design SG (see myCourses)
- Database SG (see myCourses)


<hr><hr>

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**Week 8A Notes**](8A.md)   |  [**IGME-430 Home**](../README.md) | [**Week 9A Notes**](9A.md)
