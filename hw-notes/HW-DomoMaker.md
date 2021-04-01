# DomoMaker HW Overview

- DomoMaker is a 4-part assignment where you will use React, Mongo/Mongoose, and Redis to create a web application that has the capability to create persistent data in our MongoDB cloud accounts, as well as login/logout capabilities for administrative "super users"
- The PDFs for all 4 parts are in myCourses

**Overview**

- [I. DomoMaker-A](#A)

- [II. DomoMaker-B](#B)

<a id="A"></a>

<hr>


## I. DomoMaker-A 

### I-A DomoMaker-A Tips and Hints
1) PDF of assignment is in myCourses
 
2) Start Code is here: https://github.com/IGM-RichMedia-at-RIT/DomoMaker-A-Start - because you will be posting this to Heroku, you might want to Fork the repository and then `git clone` it (rather than download the ZIP like the instructions say)

3) To get rid of those annoying warnings, and to make sure that Heroku uses the correct version of node and npm, set the "engines" keys of **package.json**

- `node -v` and `npm -v` will give you the versions (*semantic versioning* is `*major.minor.patch`) you are building with - and then replace the last digit with an `x` to specify that the latest patch should be used - for example:

```js
"engines": {
    "node": "15.4.x",
    "npm": "7.6.x"
  },
```

4) If you do NOT have a local instance of MongoDB running, just use your cloud account like we did on the Simple Models HW:

- comment out this line of code: 
  - `const dbURL = process.env.MONGODB_URI || 'mongodb://localhost/DomoMaker';`
- and replace it with this one - changing the placeholder values to instead reflect your actual Mongo Cloud login and password:
  - `const dbURL = 'mongodb+srv://MY_CLOUD_LOGIN:MY_CLOUD_PASSWORD@cluster0.bcwxq.mongodb.net/DomoMaker';`
- if the `dbURL` connection string is invalid in some way (bad username or password for example) - the app will throw an error in the Node console

### I-B. DomoMaker-A Assignment Walkthrough (we will talk about this in class)

- The architecture of this app is very similar to the *Simple Models* HW
  - **app.js**  loads the app dependencies and start up the [express](https://www.npmjs.com/package/express) server
  - **router.js** calls the various routes with code defined in the **controllers/** folder
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
- Create a user account (name and password) with **signup.handlebars**
  - `<input id="pass" type="password" name="pass" placeholder="password"/>`
  - note that the `type` is [`"password"`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/password)
  - **models/Account.js** is a mongoose model for the user's account
    - properties are `username`,`salt`,`password` (encrypted), `createdDate`
    - we encrypt the typed in password with node's built-in **crypto** library:
      - https://nodejs.org/api/crypto.html#crypto_crypto_pbkdf2_password_salt_iterations_keylen_digest_callback
      - https://nodejs.org/api/crypto.html#crypto_crypto_randombytes_size_callback
  - `controllers/Account.js` uses `signup()` to call `AccountModel.generateHash()` and generate an encrypted password
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
  - See ***tonys_class*** channel in Discord - there I noted 4 DomoMaker-B PDF typos
  - Make sure that you create a new repository (and Heroku app) for each version of DomoMaker. I will be grading/checking these off very quiickly, so you will be able to delete the old Heroku apps very quickly if need be
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

