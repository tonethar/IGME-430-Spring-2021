# DomoMaker HW Overview

- DomoMaker is a 5-part assignment where you will use React, Mongo/Mongoose, and Redis to create a web application that has the capability to create persistent data in our MongoDB cloud accounts, as well as login/logout capabilities for administrative "super users"
- The PDFs for all 5 parts are in myCourses

**Overview**

- [I. DomoMaker-A](#A)

- [II. DomoMaker-B](#B)

- [III. DomoMaker-C](#C)

- [IV. DomoMaker-D](#D)

- [V. DomoMaker-E](#E)

- [Final Project - Product/Service Site - React](#p2)

<a id="A"></a>

<hr>


## I. DomoMaker-A 

<a id="domomaker-a-tips"></a>

### I-A DomoMaker-A Tips and Hints
1) The PDF of the assignment is in myCourses

<hr>

2) The start code is here: https://github.com/IGM-RichMedia-at-RIT/DomoMaker-A-Start - because you will be posting this to Heroku, you might want to *fork* the repository and then `git clone` it (rather than download the ZIP like the instructions say)

<hr>

3) To get rid of those annoying warnings, and to make sure that Heroku uses the correct version of node and npm, set the "engines" keys of **package.json**

  - Typing `node -v` and `npm -v` in the console will give you the versions you are building with (*semantic versioning* is `major.minor.patch`)  Then you replace the last digit with an `x` to specify that the latest patch should be used - for example:

```js
"engines": {
    "node": "15.4.x",
    "npm": "7.6.x"
  },
```

**Reference:**

- https://devcenter.heroku.com/articles/node-best-practices
- https://nodejs.dev/learn/semantic-versioning-using-npm
  
<hr>

4) You will need to add an updated Babel library (otherwise, this will break on Heroku):

  - https://www.npmjs.com/package/@babel/compat-data
  - and run this command to install it: `npm i @babel/compat-data`
  - don't forget to then install everything else with `npm i`

<hr>

5) If you do NOT have a local instance of MongoDB running, just use your cloud account like we did on the Simple Models HW:

  - comment out this line of code: 
    - `const dbURL = process.env.MONGODB_URI || 'mongodb://localhost/DomoMaker';`
  - and replace it with this one - changing the placeholder values to instead reflect your actual Mongo Cloud login and password:
    - `const dbURL = 'mongodb+srv://MY_CLOUD_LOGIN:MY_CLOUD_PASSWORD@cluster0.bcwxq.mongodb.net/DomoMaker';`
  - if the `dbURL` connection string is invalid in some way (bad username or password for example) - the app will throw an error in the Node console


<hr>

### I-B. DomoMaker-A Assignment Walkthrough (we will talk about this in class)

- The architecture of this app is very similar to the *Simple Models* HW
  - **app.js**  loads the app dependencies and starts up the [express](https://www.npmjs.com/package/express) server
  - **router.js** calls the various routes with code defined in the **controllers/** folder - it also illustrates *dependency injection*
  - a **views/** folder contains [handlebars](https://handlebarsjs.com/) templates of the site's three pages (**app**, **signup**, **login**)
  - a **models/** folder that contains [mongoose](https://www.npmjs.com/package/mongoose) models (one per file) such as `Account` and (coming soon!) `Domo`
    - we add "class" methods to these models with the `statics` property
  - MVC in action:
    - note that when a user comes to the site, the router tells a ***controller*** to render the proper ***view***
    - when the user interacts with a ***view*** (for example signing up for a new account and clicking the Submit button), a message (endpoint) is routed back to the relevant ***controller***
    - the ***controllers*** will call the appropriate methods defined in the ***models***, and then render (draw) the ***views***
- Note: the **client.js** code is all [jQuery](https://jquery.com/):
  - why? `jQuery.animate()` I guess ...
    - here's a nice overview - [jQuery Fundamentals - jquery Basics](http://jqfundamentals.com/chapter/jquery-basics)
  - also, the **client.js** code is actually getting *transpiled* into ES5 by the server (utilizing Babel) and stored in **hosted/bundle.js**
- Create a user account (name and password) with **signup.handlebars**
  - `<input id="pass" type="password" name="pass" placeholder="password"/>`
  - note that the `type` is [`"password"`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/password)
  - **models/Account.js** is a mongoose model for the user's account
    - properties are `username`,`salt`,`password` (encrypted), `createdDate`
    - we encrypt the typed in password with node's built-in **crypto** library:
      - https://nodejs.org/api/crypto.html#crypto_crypto_pbkdf2_password_salt_iterations_keylen_digest_callback
      - https://nodejs.org/api/crypto.html#crypto_crypto_randombytes_size_callback
  - **controllers/Account.js** uses `signup()` to call `AccountModel.generateHash()` and generate an encrypted password
  - password encryption:
    - clear text:
      - https://simple.wikipedia.org/wiki/Cleartext
      - https://www.theverge.com/2019/4/18/18485599/facebook-instagram-passwords-plain-text-millions-users
    - encryption
      - https://www.howtogeek.com/howto/33949/htg-explains-what-is-encryption-and-how-does-it-work/
      - https://blueimp.github.io/JavaScript-MD5/
      - https://md5calc.com/hash/md5/12345678
    - rainbow tables:
      - https://www.geeksforgeeks.org/understanding-rainbow-table-attack/
      - https://en.wikipedia.org/wiki/Rainbow_table
    - salt
      - https://security.stackexchange.com/questions/17421/how-to-store-salt
      - https://security.stackexchange.com/questions/100898/why-store-a-salt-along-side-the-hashed-password
      - https://security.stackexchange.com/questions/211/how-to-securely-hash-passwords
  - Mongo database
    - locally you will be using `mongod` (maybe), and on Heroku you will be using your MongoDB cloud account
    - you will be able to see the following in a mongo client (`mongo` in Terminal/Powershell or the **MongoDB Compass** app):
      - the *database name* is set via `dbURL` (in **app.js**) and is `"DomoMaker"`
      - the *collection* is named `"accounts"` and is autogenerated by `mongoose` in **models/Account.js**
      - each user is represented by a *document* in the `accounts` collection
      - handy mongo commands you can use while you are debugging & testing:
        - `show dbs`
        - `use DomoMaker`
        - `show collections`
        - `db.accounts.find().pretty()` // show all documents in the accounts collection
        - `db.accounts.remove({})` // delete all documents in the accounts collection
- Login to an existing account with **login.handlebars**


<a id="B"></a>

<hr>


## II. DomoMaker B - Assignment Walkthrough

1) DomoMaker-B:
  - See myCourses for PDF and dropbox/due date
  - To get rid of the "circular dependency" warning - update your mongoose version in **package.json** - `"mongoose": "^5.12.3"` - and then run `npm i`
  - Comment out the following line in **models/Account.js** (with mongoose 5, we don't need it anymore):
    - `mongoose.Promise = global.Promise;`
  - Typos in PDF:
    - Near the top of page 6, delete this line (with mongoose 5, we don't need it anymore):
      - `mongoose.Promise = global.Promise;`
    - Bottom of page 6, should be `createdDate` NOT `createdData`
    - Near top of page 7, get rid of semicolon on this line `owner: convertId(ownderId)`
    - Bottom of page 7, regarding #12, a clarification. In **client.js**, the jQuery code that is called when the `#makeDomoSubmit` button is clicked is triggered by this: `$("#domoForm").on("submit", ...`
    - Bottom of Page 8, regarding #15, both lines of code are new
    - Clarification - the code for both #15 & #16 will go into **controllers/Domo.js**
  - Make sure that you create a new repository (and Heroku app) for each version of DomoMaker. I will be grading/checking these off very quickly, so you will be able to delete the old Heroku apps very quickly if need be
  - What's new:
    - HTTP *sessions* keep track of who is logged in
    - you can now add Domos to the database, "owned" and only visible to the current logged in user
    - multiple domos can have the *same name* (unlike the HW where according to the schema, the `Cat` documents have to have `unique` names
    - working version here: https://domomaker-b-2201.herokuapp.com/
    - handy mongo commands you can use while you are debugging & testing:
      - `show dbs`
      - `use DomoMaker`
      - `show collections`
      - `db.accounts.find().pretty()` // show all documents in the accounts collection
      - `db.accounts.remove({})` // delete all documents in the accounts collection
      - `db.domos.find().pretty()` // show all documents in the domos collection
      - `db.domos.remove({})` // delete all documents in the domos collection
    - you also might want to completely get rid of ("drop") a collection - in particular if you changed the associated mongoose schema of the documents
      - `db.accounts.drop()` // drop accounts collection which deletes the index and all documents in that collection
      - `db.domos.drop()` // drop domos collection which deletes the index and all documents in that collection

<hr>

2) HTTP sessions

- HTTP sessions store *per-user* data on the server, and keep the "key" to that data stored in the user's browser, as a cookie
- https://stackoverflow.com/questions/3804209/what-are-sessions-how-do-they-work
- [`Cookie` request header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cookie)
- [`Set-Cookie` response header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie)

A) Demo
  - https://github.com/tonethar/session-demo-2201
  - https://session-demo-2201.herokuapp.com/
  
B) Documentation
 - **express-session**
   - https://www.npmjs.com/package/express-session
   - `const session = require('express-session');`
   - `req.session` - To store or access session data, simply use the request property `req.session`, which is (generally) serialized as JSON by the store, so nested objects are typically fine.
 - **mongoose**
    - https://mongoosejs.com/docs/schematypes.html#objectids
     - `return DomoModel.find(search).select('name age').lean().exec(callback);`
 - **underscore**
   - https://www.npmjs.com/package/underscore

<a id="C"></a>

<hr>


## III. DomoMaker C - Add Redis & csrf

### III-A. Tips & Assignment Walkthrough

**step #3**
- explain array destructuring and what this code is doing:

```js
if (process.env.REDISCLOUD_URL) {
  // redisPASS = redisURL.auth.split(':')[1];
  redisURL = url.parse(process.env.REDISCLOUD_URL);
  [, redisPASS] = redisURL.auth.split(':');
}
```


**step #8**
- demo running on 2 ports - you will need to be using `npm start` for both instances

**step #9**
- On Heroku, look under the Resources tab (Add ons) to add Redis Enterprise Cloud
- Note that now there is a `REDISCLOUD_URL` under Config Vars - this was automagically populated for us by the Redis Add-on
- Then, test it on Heroku, it should work the same as it did locally!

**step #20**
- we already made this change back in step #4

**Step #24**
- In your form elements, make sure that there is a space after the two closing (React) curly braces:
  - like this - `<input type="hidden" name="_csrf" value={{csrfToken}} />`
  - NOT this - `<input type="hidden" name="_csrf" value={{csrfToken}}/>`

<hr>

<a id="D"></a>

## IV. DomoMaker D - Add React.js

- See myCourses for PDF and dropbox/due date
- What does React do for us in Part D?
  - In DomoMaker-C, whenever a new Domo was created by a user, the "domo list" was being rendered on the server-side by `res.render()` and Handlebars.js, which meant that every time you added a domo, a request was being made to the server, the entire HTML page was being re-created by the server, this new HTML page was sent back to the browser, and the browser needed to re-render this new page
  - In DomoMaker-D, whenever a new Domo is created by a user, the Domo is sent to the server, and if there is a successful update, the React components that are running on the client will request a new list of Domos from the server, and then just the "domo list" portion of the page will be modified by the client-side code, meaning that the entire HTML page is NOT re-rendered by the browser.
- What else is new?
  - `"buildLoginBundle"`, `"watchLoginBundle"`, `buildAppBundle`, `watchAppBundle` will watch for changes to JS files in the **client/** folder, and then transpile these files into ES5/JSX and publish them to **client/hosted/** as  **bundle.js** and **loginBundle.js**

### IV-A. Tips
 - You will need to make sure that the `watchLoginBundle` and `watchAppBundle` are running at all times. These are the scripts that will transpile the ES6 and React JSX that is located in your **client/** folder into the ES5 in your **hosted/** folder
 - PS - Handlebars.js isn't rendering the domos for you anymore in **app.handlebars** (React is now doing it on the client-side), so you don't need most of the code in the `makerPage` function (which located in **controllers/Domo.js**)
 - PS - clearing the form fields after the user makes a successful submission is always a good idea. With more modern React components we would just change the state varaible and then the component fields would update themselves. But here the "new domo" form fields are not being rendered by React so we have to do it in "old school jQuery" style:

```js
$("#domoName").val("");
$("#domoAge").val("");
```

- PS -  There is a lot of typing in this part and lot's of places to make syntax errors - esp. in the JSX. So triple-check your typing. The JSX typos often show up as errors in the browser console (which is where the React is rendering HTML) - so that is another place to look for hints if things are not working

<a id="E"></a>

<hr>

## V. DomoMaker E

- See myCourses for PDF and dropbox/due date
- Here's one possibility for a completed version you can look at as an example: https://domomaker-acjvks-2205.herokuapp.com/
- For this part, you will be:
    - A) adding a new attribute to one of the models AND
    - B) adding a new feature to the app (such as a delete button, or a new page to render

### Tips
- "A" above should be pretty straightforward, but "B" will be trickier
- To add event handling to a React component:
  - use the `onClick` attribute like this `onClick={handleClick}`, and then create the `handleClick()` function normally
  - if there are parameters to pass along, you could wrap `handleClick` above in an anonymous function like this `onClick={()=>handleClick(args)}`, OR
  - store the parameters as attributes on the component, and then access them on the event handler function with something like this `e.currentTarget.getAttribute('attributeName')`
- You will likely need to create a new endpoint (for example, **/all-users** or **/delete-domo**) - this means you will have to pass body data that includes the current value of `_csrf` everytime you call this new endpoint
- One issue with this is that Postman won't be very helpful for debugging because of the need for the `_csrf` value
- If you are using `jQuery.ajax()` to call the new endpoint from the client-side:
  - you can grab the `_csrf` value from the hidden form field using `const _csrf = document.querySelector("some-selector").value;`
  - and then pass the token along with any other data like this `const postData = "_csrf=Z6vP0rP...&anotherVariable=anotherValue&...";`



<a id="p2"></a>

<hr>

## Final Project
- [Final Project - Product/Service Site - React](../projects/project-2.md)
