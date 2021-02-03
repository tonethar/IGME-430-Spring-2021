# Skill #4 - Hello Node


## 0. Video & HW

- The video for this lecture, which walks through the notes, is here --> [Essential Skills - Part IV (15:12)](https://video.rit.edu/Watch/430-essential-skills-4)
- See the HW assignment at the bottom of the page (Part VII.)

<hr>

## I. What is Node.js?
  
- https://nodejs.org/en/
- Server-side JavaScript, built on [Chrome's V8 JavaScript Engine](https://v8.dev/)
  - V8 is highly performant, and compiles every JavaScript code snippet into native instructions
- Node.js can be used to create:
  - servers
  - desktop applications (like Discord, VS Code, Brackets, etc built with [Electron](https://www.electronjs.org/)
  - mobile apps
  - embedded systems (Rasberry Pi, Arduino, etc)
- Node.js runs JavaScript WITHOUT all of the browser restrictions we know and hate:
  - full OS access
  - full hardware access
  - unrestricted threads
- Other advantages:
  - can use same language (JS) on client & server
  - a massive ecosystem of libraries can be downloaded via package managers like [npm](https://www.npmjs.com/)
    - npm allows us to discover, download and publish *packages* (aka "libraries") from https://www.npmjs.com
  
<hr>

## II. Install Node.js
- If you are on your own computer (as opposed to a lab machine) you will need to install Node.js, as well as npm (Node Package Manager) - the installer linked below should install them both for you
  - Here's the installer link --> https://nodejs.org/en/
  - Be sure to install the LTS ("Long Term Support") version
- After it is installed, you need to verify that `node` and `npm` (node package manager) were installed. Go ahead and open up GitBash (or PowerShell, or Terminal on a Mac) and type:
  - `node -v`
  - `npm -v`
- You should see the version numbers of each application logged out

<hr>

## III. "Hello Node" Demo Start

- Today, to get you started with node, we will create a simple node app and run it *locally*
- (Next time we will run a node app locally, and then push it to Heroku so that it runs out on the Internet in the "cloud")
- Let's get started!

1) Create a folder named **hello** and make it your *cwd* (by `cd`ing into it)

2) Inside of the **hello** folder, create a file named **index.js**

3) Put the following code into **index.js** --> `console.log("Hello 430");`

4) Now run the code by typing `node ./index.js` on the command line:
    - you should see `"Hello 430"` log out to the console

<hr>

## IV. Add a package.json file

- Soon we will be adding an external library to this app so that we can utilize its capabilities
- **package.json** files contain *metadata* about your node project - analagous to a [C Makefile](https://en.wikipedia.org/wiki/Makefile)

1) Type `npm init` to launch and interactive prompt that will create a **package.json** file for us based on our answers

    - NOTE: alternatively, you can type in `npm init -y` to create a **package.json** with default values without using the interactive prompts, and then just edit the file manually

2) We will mostly go with the default values (by pressing enter), but will add values for `description`, `author`, and `keywords`

3) Here is what the file looks like:

```json
{
  "name": "hello",
  "version": "1.0.0",
  "description": "first node and npm demo",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "430",
    "week1"
  ],
  "author": "Tony",
  "license": "ISC"
}
```

- Note that this files is in JSON, where the *keys* (such as "name") must be quoted strings, and the values are legal JSON data types such as strings, objects, and arrays (booleans and numbers and null are also legal)

<hr>

## V. Edit the package.json file

1) First we will test the **package.json** file by typing `npm test`

    - this runs the contents of the "test" key (under the "scripts" key) of the **package.json** file
    
2) Now we will modify the "test" key to instead log out "No tests required"

3) Now we will create a "start" key under the "scripts" key with a value of "node ./index.js"

4) Now test the start key by typing `npm start` on the command line - this should launch index.js awhich then logs out `Hello 430` to the console

5) Finally, we'll add an "engines" key to the package.json file - this is important when the app runs on Herolu, and when we use *Continuous Integration* tools like [CircleCI](https://circleci.com/enterprise-trial-install) (coming soon!)

6) What happens when you add "bad" JSON to your **package.json** file?

<hr>

## VI. Utilize a external library (aka "package")

