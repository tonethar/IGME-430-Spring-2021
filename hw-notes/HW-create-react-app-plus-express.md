# HW Create React App + Express - Part I


## Overview 

- In this exercise, we are going to see how to:
  - create a React client Application with [`react-react-app`](https://reactjs.org/docs/create-a-new-react-app.html)
  - connect this app to an [express](https://www.npmjs.com/package/express) server
  - post the completed app to Heroku

<hr>

## I. Get Started

- For this exercise, we are going to use the Word Associations API:
  - here's the main page - https://wordassociations.net/
  - here's the developer page - https://wordassociations.net/en/api - signup for your free API key now

<hr>

## II. Start building your express app

- The express part of the application (e.g. the "back-end") will provide a *service* that the React client will call. Here we are going to have express act as a *proxy server* that calls the Word Associations API above

1) Create a folder named **word-associations** and `cd` into it

2) Type `npm init -y` (this creates a **package.json** file)

3) Type `npm i express unirest` (this downloads and add dependencies for express and [unirest](https://www.npmjs.com/package/unirest) - the latter is an easy to use HTTP library for downloading files)

4) 
