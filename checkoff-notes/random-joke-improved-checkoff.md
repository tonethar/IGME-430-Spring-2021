# Random Joke Improved - checkoff

- Today you will add nodemon, unit testing, and continuous integration to your **random-joke** web service
- You built this app for [Skill #7 - Create a "Random Joke" JSON Web Service](../core-skills/7-create-random-joke-web-service.md)

## I. Install and test `nodemon`
- `git clone <url-to-random-joke-repository>`
- test it to be sure everything still works:
  - `npm i` - *not actually needed, yet, because this project doesn't yet have "dependencies" (but it will have "devDependencies", in just a bit)
  - `npm start`
  - test these endpoints:
    - http://localhost:3000/
    - http://localhost:3000/random-joke
- add the **nodemon** capabilities we covered in [Skill #8 - Adding developer "tooling"](core-skills/8-add-developer-tooling.md) (be sure to review these notes so you don't miss any steps):
  - install the `nodemon` package (this will also add a "devDependencies" key
  - add a `"nodemon"` script to your **package.json**
  - `npm run nodemon` to test your script:
    - make some minor changes to **index.js** and be sure that the server reboots everytime you save
  
<hr>

## II. Install and test `eslint`

<hr>

## III. Submission

