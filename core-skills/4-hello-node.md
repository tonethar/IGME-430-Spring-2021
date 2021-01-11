# Skill #4 - Hello Node


## I. What is Node.js?
  
- https://nodejs.org/en/
- Server-side JavaScript, built on [Chrome's V8 JavaScript Engine](https://v8.dev/)
  - V8 is highly performant, and compiles every JavaScript instruction into native instructions
- Node.js can be used to create:
  - servers
  - desktop applications (like Discord, VS Code, Brackets, etc built with [Electron](https://www.electronjs.org/)
  - embedded systems (Rasberry Pi, Arduino, etc)
- Node.js runs JavaScript WITHOUT all of the browser restrictions we know and hate:
  - full OS access
  - full hardware access
  - unrestricted threads
- Other advantages:
  - can use same language on client & server
  - massive ecosystem of libraries can be downloaded via package managers like [npm](https://www.npmjs.com/)
  
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

1) Create a folder named **hello** and make it your *cwd* (by `cd`ing into it)

2) Inside of the **hello** folder, create a file named **index.js**

3) Put the following code into **index.js** --> `console.log("Hello 430");`

4) Now run the code by typing `npm ./index.js` on the command line - you should see `Hello 430` log out to the console

<hr>

## IV. Add a package.json file

- Soon we will be adding a library to this app () so that we can utilize its capabilities
- **package.json** files contain *metadata* about your node project - analagous to a C Makefile 

1) Type `npm init` to launch and interactive prompt that will create a **package.json** file for us based on our answers

  - NOTE: you can alternatively type in `npm init -y` to create a **package.json** with default values without using the interactive prompts, and then just edit the file manually

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



<hr><hr>

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
|   [Skill #3 - Command-line Git & Cloning Repositories](3-command-line-git.md) |  [**IGME-430**](../) | Skill #5 TBA
