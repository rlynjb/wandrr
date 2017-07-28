---
layout: post
title: "Explain how JSONP works (and how it's not really AJAX)"
date: 2016-01-26 10:47:13
tags:
- javascript interview questions
---

### Explain how JSONP works (and how it's not really AJAX).

JSONP (acronym for JavaScript Object Notation with Padding) is a common method to retrieve data from another domain and bypass CORS (Cross Origin Resource Sharing) rules.

**An overview of JSONP base on personal experience**<br>
I have used JSONP as a work around to get data by wrapping the response data in JSON format with a function callback set in query string as parameter and setting the callback as an object property of ajax object.

** _Note, I was using jQuery library when implementing AJAX with JSONP_

I've also heard of CORS as a set of rules regarding retrieving and transferring data or assets from 3rd parties or different domains from a client. This strictly applies to XMLHttpRequest for security reasons. Making HTTP Requests with XMLHTTPRequest object will only let us make request to our own domain and restricts us from different domain, thus, JSONP was created as a way to bypass this rule. 

[More about CORS: HTTP access control (CORS)](https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS)

-----

**How does JSONP work?**<br>

After reading further, implementation of JSONP differ from JavaScript libraries to the actual native JavaScript.
In native JavaScript, JSONP requests aren't dispatched with XMLHttpRequest object, rather, a `script` tag is added to the DOM, targeting its `src` attribute with the url. Reason is `script` tag does not have limitation to which domains it can retrieve its scripts from.
Also, since JavaScript has a global scope, we can reference a function to handle incoming JSON data from a 3rd party api url and link that to our application.
While, in JavaScript libraries such as jQuery, it automatically generate callback and clean up any inserted `script` tags unto the DOM.

In order for JSON data to be wrapped in a function, the 3rd party API service needs to support JSONP feature. Usually, they will specify on their documentation how to implement JSONP. [Here is an example: http://forismatic.com/en/api/](http://forismatic.com/en/api/)

If you copy & paste the url below, this will return a simple quote formatted in JSON

> http://api.forismatic.com/api/1.0/?method=getQuote&lang=en&format=json

While this url will return the same result except JSON data will be wrapped with a function since we explicitly specify format as jsonp and gave it a callback function

> http://api.forismatic.com/api/1.0/?method=getQuote&lang=en&format=jsonp&jsonp=processQuote

When this loads unto our application from `script` tag, the given callback name (function name) will get registered unto the global scope and will be available for us to use throughout our application.

-----

JSONP limits us with just retrieving `GET` data. It does not let us create, update, or delete `CRUD` data. That's why its just a work around but it does have its advantages. For example, retrieving simple data from a weather api, etc. If you want to take advantage of these other HTTP methods, then its best to build your own simple API Server.

-----

#### **References:**

- [JSONP How does it work](https://johnnywey.wordpress.com/2012/05/20/jsonp-how-does-it-work/)
