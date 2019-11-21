# Getting Data into Your App

## Learning Objectives

- SWBAT 

## Sequence

1. [Launch](#launch)
2. [Adding Static Data to Your App](#adding-static-data-to-your-app)
3. [APIs Overview](#apis-overview)
4. [Viewing Data](#viewing-data)
5. [APIs + JavaScript](#apis--javascript)
6. [NYC Open Data APIs](#nyc-open-data-apis)
7. [Close](#close)

## Launch

* click on this URL ... (Jservice)

## Adding Static Data to Your App

Some text here

## APIs Overview

An API, or an Application Programming Interface, is a way of writing data to, or reading from, a database that you don't necessarily own. Although some developers do set up and use their own APIs, here we'll focus on using other people's APIs to get their data.

Using an API involves two steps:

1. The Request: a request is where you're asking for someone else's data, and you typically need to specify what data you want according to the rules that the database owner sets up. Those rules are documented in developer documentation.
2. The Response: if the database accepts your request, then it sends back a response. The response is the data you've asked for, and the structure of the response data is typically also documented in developer documentation.

Have you ever noticed how the google URL changes when you google something? The URL is the request, and the data on the search results page is the response.

Can you guess what data this URL will show?: [https://www.google.com/search?q=red+lobster](https://www.google.com/search?q=red+lobster)

Now click on the URL. What happens if you change part of the URL from `red+lobster` to `blue+lobster`?

## Viewing Data

Most API requests are built from three parts:

1. An Endpoint: an endpoint is the stem of the request URL. For the example above, the endpoint is `https://www.google.com/search`.
2. Parameters: parameters are the variables that are passed to the database as part of the request and follow the `?`. For the example above, there is one parameter, `q`.
3. Values: values are paired with variables and are the data that is passed to the database in the request. For the example above, the value `red+lobster` is paired with the parameter `q`.

Not all API requests will return the data for a webpage like Google search results; some APIs just return raw data.

- A few examples to get raw data and to manipulate the request
	- We love Jservice because it's an open API that allows us to spend a fair bit of time JUST messing with the endpoint. I think that fits the bill here as a simple example before ramping up to NYCOpenData
	- fixer.io
- For working with JSON data - see [JSON & Firebase](json-firebase.md) mini-unit
- APIs can also write data - see [JSON & Firebase](json-firebase.md) mini-unit

## APIs + JavaScript

- AJAX (vanilla JS & jQuery) (name only)
- promises (name only)
- async, await (focus here)
- For visualizing API data - check out the [Victory](victory.md) mini-unit

## NYC Open Data APIs

- Documentation
- Peculiarities, difficulties, troubleshooting

> This is both the hardest part of the task I've set before you, Jeffrey, and also the most important.
> 
> If the WHOLE lesson can be focused mostly around this, with an aside to "btw, giphy's api is much easier", that feels right to me.
> 
> If that's not possible, let me know and we can brainstorm scaffolding.

## Close

Some text here

#### Questions for students

- Some text here
