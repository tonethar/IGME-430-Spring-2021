# Random Joke with tooling - checkoff

- Today you will add `nodemon`, `eslint` (code validation), and continuous integration (CircleCI) to your **random-joke** web service
- You built this app for [Skill #7 - Create a "Random Joke" JSON Web Service](../core-skills/7-create-random-joke-web-service.md)

## I. Install and test `nodemon`
- `git clone <url-to-random-joke-repository>`
- test it to be sure everything still works:
  - `npm i` - *not actually needed, yet, because this project doesn't yet have "dependencies" (but it will have "devDependencies", in just a bit)*
  - `npm start`
  - test these endpoints:
    - http://localhost:3000/
    - http://localhost:3000/random-joke
- add the **nodemon** capabilities we covered in [Skill #8 - Adding developer "tooling"](../core-skills/8-add-developer-tooling.md) (be sure to review these notes so you don't miss any steps):
  - install the `nodemon` package (this will also add a "devDependencies" key
  - now check for a **node_modules** folder and a "devDependencies" key in **package.json** to see the changes
  - add a `"nodemon"` script to your **package.json**
  - `npm run nodemon` to test your script:
    - make some minor changes to **index.js** and be sure that the server reboots everytime you save
 - make sure that your endpoints work as before, and move on
  
<hr>

## II. Install and test `eslint`

- Add the **eslint** capabilities we covered in the **ESLint** section of [Skill #8 - Adding developer "tooling"](core-skills/8-add-developer-tooling.md) (be sure to review those notes so you don't miss any steps)
- `npm run test` (or `npm test` for short) will run your "pretest" script, followed by your "test" script
- Fix any code errors - you will probably see the `eqeqeq` error, as well as some `no-tabs` - these are easy to fix

<hr>

## III. Add CircleCI
- Add Continuous Integration to your project by going through the steps here:
  - [Skill #9 - Continuous Integration with CircleCI](../core-skills/9-continuous-integration.md)
  - don't clone your project again, just use what we have
  - you should be able to re-use the **config.yml** file from the HW if you want to (don't forget to put it in a **.circleci** folder!)
  - commit your local changes to GitHub (`git status`, `git add .`, `git commit -m`, `git push`)
  - set everything up in CircleCI's web interface
  - head to this project's Heroku control panel and check the "Wait for CI to pass before deploy" checkbox
  - once all the tests run and pass on CircleCI (you might have to "push" a change to GitHub one more time to get CircleCI to run), you should see the "Green checkmark" on your GitHub repository

<hr>

## IV. Commit your changes

- we added `nodemon` and `eslint` and CircleCI so we have made some changes to existing files, and added some new files - these need to be committed to our local repository, and then pushed to the remote repository:
  - **.eslintrc.json**
  - **.circleci/config.yml**
- BTW - You DO have a **.gitignore** file right?
  - with `node_modules` typed at the top of it?
  - and it HAS already been committed to your repository?
- Do one last `git status` to be sure you are up to date with the remote repository:
  - but you should have already committed all of these files, above when you set up CircleCI

<hr>

## V. Submission

- In the mycourses dropbox:
  - ZIP and POST the updated **random-joke** folder
  - we will be running `npm test` and `npm run nodemon` on this
- In the comments field of the dropbox, type:
  - the URL to your GitHub repository:
    - we will be looking for the "green checkmark" to confirm that CircleCI passed (i.e. it ran your `npm test` and passed)
  - the working URL to your functional "random-joke" page on Heroku - just the main page link 
  - IMPORTANT - DO NOT post your Heroku control panel link - no one but you can see that page

