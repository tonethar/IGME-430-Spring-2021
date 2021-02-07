# Skill #8 - Adding developer "tooling"

## 0. Video & HW
- The video for this lecture, which walks through the notes, is here - [Essential Skills - Part VIII (20:48)](https://video.rit.edu/Watch/430-essential-skills-8)
- See the HW assignment at the bottom of the page (Part IV.)

<hr>

## I. Overview

- Today we are going to utilize some npm developer tools to our project. These 2 tools will dramatically improve your productivity:
  - https://www.npmjs.com/package/nodemon
  - https://www.npmjs.com/package/eslint

<hr>

## II. nodemon

- Getting sick or having to *quit* (**control-c**) and *restart* (`npm start`) your server constantly - every time you make a change to your code?
  - You should be!
- Make your developer life easier!
  - https://www.npmjs.com/package/nodemon
  - *nodemon is a tool that helps develop node.js based applications by automatically restarting the node application when file changes in the directory are detected.*
- Let's go ahead and try out `nodemon` on some of our previous code

### II-A. Start code

- Your start code is going to be the "Done" version of your [Skill #6 - First Node Web Service](6-first-node-web-service.md)
- Navigate to a folder on your hard drive, and in your console app of choice:
  - `git clone <url>` your **first-web-service** repository (or **first-web-service-heroku**, or whatever you called it) from GitHub
  - `cd` into the cloned folder so that it now the *cwd*
  - `npm start` to be sure that it works as before
  - now **control-c** to quit the server


### II-B. Install nodemon

- To install the `nodemon` package, type `npm i --save-dev nodemon`
  - this will download the `nodemon` files and put them into a **node_modules** folder
  - this will also add a "devDependencies" key to your **package.json** file
  - note that for developer dependencies, the `--save-dev` flag IS required, and is what causes the "devDependencies" key to be added to the **package.json** file
  - this will also create a **package-lock.json** file - `npm` uses this file - you will need to commit it later on
- Take a look in your **node_modules** folder to see all of the files that have been downloaded
- Now open your **package.json** file to verify that there is now a "devDependencies" key 

### II-C. Utilize nodemon

- Add a "nodemon" key to your  **package.json** "scripts" key - you can put this right after "start" - it looks like this:
  - `"nodemon" : "nodemon ./src/index.js -e js,html,css"`
  - what this command means:
    - every time `nodemon` detects that a file has been modified and changed, it will quit `node`, and then restart the app by running `./src/index.js`
    - by default, `nodemon` will "watch" all of the files and folders in the current directory, and any file and folders in sub-directories (BTW - this behavior can be changed with the `--watch` flag)
    - the file extensions that `nodemon` will watch in this case are `.js`, `.html`, and `.css`

### II-D. Try it!

- Type `npm run nodemon` to launch the server. You should see something like this in the console:

```
[nodemon] 2.0.7
[nodemon] to restart at any time, enter `rs`
[nodemon] watching path(s): *.*
[nodemon] watching extensions: js,html,css
[nodemon] starting `node ./src/index.js`
Listening on 127.0.0.1: 3000
```

- Now make a change to **index.js**, you should see something like this in the console:

```
[nodemon] restarting due to changes...
[nodemon] starting `node ./src/index.js`
Listening on 127.0.0.1: 3000
```

- Cool! Trust us when we tell you that you will find this very helpful as you continue to write code in this class!

### II-E. Commit your changes

- We need to commit these *local* changes back to your *remote* repository
- Now that we have a massive **node_modules** folder, we want to be sure that we don't commit it to the repository
  - this is especially true in this case because Heroku will ignore any packages listed under "devDependencies" and will NOT download them when it builds your app - it doesn't need them!
- You DO have a **.gitignore** file, right?
  - If not, create one and add `node_modules` to the top of it
- Update your *local* git repository and commit your files
  - `git status` - to see your changes
  - `git add .` - to add these files to the local *staging area*
  - `git commit -m "Added nodemon to devDependency"` - to commit files in the staging area to the *local* repository
  - `git push` - to push the *local* repository changes to the *remote* repository
- Head up to GitHub and check your repository to be sure it's working
- Also check this app on Heroku, verify that it has uodated, and it should work as before (as mentioned above, Heroku will ignore the "devDependencies" and "nodemon" keys of **package.json**)

### II-F. Test your package.json file

- Once you are sure that you have properly pushed your local repository changes, go ahead and delete the cloned folder
- Now go ahead and `git clone <url>` the folder again, and `cd` into it
- Type `npm run nodemon`
  - ERROR! 
  - This is because you have not yet downloaded the `nodemon` files (the ones that go in the **node_modules** folder)
  - To download/install these `nodemon` files, type `npm install` (or just `npm i`)
  - `npm` will go ahead an automatically download all of the packages listed under the "devDependencies" and "dependencies" keys in the **package.json** file (we talked about this back in [Skill #4 - Hello Node](4-hello-node.md))
- Now type `npm run nodemon` again - now that the required packages have been installed, things should work like they did earlier
  
<hr>

## III. ESLint

- *ESLint is a tool for identifying and reporting on patterns found in ECMAScript/JavaScript code:*
  - https://www.npmjs.com/package/eslint
  - `ESLint` enforces code *style guides* - a style guide is a set of standards that outline how code should be written and organized
  - Companies generally frown on *idiomatic* code - most feel that no matter how large a developer team is, the code base should look like it was written by *one person* 
  - Style guides are created so developers can get up to speed on a code base quickly, and then write code that the other developers can easily understand
  - We will be using the *Airbnb JavaScript Style Guide* in this course - https://github.com/airbnb/javascript
  
### III-A. Installing ESLint with AirBnB
  
- make sure that you are still in the right *cwd*
- type `npm i --save-dev eslint eslint-config-airbnb eslint-plugin-import`
- wait for the install to complete
- now check your **node_modules** folder and the "devDependencies" key for changes
  
### III-B. Running ESLint

- modify the value of the "test" key of **package.json** to be `"echo \"Tests complete\""`
- add a "pretest" key (under "scripts") to **package.json** - give it a value of `"eslint ./src --fix"`
  - this will run `eslint` on all of the files in the **/src** folder, and "fix" them where possible
- Now run your tests by typing `npm run test` (or `npm test` as a shortcut)
- Now you will get an ERROR - eslint is looking for a configuration file!
- To create one, go ahead and type `eslint --init` - which creates an interactive program that asks questions:
  - **IMPORTANT:** if you get an error message `"bash: eslint : command not found".` - it's probably a `PATH` issue
    - Try typing `npx eslint --init` instead
  - ***IMPORTANT: THE ARROW KEYS MIGHT NOT WORK ON WINDOWS GITBASH:***
    - https://stackoverflow.com/questions/55753151/cant-use-arrow-keys-in-git-bash-windows
    - so use PowerShell, Visual Studio Code's terminal window, or [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?active) instead
- Follow the presets we use in the video:
  - *How would you like to use ESLint?* - **"To check syntax, find problems, and enforce code style"**
  - *What type of modules does your project use?*  - **"CommonJS (require/exports)"**
  - *Which framework does your project use?* - **"None of these"**
  - *Where does your code run?* - **"Node"**
  - *How would you like to define a style for your project?* - **Use a popular style guide**
  - *Which style guide do you want to follow?* - **"Airbnb (https://github.com/airbnb/javascript)"**
  - *What format do you want your config file to be in?* - **"JSON"**
  - *The config that you've selected requires the following dependencies - Would you like to install them now with npm?* - **"Yes"**
- You should now have a **.eslintrc.json** file (Reminder: Don't forget to eventually commit it to your repository!)

<hr>

- Here's some "bad code" to add to the top of **index.js**

```js
const name = "fred";
const car = {
  "make" :"Ford",
  "make" :"Ford",
};
```

<hr>

- Now type `npm test` again:
  - there will (probably) be many errors, but that depends on how closely your code followed ours
  
```
warning  Unexpected console statement               no-console
error    'name' is assigned a value but never used  no-unused-vars
error    'car' is assigned a value but never used   no-unused-vars
error    Duplicate key 'make'                       no-dupe-keys
error    Unexpected tab character                   no-tabs
error    Assignment to function parameter 'max'     no-param-reassign
error    Assignment to function parameter 'max'     no-param-reassign
error    Assignment to function parameter 'max'     no-param-reassign
warning  Unexpected console statement               no-console
warning  Unexpected console statement               no-console
warning  Unexpected console statement               no-console
warning  Unexpected console statement               no-console
error    Expected '===' and instead saw '=='        eqeqeq
error    Expected '===' and instead saw '=='        eqeqeq
warning  Unexpected console statement               no-console
```
  
  - Watch the video to see how we will:
    - fix the  `no-dupe-keys`, `no-tabs`, `no-param-reassign`, and `eqeqeq` errors
    - turn the  `no-unused-vars` *error* into a *warning* by editing the **.eslintrc.json** file

### III-C. All fixed?

- You should see only warnings in the console


### III-D. Commit your changes!
- `git status`
- Commit these changes to your local repository, and then push them to the remote repository:
  - don't forget about committing **.eslintrc.json**
- Double-check that everything still works on Heroku

<hr>

## IV. Homework & Submission

- In the mycourses dropbox:
  - ZIP and POST the updated **first-web-service** folder
  - We will be running `npm test` on this
- In the comments field of the dropbox, type:
  - the URL to your GitHub repository
  - the working URL to your functional `abc1234-first-web-service` page on Heroku - just the main page this time
  - IMPORTANT - DO NOT post your Heroku control panel link - no one but you can see that page

<hr><hr>

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
|   [Skill #7 - Create a "Random Joke" JSON Web Service](7-create-random-joke-web-service.md) |  [**IGME-430**](../) | [Skill #9 - Continuous Integration with CircleCI](9-continuous-integration.md)
