# HW Create React App + Express - Part I


## Overview 

- In this exercise, we are going to see how to:
  - create a React client Application with [`create-react-app`](https://reactjs.org/docs/create-a-new-react-app.html)
  - connect this app to an [express](https://www.npmjs.com/package/express) server
  - post the completed app to Heroku

<hr>

## I. Get Started

- For this exercise, we are going to use the Word Associations API:
  - here's the main page - https://wordassociations.net/
  - here's the developer page - https://wordassociations.net/en/api - signup for your free API key now
- Now test this endpoint with your API key:
  - `https://api.wordassociations.net/associations/v1.0/json/search?apikey=YOUR_API_KEY&text=welcome&lang=en`
  - this will return 50 words that are related to the word "welcome", and a number between 1 and 100 that indicates the amount of similarity
  -  you should get results something like below - note that the `response[0].items` array is what we are interested in

```json
 "version": "1.0",
  "code": 200,
  "request": {
    "text": [
      "welcome"
    ],
    "lang": "en",
    "type": "stimulus",
    "limit": 50,
    "pos": "noun,adjective,verb,adverb",
    "indent": "yes"
  },
  "response": [
    {
      "text": "welcome",
      "items": [
        {
          "item": "Warmly",
          "weight": 100,
          "pos": "adverb"
        },
        {
          "item": "Hearty",
          "weight": 98,
          "pos": "adjective"
        },
```

<hr>

## II. Start building your express app

- The express part of the application (e.g. the "back-end") will provide a *service* that the React client will call
- Here we are going to have express act as a *proxy server* that calls the Word Associations API above

1) Create a folder named **word-app** and `cd` into it

2) Type `npm init -y` (this creates a **package.json** file)

3) Type `npm i express unirest` (this downloads and add dependencies for express and [unirest](https://www.npmjs.com/package/unirest) - the latter is an easy to use HTTP library for downloading files)

4) In  **word-app**, create a file named **server.js**

5) Add the following code to it:

```js
const express = require('express');
const app = express();
const port = 3001;
const unirest = require("unirest");
const API_KEY = "YER-API-KEY-GOES-HERE";

app.get('/api/associations/:word', (req, res) => {
	const word = req.params.word;
	const request = unirest.get(`https://api.wordassociations.net/associations/v1.0/json/search?apikey=${API_KEY}&lang=en&text=${word}`)
	.then(response => {
			const results = response.body.response[0].items || []; // grab array of results
			console.log(`Num results=${results.length}`);
			res.json(results);
	})
	.catch(error => {
		console.log(`error=${error}`);
		res.json({status:"Error", message: `${error}`});
	});
});

app.listen(port, () => {
  console.log(`word-app listening on port ${port}`);
});
```

6) Add `"start" : "node ./server.js"` to the "scripts" key of your **package.json** file

7) Type `npm start` to start up this proxy server

8) To test the proxy server, head to http://localhost:3001/api/associations/software

- you should get results something like this:

```json
{
  "item": "Gnu",
  "weight": 100,
  "pos": "noun"
},
{
  "item": "Hardware",
  "weight": 96,
  "pos": "noun"
},
{
  "item": "Proprietary",
  "weight": 78,
  "pos": "adjective"
},
{ 
...
```


