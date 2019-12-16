# APIs in React

## Learning Objectives

- SWBAT read developer documentation to construct an API call
- SWBAT read developer documentation to interpret an API response
- SWBAT integrate API data into a React component

## Sequence

1. [Launch](#launch)
2. [APIs Overview](#apis-overview)
3. [Viewing Data](#viewing-data)
4. [APIs + JavaScript](#apis--javascript)
   1. [Fetch](#fetch)
      1. [Chaining `.then()` Functions](#chaining-then-functions)
      2. [`fetch()`: `GET` and `POST`](#fetch-get-and-post)
      3. [`async` & `await`](#async--await)
   2. [Using `fetch()` in React](#using-fetch-in-react)
5. [Visualizing API Data](#visualizing-api-data)
6. [Close](#close)

## Launch

Click on this url: [http://jservice.io/api/random?count=1](http://jservice.io/api/random?count=1)

- What do you see when you click on that URL?
- Does the result look familiar? What's the name of the format you see?
- Look closer: can you find the trivia question?
- Look closer: can you find an answer to the trivia question?

> Using a browser plugin like [JSON Formatter (Chrome)](https://chrome.google.com/webstore/detail/json-formatter/bcjindcccaagfpapjjmafapmmgkkhgoa) will reformat that site to make it easier to read.

The [jservice.io](http://jservice.io/) site is a place where you can go to access over 156,800 trivia questions. We've reformatted one of the trivia questions below so you can more easily inspect the data you get from this API.

#### Request

```javascript
http://jservice.io/api/random?count=1
```

#### JSON Response

```javascript
[{
	"id": 117776,
	"answer": "the Globe",
	"question": "This London theatre was razed in 1644, 2 years after the Puritans closed it down",
	"value": 800,
	"airdate": "2013-04-05T12:00:00.000Z",
	"created_at": "2014-02-14T02:47:13.857Z",
	"updated_at": "2014-02-14T02:47:13.857Z",
	"category_id": 306,
	"game_id": null,
	"invalid_count": null,
	"category": {
		"id": 306,
		"title": "potpourriiii",
		"created_at": "2014-02-11T22:48:12.939Z",
		"updated_at": "2014-12-08T12:51:44.677Z",
		"clues_count": 320
	}
}]
```

> Note: the data above is an array containing a single object. This will become important later when we use data in React.

- What if you wanted 20 questions instead of just 1? How would you change the URL to get more results?

## APIs Overview

An API, or an Application Programming Interface, is a way of reading data from, or writing data to, a database that you don't necessarily own. Although some developers do set up and use their own APIs, here we'll focus on using other people's APIs to get their data.

APIs are great because we can hook into a service - that is maintained by someone else - to ensure that our app is always showing current data. For instance, let's say you want to build a weather app. Would you rather maintain a database of the weather in every location in the world? Or would you rather tap into a meterological database where they're already doing that?

Using an API involves two steps:

1. The Request: a request is where you're asking for someone else's data, and you typically need to specify what data you want according to the rules that the database owner sets up. Those rules are documented in developer documentation.
2. The Response: if the database accepts your request, then it sends back a response. The response is the data you've asked for, and the structure of the response data is typically also documented in developer documentation.

Have you ever noticed how the google URL changes when you google something? The URL is the request, and the data on the search results page is the response.

Can you guess what data this URL will show?: [https://www.google.com/search?q=red+lobster](https://www.google.com/search?q=red+lobster)

Now click on the URL. What happens if you change part of the URL from `red+lobster` to `blue+lobster`?

## Viewing Data

Most API requests are built from three parts:

1. An Endpoint: an endpoint is the stem of the request URL. For the example above, the endpoint is `https://www.google.com/search`.
	> For the first example we saw, the endpoint is `http://jservice.io/api/random`.
2. Parameters: parameters are the variables that are passed to the database as part of the request and follow the `?`. For the example above, there is one parameter, `q`.
	> For the first example we saw, the parameter was `count`.
3. Values: values are paired with variables and are the data that is passed to the database in the request. For the example above, the value `red+lobster` is paired with the parameter `q`.
	> For the first example we saw, the value was `1`.

> Note: when there are multiple parameters and variables passed to an API, the parameter/variable pairs are separated by an `&` symbol.

Not all API requests will return the data for a webpage like Google search results; some APIs like jservice.io just return raw data.
	
- For more on working with JSON data, see the [JSON & Firebase](json-firebase.md) mini-unit
- APIs can also be used to write data. To learn more about writing data to a database, see the [JSON & Firebase](json-firebase.md) mini-unit

## APIs + JavaScript

Now that you see how an API is a request for data, you'll probably want to use that data somewhere in an app. Although there are a number of ways of making API requests using JavaScript (e.g. using [vanilla JavaScript](https://plainjs.com/javascript/ajax/send-ajax-get-and-post-requests-47/) or [jQuery](https://www.w3schools.com/jquery/ajax_ajax.asp)), we're going to focus on how to integrate API requests with React.

Before jumping into React, however, we need to strategize a bit about how we want to use APIs to make for a seamless user experience.

When we make a request to an API, sometimes it takes a bit of time for the API to respond. So if we wait to fully load a webpage until the API responds, we might be making our user wait a long time before the page loads, if it even loads at all. In the worst case scenario, if we wait to load a page until an API responds and the API never responds, then the page will never load and the user will have a terrible experience; we can't rely on the success of a call to the API in order to load the page.

### Fetch

To overcome this problem, we need to use a way of calling the API where the call is done as soon as a page loads, and then the response (or lack thereof) can trigger a secondary event such as rendering the data. This pattern of requesting data in parallel to the normal loading order of the page is done using a "promise" function called `fetch()`.

`fetch()` requests data from an API via a URL (or even a local file) and then will do something depending on what it gets back from its request. If `fetch()` gets a response from the request (even if that response is no data at all), `fetch()` will pass that data on to a function called `.then()` which is chained to the `fetch()` request. If, however, the `fetch()` function gets an error response from its request (e.g. because of a bad request or a server error), it will execute whatever is in a `.catch()` function which is also chained to the `fetch()` request:

```javascript
fetch(apiURL) // requests data from apiURL
  .then(data => {
    // do something with the response that is returned to fetch which we're calling "data"
  })
  .catch(e => {
    // do something if the response is an error which we're calling "e"
  });
```

#### Chaining `.then()` functions

The pattern shown above is the simplest implementation of the `fetch()` which will get data from a URL, and it's primarily what we'll be using. It can, however, get more complex.

For instance, it's possible to chain together multiple `.then()` functions which will be executed in order following a successful `fetch()` request. This might come in handy if you first want to convert response data to JSON before using it:

```javascript
fetch(apiURL)
  .then(response => response.json()) // first convert the response to JSON
  .then(data => {
    // next do something with the JSON-ified data
  })
  .catch(e => {
    // do something if the response is an error
  });
```

#### `fetch()`: `GET` and `POST`

The `fetch()` function is, as a default, making a `GET` request of the API URL. But what if you wanted to use `fetch()` to send data via a `POST` request?

`fetch()` can accept an optional second parameter which is a set of options for how the `fetch()` request should be made. In this `init` parameter, you can set things like the type of request (`GET`, `POST`, `PUT`, etc.), headers, credentials, the body of a `POST` request, and more.

```javascript
// default options marked with *
fetch(apiURL, {
  method: 'POST', // *GET, POST, PUT, DELETE, etc.
  mode: 'cors', // no-cors, *cors, same-origin
  cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
  credentials: 'same-origin', // include, *same-origin, omit
  headers: {
    'Content-Type': 'application/json'
    // 'Content-Type': 'application/x-www-form-urlencoded',
  },
  redirect: 'follow', // manual, *follow, error
  referrer: 'no-referrer', // no-referrer, *client
  body: JSON.stringify(data) // body data type must match "Content-Type" header
})
```

> Read more about `fetch()` in the [Mozilla Web Developer Documentation](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch).

We'll use `fetch()` as the primary method for making API calls because that's what you'll see as you explore documentation on the web. That said, there's another pattern which is becoming more common which you may also see, so it's worth mentioning it here, too.

#### Async & Await

Another way to overcome this problem is to use a pattern called `async await` which you may see in documentation. `async` (for asynchronous) means that JavaScript will not have to wait for a function to succeed before continuing on to do other things. The `async` function will `await` a response from an API, and depending on the response - usually either `success` or an `error` - will do something. `async` and `await` are useful because they won't block the rest of the page from continuing to load even though data hasn't been received yet. This is particularly useful when you can't be certain how long an API will take to return data (if it returns data at all).

There's a lot to be said about using `async` and `await` properly, and there's a lot of complexity to handling and manipulating promises efficiently, but the basic anonymous version of the `async-await` functional pattern (with error handling) is below:

```javascript
(async () => {
  try {
    let response = await fetch(apiURL);
    // other await statements could go here

    // other code to execute once response is defined
  } catch(err) {
    // catches errors in any of the await statements in try {}
    alert(err);
  }
})();
```
- the `async` keyword is placed before the function to define it as an asynchronous function and to indicate that it will return a promise
- `try ... catch` is used to handle any errors that might result from an unsuccessful API request
- `await` makes JavaScript wait until the `fetch()` request has returned a result
> Note: `await` only works within an `async` function

So the anonymous function will wait for `https://someAPIcall` to return a result. If it does return a result, then it will store that as the `response` variable and then do something with it. If the request throws an error, then the function will do what's the in the `catch` code block, in this case showing an `alert()` with the error.

- More on [Using `async await` in React](https://www.valentinog.com/blog/await-react/), including troubleshooting

### Using `fetch()` in React

Now that we know what an API is and how it works, and how to make `fetch()` API requests, we can see how to make an API call in React.

API calls are typically done in the `componentDidMount` method of a component because the timing of the API request should be so the response of the request can be displayed in the component on the page:

```javascript
import React from 'react';
// any other import statements

const Item = () => {
  const component = new React.Component();
  component.state = {
    // define state variables here
  }

  component.componentDidMount = () => {
    fetch(apiURL)
      .then(data => {
        // do something with the response from apiURL
      })
      .catch(e => {
        // handle any errors from the request
      })
  }
  
  component.render = () => {
    return (
      // render component HTML here
    )
  }

  return component;
}
   
export default Item;
```

The standard way of handling the data returned from an API is to use `setState` within the `.then()` method in order to update any state variables which act as containers for the data that's returned. The component then renders based on updates to the state variables.

Below is an example where the `component.state.hits` variable is used to store the results of the API request; `component.state.hits` is also used to render the result.

```javascript
import React from 'react';
// any other import statements

const Item = () => {
  const component = new React.Component();
  component.state = {
    hits = []
  }

  component.componentDidMount = () => {
    fetch(apiURL)
      .then(result => component.setState({"hits": result.data}))
      .catch(e => {
        console.log(e);
        component.setState({"hits":[
          {
            'title':'An error has occurred.',
            'objectID': 0,
            'url': '#'
          }
        ]})
      })
  }
  
  component.render = () => {
    return (
      <ul>
        {component.state.hits.map(hit =>
          <li key={hit.objectID}>
            <a href={hit.url}>{hit.title}</a>
          </li>
        )}
      </ul>
    )
  }

  return component;
}
   
export default Item;
```

## Visualizing API Data

If you've completed the [Victory](victory.md) mini-unit, you can also consider how you might visualize or graph data returned from an API.

## Close

Successfully using APIs to get data is all about knowing the data you need, finding a source for that data, and being able to access it via a URL.

In order to implement APIs in React, we've also covered two more-technical strategies: leveraging the `componentDidMount` method in React and using `fetch()` to asynchronously request data while handling errors that may result.

At this point, we encourage you to move on to the [NYC Open Data mini-unit](react-nyc-open-data).
