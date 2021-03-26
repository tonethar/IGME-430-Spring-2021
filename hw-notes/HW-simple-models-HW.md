# HW - Simple Models

## I. Overview

- This HW covers a lot:
  - Express Routes
  - MVC
  - Server-side view rendering (handlerbars)
  - Mongo
  - Mongoose


<hr>

## II. Instructions

1) Start files are here - https://github.com/IGM-RichMedia-at-RIT/Simple-MVC-Example

2) Watch the video here, follow along by listening and typing in the code. The video is here: [YouTube - Rich Media 2 - Week 8.2 Simple MVC - Models (1:04:33)](https://www.youtube.com/watch?v=2DgCCVpRRbM)

3) Done files are here - https://github.com/IGM-RichMedia-at-RIT/simple-mvc-example-done

4) Now head to myCourses and grab the **SimpleModelsICE_MongoCloudUpdate.pdf** file - the HW instructions are there

5) Follow the submission instructions in the PDF


<hr>

## III. Walkthrough & Tips

1) You may want to skip setting up a local MongoDB for this HW, and instead exclusively use your Mongo Cloud account. To do so:

    - comment out this line of code:
      - `const dbURL = process.env.MONGODB_URI || 'mongodb://localhost/simpleMVCExample';`
    - and replace it with this one - replacing the placeholder values with your Mongo Cloud login and password:
      - `const dbURL = 'mongodb+srv://MY_CLOUD_LOGIN:MY_CLOUD_PASSWORD@cluster0.bcwxq.mongodb.net/simpleMVCExample';`

<hr>

2) If you are using the MongoDB Cloud with this assignment, in **MongoDB Compass** you can see the cats that you have added to `SimpleModels`. You can even add some more yourself using the **MongoDB Compass** app. Below is what you need to type into the **MongoSH Beta** console:

```
use simpleMVCExample

db.cats.insertOne({
  name: 'Mr Meow',
  bedsOwned: 1,
  createdDate: Date()
})

db.cats.find().pretty()
```

- Any changes ("CRUD") that you make to the cat data in either the Node App, or in **MongoDB Compass**, are reflected in ***BOTH apps***
- Try it:

```

```

- Then head back to `http://localhost:3000/page1` of the node app

<hr>

3) When you start working on this HW, change the name of the database from `simpleMVCExample` to `SimpleModels` (by editing the end of `dbURL`)

