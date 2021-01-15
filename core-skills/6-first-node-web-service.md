# Skill #6 - First Node Web Service

- Today we will learn how to build a simple [*web service*](https://www.tutorialspoint.com/webservices/what_are_web_services.htm) using Node.js, and how to pass parameters to it

## I. Overview

### I-A. Better code (slightly)

- the simple web server we created last time wasn't too special - it actually returned the SAME web page (*index*) for every request it received. This means that when the web browser also asked for a favicon, this web server also sent back the same *index* page, again! Good thing that the browser is smart enough to ignore that HTML and not instead try to create an image out of a web page!
- this time we'll actually look for the page that the client is looking for (using the `request.url`) property
- we will also look for *query parameters* - in this case one named `max` that will get passed in like this - `http://localhost:3000/getRandom?max=10`

### I-B. New (to us) built-in Node.js modules
- last time we will used the `http` module to help us build a simple web server
  - https://nodejs.org/api/http.html
- this time we will also use, so that we can get `pathname` and *query parameters* from the URL: 
  - https://nodejs.org/api/url.html
  - https://nodejs.org/dist/latest-v14.x/docs/api/querystring.html

<hr>

## II. The web service

- The complete code for your first node web server is below:
  - Create a folder named **first-web-service**
  - Using a terminal program (GitBash/Powershell/Terminal) make that folder the *cwd* by `cd`ing into it
  - `npm init -y` - let's use the default values this time
  - edit the **package.json** file:
    - under the `"scripts"` key add a `"start"` key with the value of `node ./src/index.js`
  - in the **first-web-service** folder, create a **src** folder
  - create **index.js** and put it in the **src** folder
  
<hr>

## XX. Homework
  
  
<hr><hr>

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
|   [Skill #5 - First Node Web Server](5-first-node-web-server.md) |  [**IGME-430**](../) | [Skill #7 - Create Random Joke Web Service](7-create-random-joke-web-service.md)
