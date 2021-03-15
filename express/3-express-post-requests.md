# 3 - Express - Serving Static Files

## I. Overview

## VI. Enable `POST` requests

### VI-A. Create a HTML `<form>` page

- put the following in the **client/html/** folder

**add-user-form.html**
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Add a user</title>
  </head>
  <body>
    <header>
      <h1>Add a user!</h1>
    </header>
    <main>
      <form action="/add-user" method="POST">
        First name:
        <input type="text" name="firstname" value="">
        Last name:
        <input type="text" name="lastname" value="">
        <input type="submit" value="Submit">
      </form>
    </main>
    <footer>
      <p>&copy; 2021 Ace Coder</p>
    </footer>
  </body>
</html>
```

- now head to `http://localhost:3000/assets/html/add-user-form.html` - the form should be visible because of `express.static()` serving it for us:
  - although that's a clunky endpoint!
- so let's serve it on **'/add-user-form.html'** instead:
  - head to **server.js** and add a `GET` endpoint - `app.get('/add-user-form.html', ...),`
  - then test it at `http://localhost:3000/add-user-form.html` to be sure you did it right

<hr>

### VI-B. Create the `/add-user` `POST` endpoint

- When you look at the `<form>` tag above, you will see that the form's HTTP `method` is `POST`, and the `action` (the endpoint it calls when the submit button is clicked) is `/add-user`
- There is some built in *middleware* to handle POST requests and data sent in the HTTP message body - add the following to **server.js**:

```js
import bodyParser from 'body-parser';
```

and

```js
app.use(bodyParser.urlencoded({extended: true}));
```

- Let's write some code for that endpoint:

<hr>

## XX. Submission

- Delete your **node_modules** folder, then ZIP and POST to the dropbox
- There is no need to post this to GitHub or Heroku


<hr><hr>

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
|   [Express #1 - Intro to express](1-express-intro.md) |  [**IGME-430**](../) | **Express #3**