1) Here we will utilize the *Nano ID* package, which is used to generate [UUIDs](https://en.wikipedia.org/wiki/Universally_unique_identifier) - docs and usage example is here --> https://www.npmjs.com/package/nanoid

2) Let's utilize the `nanoid` library in **index.js** - go ahead and delete the old code and make it look like this:

```js
const {nanoid} = require('nanoid'); // import the library using CommonJS syntax
const uuid = nanoid();
console.log(`Here's a UUID for you: ${uuid}`);
```

- quick aside: what is this `require()` function?
- believe it or not, Node DOES NOT support ES6 module imports by default:
  - for example ES6 module style code such as `import { nanoid } from 'nanoid'` is not supported unless you declare in the **package.json** file that your code is using ES6 modules
- in this class we will mostly be using the pre-ES6 [CommonJS](https://nodejs.org/en/knowledge/getting-started/what-is-require/) syntax (on the server-side) to import libraries and create code modules - there are two symbols that are used:
  - `require()`function
  - `exports` object
- we will be seeing a lot of this module style during the semester, so don't worry about it too much right now


3) `npm start` - oops something went wrong!

![screenshot](_images/ss-19.png)

  - on the client side, we can "import" a library (for example, RiTa.js), and the browser will take care of downloading it for us
  - but on the server side, WE need to download the libray files ourselves

4) To download the `nanoid` library files and add an entry to the "dependencies" key of our **package.json** file, type:
  
    - `npm install --save nanoid` :
      - what happened when typed the above command in?
      - the `nanoid` library files were downlaoded by `npm` into a **node_modules** folder
      - a "dependencies" key was added to our **package.json** file
      - go look for both of these things now!
    
5) Now run the app by typing `npm start` again - it should run and then log a UUID to the console.

```
Here's a UUID for you: kaTb4hL2IvqoM05lXTcIX
```

6) Now try deleting the **node_modules** folder and typing `npm start` again - ERROR!

    - BTW - we ALWAYS delete the **node_modules** folder before posting code to myCourses or commiting it to GitHub
    - Why? Because they take up a lot of space, and whenever we post a node project to Heroku that has a **package.json** file, Heroku will go ahead and download fresh copies of all of the packages listed in the "dependencies" key for us

7) But because `nanoid` is listed as a "dependency" in the **package.json** file, we only have to type in `npm install` to re-download the `nano` package. This means we don't have to specify a package after it has been added to the "dependencies". This is a good thing because you are going to see very soon that we often need to be using 5 to 10 packages on a typical project, so re-typing all of the package names everytime we need to rebuild the project would be onerous and error prown.

8) Finally, the command we typed in step #4 above could be shortened to this - `npm i nanoid` :

    - why?
    - `i` is short for `install`
    - starting with Node version 5.0, `--save` is  no longer required to save packages to the "dependencies" key, this is now done by default

9) BTW - this was not mentioned in the companion video - `npm init` also generates a **package-lock.json** file - the file is needed by npm so you will commit it to your respository - but you will never edit it - you can read about its purpose here --> https://docs.npmjs.com/cli/v6/configuring-npm/package-lock-json

<hr>

## VII. HW & Submission (Out of 10 points)

- In the mycourses dropbox:
  - ZIP and POST the **hello** folder (with the **node_modules** folder deleted)
  - take a screenshot of your shell session (showing `npm start`, `npm install --save nanoid` and `npm install`) and post it to the dropbox
- In the comments section of the dropbox, type the answers to the following questions:
  - #1 - True or False. The Chrome V8 engine compiles JavaScript instructions down to native code and is thus very fast
  - #2 - True or False.  node/npm can be used to create desktop and mobile apps
  - #3 - What kind of information/data goes into a **package.json** file?
  - #4 - What are the 2 things that happen when you install a package with `npm install package-name`?
  - #5 - What command would we type to "re-install" a project's package dependencies?
- Rubric:
  - wrong answer/missing answer to question -1
  - **node_modules**  NOT deleted -3
  - missing screenshot -5

<hr><hr>

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
|   [Skill #3 - Command-line Git & Cloning Repositories](3-command-line-git.md) |  [**IGME-430**](../) | [Skill #5 - First Node Web Server](5-first-node-web-server.md)
