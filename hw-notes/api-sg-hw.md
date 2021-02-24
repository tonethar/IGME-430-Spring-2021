# HTTP API Study Guide Notes

- This study guide exposes you to API terminology and some best practices for designing APIs
- See myCourses for DOC file and due date


## I. HTTP Methods

- https://www.tutorialspoint.com/http/http_methods.htm 
- Briefly describe the following types of HTTP Requests:
  - `GET`
  - `HEAD`
  - `POST`
  - `PUT`
  - `DELETE`

<hr>

## II. Differences between `GET` and `POST`:

- http://www.w3schools.com/TAGS/ref_httpmethods.asp 

<hr>

## III. API Design Best Practices

- https://geemus.gitbooks.io/http-api-design/content/en/responses/ 

### III-A. Requests
- Accept serialized JSON in request bodies
- Use the plural version of a resource name unless the resource in question is a singleton within the system
- Use downcased and dash-separated path names - ex. `jokes-api.com/users` or  `jokes-api.com/all-jokes`
- Require Versioning in the `Accepts` Header


### III-B. Responses

#### III-B-i. Return appropriate Status Codes

- [`200`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200)
- [`201`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/201)
- `202`
- [`204`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/204)
- `206`
- [`400`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400)
- `401`
- `403`
- `404`
- `422`
- `429`
- `500`

#### III-B-ii. Time Stamps


#### III-B-iii. Serialize Foreign Key References


#### III-B-iv. Generate Structured Errors


#### III-B-v. Keep JSON Minified
