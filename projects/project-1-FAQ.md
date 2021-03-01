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

### I-B. Debug the server by testing your endpoints
- We have done this many, many times in class, and it's pretty straightforward to do. You just have to do it
- For your `GET` endpoints, you can use the Chrome Web Inspector. More than likely you will need the **Network** tab. Things to look for:
  - is the content what you expected?
  - if the content is in the JSON format, is it *valid*? The [JSON Viewer](https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh?hl=en-US) extension will help determine that. There are also various online JSON validators that you can use
  - is your server sending the correct `Content-Type` header? It's a common "vopy/paste" error to neglect to change the content type. Recall that 
 
### I-XX. Debugging the "client"

