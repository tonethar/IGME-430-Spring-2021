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

1) You may want to skip setting up a local MongoDB for this HW, and instead exclusively use your Mongo Cloud account. To do so

- comment out this line of code  `const dbURL = process.env.MONGODB_URI || 'mongodb://localhost/simpleMVCExample';`
- and replace it with this one - replacing the placeholder values with your Mongo Cloud login and password:
  - `const dbURL = "mongodb+srv://MY_CLOUD_LOGIN:MY_CLOUD_PASSWORD@cluster0.bcwxq.mongodb.net/SimpleModels";`

2) From **MongoDB Compass**, you can see the cats you've added to ``, and even add some yourself. Here's what you need to type into the **MongoSH Beta** console at the bottom of the **MongoDB Compass** window

```js
use SimpleModels

db.cats.insertOne({
  name: 'Mr Meow',
  bedsOwned: 1,
  createdDate: Date()
})

db.cats.find().pretty()
```
