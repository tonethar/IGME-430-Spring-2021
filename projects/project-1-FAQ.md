# Project 1 FAQ

## I. Debugging

- You might not be asking "how do I debug my code"? - but you should be! 
- You may have been able to skate through web dev until now without opening up the debugger, but it's unlikely that you will be able to continue to rely on `console.log()` for much longer
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
  - is your server sending the correct `Content-Type` header? It's a common "copy/paste" error to neglect to change the content type to the proper value in `response.writeHead()`. Recall that that HTML files, CSS files, JavaScript/JSON files, XML files, text files, images etc *all have distinct content-types*
  - Are any of the headers you are sending back giving incorrect of improperly formatted information?
    - for example, are you sending back an incorrect `Content-Length` header?

### I-C. Debug the server by testing your POST endpoints
- For POST requests, you can not test them in the browser's address bar, instead you will need to test them with:
  - the [Postman](https://www.postman.com/) App (this is the recommended way to start)
  - or with an HTML form
  - and/or with Ajax (e.g. `XHR`)

### I-C. Debug the server code directly 
- Go ahead and use `console.log()` to test your assumptions about what code is firing when, and 
- You can insert breakpoints in your server code (the Node.js code in your **src** folder) by launching the inspector:
  - `node --inspect ./src/index.js`
  - the head to **chrome://inspect**
  - this was covered in [Skill #10 - Debugging Node](../core-skills/10-debugging-node.md)
  - then you need to set a lot of breakpoints, step through the code, and test your assumptions
  - 
 
### I-XX. Debugging the "client"

<hr><hr>

## II. Questions on Project Requirements

- [Project 1 - API Powered App](project-1.md)

<hr><hr>

## III. Technical Questions

### III-A. Endpoint Issues

<hr>

