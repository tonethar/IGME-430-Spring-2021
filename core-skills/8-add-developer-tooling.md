# Skill #8 - Adding developer "tooling"

## I. Overview

- Today we are going to utilize some npm developer tools to our project:
  - https://www.npmjs.com/package/nodemon
  - https://www.npmjs.com/package/eslint

<hr>

## II. nodemon

- Getting sick or having to *quit* (**control-c**) and *restart* (`npm start`) your server constantly - every time you make a change to your code?
  - You should be!
- Make your developer life easier!
  - https://www.npmjs.com/package/nodemon
  - *nodemon is a tool that helps develop node.js based applications by automatically restarting the node application when file changes in the directory are detected.*
- Let's go ahead and try out nodemon on some previous code

### II-A. Start code

- Your start code is going to be the "Done" version of your [Skill #6 - First Node Web Service](6-first-node-web-service.md)
- Navigate to a folder on your hard drive, and in your console app of choice:
  - `git clone <url>` your **first-web-service** repository (or **first-web-service-heroku**, or whatever you called it) from GitHub
  - `cd` into the cloned folder so that it now the *cwd*


### II-B. Install nodemon

- To install the `nodemon` package, type `npm i --save-dev nodemon`
  - This will download the `nodemon` files and put them into a **node_modules** folder
  - This will also add a "devDependencies" key to your **package.json** file
  - Note that for developer dependencies, the `--save-dev` flag IS required, and is what causes the "devDependencies" key to be added to the **package.json** file
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
- Update your *local* git repository and commit your files
- You DO have a **.gitignore** file, right?
  - If not, create one and add `node_modules` to the top of it
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



<hr><hr>

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
|   [Skill #7 - Create a "Random Joke" JSON Web Service](7-create-random-joke-web-service.md) |  [**IGME-430**](../) | Skill #9 - TBA
