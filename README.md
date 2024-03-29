CodeED in a Day
===============

This boilerplate helps attendees get started with their CodeED in a Day app.

## HTML

#### head-helper.html

Some simple code snippets to help mobile optimise a web app. Place within your HTML &lt;head&gt;

## JavaScript

#### form.js

JavaScript file that processes a form input, and submits the result to the Decoded Checkin API without refreshing the page (uses jQuery's AJAX helper function)

#### tracker.js

Starter file for writing code that tracks the user's position using the HTML5 geolocation API.

# API Documentation

## What it does

The Decoded Checkin API makes it possible to store a list of usernames and the number of times each one has been checked in.

## How to use it

The API is exposed via a URL: `http://api.decoded.co/checkin/`

Each data store consists of a list of usernames and checkins.  To create a new data store using the API, add a unique string of text to the URL:

`http://api.decoded.co/checkin/dd-mm-yy/app-name`

In the above example we are using the date and a separate app name to create a new data store. By default, this URL will return a list of all the names with the number of checkins in "JSON" format.

To create a new checkin, make an HTTP request to the same URL but append a "username" parameter:

`http://api.decoded.co/checking/dd-mm-yy/app-name?username=stephenfry`

If the "username" does not currently appear in the data store, then it is added with the number of checkins set to one (1).  Each subsequent HTTP request will increment the number of checkins for that user by one.  By default, this URL will return a JavaScript object of the form:

`{
  user: "StephenFry",
  checkins: 5
}`


## How it works

The API has been implemented using JavaScript/Node.js to run a server on the Raspberry PI.  Each data store file consists of a list of usernames and corresponding number of checkins, stored in "JSON" (JavaScript Object Notation) format eg

`{
  "StephenFry": 4,
  "RogerMoore": 16,
  "ada4ever": 7
}`

The contents of this file are updated in response to the HTTP requests described above.
