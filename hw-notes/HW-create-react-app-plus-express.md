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

5) Add the follwoing code to it:

```js

```
