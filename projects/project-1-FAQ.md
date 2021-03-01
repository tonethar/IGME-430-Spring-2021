# Project 1 FAQ

## Navigation

- [I. Debugging](#debugging)

- [II. Questions on Project Requirements](#project-requirements)

- [III. Technical Questions](#technical-questions)

<a id="debugging" />

<hr><hr>

## I. Debugging

- You might not be asking "how do I debug my code"? - but you should be! 
- You may have been able to skate through web dev until now without opening up the debugger, but it's unlikely that you will be able to continue to rely *solely* on `console.log()` for much longer
- When things aren't working as expected:
  - first, run `npm test`, that often flags unused variables, which often mean that you misspelled something
  - next, decide if you want to debug from the "top down" (look at the client code and verify what it's doing, then the server), or from the bottom up (server code first, then client)
  - Below, we will discuss debugging strategies from the "bottom up"


### I-A. App is crashing Heroku, but works fine locally

- This should not happen very often on Project 1, but if it does, check your error logs on Heroku to get an idea of what went wrong:
  - https://devcenter.heroku.com/articles/logging#log-retrieval-via-the-web-dashboard

### I-B. Debug the server by testing your GET endpoints
- We have done this many, many times in class, and it's pretty straightforward to do. You just have to do it!
- For your `GET` endpoints, you can use browser's address bar, and the Chrome Web Inspector
- Parameters are usually passed in like this **`http://localhost:3000/get-jokes?limit=5&minrating=3`** 
- More than likely you will need the **Network** tab of the Web Inspector, which allows you to see the status code, content-type, and the actual returned text. Things to look for:
  - is the content what you expected?
  - if the content is in the JSON format, is it *valid*? The [JSON Viewer](https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh?hl=en-US) extension will help determine that. There are also various online JSON validators that you can use
  - is your server sending the correct *HTTP status code*? It's a common "copy/paste" error to neglect to change the status code to the proper value in `response.writeHead()` (for example, sending `404` as a status code for your index page)
  - is your server sending the correct `Content-Type` header? It's a common "copy/paste" error to neglect to change the content type to the proper value in `response.writeHead()`. Recall that that HTML files, CSS files, JavaScript/JSON files, XML files, text files, images etc *all have distinct content-types* --> https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types
  - Are any of the headers you are sending back giving incorrect of improperly formatted information?
    - for example, are you sending back an incorrect `Content-Length` header?

### I-C. Debug the server by testing your POST endpoints
- For POST requests, you can not test them in the browser's address bar, instead you will need to test them with:
  - the [Postman](https://www.postman.com/) App (this is the recommended way to start)
  - or with an HTML form
  - and/or with Ajax (e.g. `XHR`)

### I-C. Debug the server code directly 
- Go ahead and use `console.log()` to test your assumptions about what code is firing when, and what the values of variables are. These logs will appear on the *server-side* - meaning in the console that you launch your Node.js server from
- You can insert breakpoints in your server code (the Node.js code in your **src** folder) by launching the Node.js inspector:
  - `node --inspect ./src/index.js`
  - the head to **chrome://inspect**
  - this was covered in [Skill #10 - Debugging Node](../core-skills/10-debugging-node.md)
  - then you need to set a lot of breakpoints, step through the code, and test your assumptions on what code is firing when, and what the values of variables are as the code executes
 
### I-D. Debugging the "client"
- The *client* code means the JavaScript that runs on the *client-side* - e.g. the web browser
- This is the code that is in the `<script>` tag of any of your HTML pages - meaning those pages that are located in the **client** folder of your project:
  - you might have also moved that code to an etxternal JavaScript file - for example  **client/js** - but it's still running on the **client-side**
- Go ahead and use `console.log()` to test your assumptions about what code is firing when, and what the values of variables are. These logs will appear on the *client-side* - meaning in the web inspector console of the web browser
- You can insert breakpoints in your client code (the JavaScript in your `<script>` tag) by using the Chrome web inspector:
  - this has been ddemo, so many times, in 330

### I-E. Head to Discord
- After you have made attempts to debug your code, and had limited success, it's time to head to Discord and see if your fellow students can help:
  - the time you spent debugging has hopely narrowed down the scope of the issue!
  - so that other people can help you, you'll need to:
    -  describe how the problem happens
    -  give an example of the output you received - screenshots are really helpful
    -  tell us what the expected output is
    -  describe what you've done to attempt to fix the problem on your own
  - be aware:
    - it's OK to share code snippets
    - but DO NOT otherwise share too much your code with your classmates
  - If you are still stuck:
    - push your latest code to GitHub
    - send the professor an email with the GitHub and Heroku links
    - be sure to document & describe the issue 
 - PS:
   - Yes, it's still OK to shortcut this debug process occasionally - for example:
     - *Is anyone else getting the `"no-restricted-syntax"` error when you run ESLint?*
  

<a id="project-requirements" />

<hr><hr>

## II. Questions/Clarifications on Project Requirements

- [Project 1 - API Powered App](project-1.md)

<a id="technical-questions" />

<hr><hr>

## III. Technical Questions

### III-A. Endpoint Issues

1) Imagine that you have an HTML page in your **client** folder that is trying to load a style sheet like this -  `<link href="default-styles.css" type="text/css" rel="stylesheet" />`:
    - make sure the endpoint is named properly in your **src/index.js** file - ex. **default-styles.css**  - NOT something like **/css**
    - test the endpoint in the browser as recommended in **I-B.** above
      - make sure that you are serving the correct `Content-Type` and *HTTP status code* in your **src/responses.js** file - ex. `text/css` and `200`

### III-B. ESLint Issues

1) *I can't push my code to GitHub because of ESLint errors - this AirBnB spec is really picky - what should I do?!*
    - First, you should either fix or comment out the offending code
    - If the code seems to run locally OK, then you can edit your **.eslintrc.json** file and convert the *error* to a *warning*. Then you should be able to push your code to GitHub - example:


```js
"rules": {
        "no-unused-vars": "warn",
        "no-restricted-syntax": "warn"
    }
```

***HOWEVER - you need to take the error seriously, and be sure to revisit it later on when you have time to work out what's going on***

### III-C. TBA


<hr>

