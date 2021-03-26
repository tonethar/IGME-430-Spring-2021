# HW - Simple Models

## I. Overview

- This HW covers a lot:
  - Express Routes
  - MVC
  - Server-side view rendering (handlerbars)
  - Mongo
  - Mongoose
- But we have actually already looked at the first 4 of these, which just leaves the last one:
  - connecting a Node.js app to MongoDB
  - assigning a *schema* to MongoDB collection using Mongoose
  - doing the Mongo DB "CRUD" operations from Node.js


<hr>

## II. Instructions

1) Start files are here - https://github.com/IGM-RichMedia-at-RIT/Simple-MVC-Example

2) Watch the video here, follow along by listening and typing in the code. The video is here: [YouTube - Rich Media 2 - Week 8.2 Simple MVC - Models (1:04:33)](https://www.youtube.com/watch?v=2DgCCVpRRbM)

3) Done files are here - https://github.com/IGM-RichMedia-at-RIT/simple-mvc-example-done

4) Now head to myCourses and grab the **SimpleModelsICE_MongoCloudUpdate.pdf** file - the HW instructions are there

5) Follow the submission instructions in the PDF


<hr>

## III. Tips

1) You may want to skip setting up a local MongoDB for this HW, and instead exclusively use your MongoDB Cloud account. To do so:

    - comment out this line of code:
      - `const dbURL = process.env.MONGODB_URI || 'mongodb://localhost/simpleMVCExample';`
    - and replace it with this one - changing the placeholder values to instead reflect your actual Mongo Cloud login and password:
      - `const dbURL = 'mongodb+srv://MY_CLOUD_LOGIN:MY_CLOUD_PASSWORD@cluster0.bcwxq.mongodb.net/simpleMVCExample';`
    - if the `dbURL` connection string is invalid in some way (bad username or password for example) - the app will throw an error in the Node console
    - links:
      - https://mongoosejs.com/docs/connections.html
      - https://mongoosejs.com/docs/deprecations.html

<hr>

2) If you are using the MongoDB Cloud with this assignment, in **MongoDB Compass** you can see the cats that you have added to the `simpleMVCExample` database. You can even add some more yourself using the **MongoDB Compass** app. Below is what you need to type into the **MongoSH Beta** console:

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
  - Try running the mongo commands below in **MongoDB Compass** - and as you create/update/delete cats, be sure to head back to `http://localhost:3000/page1` of the node app to see that the changes you made are happening there too!:

```
use simpleMVCExample

db.cats.updateOne({ name: 'Mr Meow' },
{
  $inc: {
    bedsOwned: 10
  }
})

db.cats.find().pretty()
```

  - And:

```
use simpleMVCExample

db.cats.deleteOne({ name: 'Mr Meow' })

db.cats.find().pretty()
```

<hr>

3) When you start working on this HW, change the name of the database from `simpleMVCExample` to `SimpleModels` (by editing the end of `dbURL`)

<hr>

## IV. Walkthrough of *simple-mvc-example-done*

- We will hit the key points of the video linked above (but you will still need to watch the video!)

### IV-A. Get Mongo working
- **server/app.js**
- talk about MongoDB cloud code above
- demo a local install of `mongo`:
  - `mongo` (the client) and `mongod` (the server)
  - a PDF in myCourses covers how to install a local version of MongoDB


### IV-B. Mongoose - creating a data *schema*
- Mongoose - *"elegant mongodb object modeling for node.js"* - https://mongoosejs.com/
- A *schema* is a "blueprint" of how a MongoDB collection will be structured
- https://mongoosejs.com/docs/guide.html
  - *"Everything in Mongoose starts with a Schema. Each schema maps to a MongoDB collection and defines the shape of the documents within that collection."*
- **server/models/Cat.js**

```js
const CatSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
    trim: true,
    unique: true,
  },

  bedsOwned: {
    type: Number,
    min: 0,
    required: true,
  },

  createdDate: {
    type: Date,
    default: Date.now,
  },

});
```

- A mongoose *schema* enforces a data *type* for the properties of the `Cats` collection
  - The permitted *SchemaTypes* are `String`, `Number`, `Date`, `Buffer`, `Boolean`, `Mixed`, `ObjectId`, `Array`, `Decimal128`, `Map`
  - There are other *options* we can specify such as minimum/maximum values, if there is a default value, and if a value is required, or if a value must be *unique*:
    - https://mongoosejs.com/docs/guide.html#options
    - be careful with the `unique` option - it's not something that you will need very often (so don't copy/paste it and keep reusing it!)



### IV-C. Mongoose schemas can have *static functions*

- Below is a function that we'll define - it looks for a specific cat - that we'll later call from `readCat()` like this: `Cat.findByName(name1, callback);`

```
CatSchema.statics.findByName = (name, callback) => {
  const search = {
    name,
  };

  return CatModel.findOne(search, callback); // calls Mongo's built-in `findOne()` method
};
```

### IV-D. Create `CatModel`

- Create `CatModel` and utilize `CatSchema`, and name the MongoDB collection `Cat`

```
let CatModel = mongoose.model('Cat', CatSchema);
```


### IV-E. Make a new `Cat`

- We can then make a new `Cat` like this:

**controllers/index.js** (Some of if)

```
const Cat = models.Cat.CatModel; // renaming `CatModel` to `Cat`

...

const setName = (req, res) => {
  // check if the required fields exist
  // normally you would also perform validation
  // to know if the data they sent you was real
  if (!req.body.firstname || !req.body.lastname || !req.body.beds) {
    // if not respond with a 400 error
    // (either through json or a web page depending on the client dev)
    return res.status(400).json({ error: 'firstname,lastname and beds are all required' });
  }

  // if required fields are good, then set name
  const name = `${req.body.firstname} ${req.body.lastname}`;

  // dummy JSON to insert into database
  const catData = {
    name,
    bedsOwned: req.body.beds,
  };

  // create a new object of CatModel with the object to save
  const newCat = new Cat(catData);

  // create new save promise for the database
  const savePromise = newCat.save();

  savePromise.then(() => {
    // set the lastAdded cat to our newest cat object.
    // This way we can update it dynamically
    lastAdded = newCat;
    // return success
    res.json({ name: lastAdded.name, beds: lastAdded.bedsOwned });
  });

  // if error, return it
  savePromise.catch((err) => res.status(500).json({ err }));

  return res;
};
```

