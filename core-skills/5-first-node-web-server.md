# Skill #5 - First Node Web Server

# I. Overview

- Last time we "imported" (using `require()`) an *external* libray (aka "package") named `nanoid`
- this time we will use a *built-in* library called `http` to help us build a simple web server
- the properties and methods that we will use today are: 
  - [`http.createServer(listener)`](https://nodejs.org/api/http.html#http_http_createserver_options_requestlistener) - will create a new http web server for us, and any client requests that come in will be routed to `listener`
  - [`httpServer.listen(port)`](https://nodejs.org/api/http.html#http_server_listen) - the server will begin to listen on the `port` we provide
  - [`ClientRequest.url` and `ClientRequest.headers`](https://nodejs.org/api/http.html#http_class_http_incomingmessage) - incoming requests will have a `clientRequest` and a `httpResponse` object - the `.url` and `.headers` properties give us information about that client request
  - [`httpResponse.writeHead()`](https://nodejs.org/api/http.html#http_response_writehead_statuscode_statusmessage_headers) - where we specify the *http response headers* we want to send back
  - [`httpResponse.write()`](https://nodejs.org/api/http.html#http_response_write_chunk_encoding_callback) - where we specify the *content* we want to send back
  - [`httpResponse.end()`](https://nodejs.org/api/http.html#http_response_end_data_encoding_callback) - close the connection
 
 
 
- require `http`
- `process.env`
- `npm i nodemon --save-dev`


<hr><hr>

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
|   [Skill #4 - Hello Node](4-hello-node.md) |  [**IGME-430**](../) | Skill #6 TBA
