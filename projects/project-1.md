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

2) Must have a "test" script that uses ESLint with the Airbnb spec. Must pass when I run `npm test`

3) Must use CircleCI for testing - the "test" script will be run by CircleCI, and a green checkmark will appear on the GitHub repo

4) Must have `nodemon` installed. We will test this by typing `npm run nodemon`

5) Must be deployed to Heroku. The 

<hr>

## IV. Functional Requirements
1) Should provide an engaging and rich user experience.



Must use a cloud service (such as Heroku) for deployment (unless special arrangements have been made).
Your application must be professionally designed and implemented.
Your application should have good, stable performance. There should not be any hiccups or performance issues when the server is under a light load. This means both your client and server need to run smoothly.
Static files (such as HTML, CSS, Client JS, Images, Videos, etc) should be delivered from the server.
Information calls (getting data, posting data, checking for updates, etc) should all be done through Ajax and a web API.
Direct calls to GET requests should work correctly. As in: going straight to the Ajax URL in the browser (including parameters).
Users should be able to add data to the API (with limitation). For example, maybe your app is a collection of images and keywords. You might then have a way for the user to add an image url and keywords to your API.
Your application should scale infinitely until it hits the limitations of the hardware it is on. This means, you cannot have any hard limits for how many different users have access until you run out of storage/memory. You may not give any site messages saying too many people are online or too many accounts have been created unless it is related to storage/memory/hardware performance.
App should go above and beyond in order to get an A.

<hr>

## V. Programming Requirements

<hr>

## VI. Rubric

<hr>

## VII. Deliverables







