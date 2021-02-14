# Project 1 - API Powered App - DRAFT

##  I. Overview

- Individually, you need to make a rich web app that uses a web API of your design. You may use an external API **in addition to your own**. The app should be engaging and aesthetically pleasing. Ideally it will be (or approach) portfolio quality. The project should be scoped for just a couple weeks.

- **Application:** The actual project is fairly open-ended. The goal is to make a rich web app that uses backend (server) data from an API. The app should be aesthetically pleasing and provide a rich user experience. The static files (like HTML, CSS, Client JS, images, etc) may be sent normally, but the rest of the changes/updates for the app should be done through a custom AJAX API.

<hr>

## II. Ideas

Here are some loose ideas that would warrant a server side API. Be creative! Make a good portfolio piece!

- https://www.pokedex.org/ (loads page with overall list, but then calls to an individual one when clicked. Your API should work directly from the URL returning JSON.)
- https://naramsim.github.io/Colosseum/ (similar to above, with individual calls to certain objects. Note: this app uses a hash reference in the URL instead of query parameters, which does not quite fit the requirements. The overall app itself is similar to the idea of the assignment though.)
- https://sii.im/playground/notes/ (Note system where users can create a note and then use a query parameter through some UI ability or unique url to recall that particular note. Then the user could edit their note again.)
- https://trello.com/ (similar to above, a shared task board people could add tasks to or update.)
- https://asana.com (Similar to Trello. A task board people can add tasks to or update.)
- https://www.meetup.com (App for creating meetups based on a topic, area and time.)
- https://www.pinterest.com/ (board or boards people could add images, text, keywords to and add more later. To avoid uploading images, the user could submit a URL instead).
- https://deanhume.github.io/beer/ (App indexing some topic, such as board games, heartstone cards, music, etc and letting the user click on individuals for more info, go through categories or even search).
- https://hellosunapp.com (App that shows positions of the sun and moon in different times zones throughout the world.)
- https://getkana.com/app/ (Another tutorial type app that users could add to).
- http://flateric.columba.uberspace.de/canvas/ (Visualization of user collected messages, links, etc).
- http://idiots.win/ (quiz type app users could add questions to or create their own unique quiz).
- https://www.google.com/forms/about (A survey & survey creation system.)
- https://www.instapaper.com (A link and article manager. For users to store links for later.)
- https://www.getpennies.com (A personal financial tracker. Users can add their own data. DO NOT COLLECT REAL USER FINANICAL DATA IN THIS COURSE.)

<hr>

## III. Development Requirements

1) Must use Git for version control in a repo I can access. You may make the repo *private* if you wish, just be sure to send me an invite to collaborate ASAP

2) Must have a "test" script that uses ESLint with the Airbnb spec. Must pass tests when I run `npm test`

3) Must use CircleCI for testing - the "test" script will be run by CircleCI, and a green checkmark will appear on the GitHub repo

4) Must have `nodemon` installed. I will test this by typing `npm run nodemon`

5) Code must be well-commented. Every function/method should have a comment describing its purpose

6) Must be deployed to Heroku. The "Wait for CI to pass before deploy" checkbox must be checked.


<hr>

## IV. Functional Requirements
1) Must provide an engaging and rich user experience

2) Users must be able to add data to the API (with limitation). For example, maybe your app is a collection of images and keywords. You might then have a way for the user to add an image url and keywords to your API.




Your application should have good, stable performance. There should not be any hiccups or performance issues when the server is under a light load. This means both your client and server need to run smoothly.
Static files (such as HTML, CSS, Client JS, Images, Videos, etc) should be delivered from the server.
Information calls (getting data, posting data, checking for updates, etc) should all be done through Ajax and a web API.
Direct calls to GET requests should work correctly. As in: going straight to the Ajax URL in the browser (including parameters).

Your application should scale infinitely until it hits the limitations of the hardware it is on. This means, you cannot have any hard limits for how many different users have access until you run out of storage/memory. You may not give any site messages saying too many people are online or too many accounts have been created unless it is related to storage/memory/hardware performance.


<hr>

## V. Programming Requirements

1) Server API must support the following status codes: 200, 201, 204, 400, 404, 500 (only necessary if applicable)

2) Server API must support the following methods:

    - HEAD (should be supported on the calls that get data back)
    - GET
    - POST
    
3) At least one GET request type will support query parameters (both in AJAX and directly). These could be used to filter results, sort results or something else.
Client should use accept header (only needs to support JSON, but other formats would count as extra).
Client should submit a body in a POST request to add or update data.
It is okay to keep your API data in memory for this project. That does mean user added data will go away after each server reload. (roughly 30 minutes on Heroku).
Any borrowed code or fragments must be credited in both your code comments, and in the final documentation of the project.
Separation of Concern - There should be a clear separation of purpose and classes. Do not put everything in the same file/module.
D.R.Y. - Don't Repeat Yourself. Repeated blocks of nearly identical code should be factored out and placed in a separate function.


<hr>

## VI. Rubric

- App should go above and beyond in order to get an A.

<hr>

## VII. Deliverables

### VII-A. Prototype

- Should at least be the core experience with some of the API working. The full API might not be ready and the app may not be finished, but the main part of the experience should be testable
- Submission:
  - Working version must be accessible online through Heroku
  - Final code must be pushed to Git repo
  - Final code must be zipped and submitted to the dropbox (without **node_modules**)
  - The following links in the submission comments

### VII-A. Final Version

- Final code must be pushed to Git repo
- Final code must be zipped and submitted to the dropbox (without node_modules)

Link to the Git repo (add me if necessary).
Link to CircleCI Build.
Link to cloud deployed app (Heroku).
Final:

Documentation:
README.md

Hand in documentation explaining the following:

What your site does and its purpose.
What part of your app does the API handle?
What went right and what went wrong?
If you were to continue, what would you do to improve your app?
How did you go above and beyond?
Code:

Must be accessible online through Heroku (unless special arrangements have been made).
Final code should be submitted to Git repo.
Final code should be zipped and submitted to the dropbox (without node_modules).
The following links in the submission comments
Link to the Git repo (add me if necessary).
Link to CircleCI Build.
Link to cloud deployed app (Heroku).








