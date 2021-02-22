# Checkoff - Jokes Plus Ajax Client


## I.Overview

- We are going to add a simple `XHR` driven client page to your completed [HW - Random Jokes Plus - Phase 4](https://github.com/tonethar/IGME-430-Spring-2021/blob/main/hw-notes/HW-random-jokes-plus.md#phase4)
- You have worked with XHR and web services in both IGME-230/235 & IGME-330 - so this should be really easy for you

## II. Workflow

### II-A. Serving *joke-client.html*

- Save **joke-client.html** below into your the **client** folder of your **random-jokes-plus** (or whatever you called it) folder of your project
- In your **htmlResponses.js** file:
  - use `fs` to load the **joke-client.html** file in 
  - create a response handling function to "serve" the file'
  - "export" the response handling function
- In **index.js** - add an endpoint for **joke-client.html**
- Lastly, add a hypertext link to **client/error.html** that leads to **joke-client.html**
- Test your **joke-client.html** endpoint both in the location bar of the browser, and by clicking the hypertext link you just created

### II-B. Serving *joke-client.html*

