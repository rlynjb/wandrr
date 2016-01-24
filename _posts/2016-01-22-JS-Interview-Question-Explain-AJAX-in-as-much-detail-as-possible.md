---
layout: post
title: "Explain AJAX in as much detail as possible"
date: 2016-01-22 10:47:13
tags:
- javascript
- interview question
---

### Explain AJAX in as much detail as possible

**Overview** <br>
AJAX is a way to communicate to the server without reloading the page. Once we receive the data from the server, we can then manipulate those data and display unto certain parts of the page, this is why we don’t need to reload the page.

**Technically..** <br>
AJAX is acronym for Asynchronous JavaScript and XML. It uses a host object called XMLHttpRequest to communicate to a server-side script to retrieve data formatted in either JSON, XML, HTML, or plain text.
AJAX, as in its acronym states, is Asynchronous in nature. This means, it can receive data through user or automation event interaction without the need to refresh the page, thus, updating and reloading certain portion of the page.

There are many ways we can use AJAX, via jQuery or native JavaScript. Since this is for learning purposes, I am going to use native JavaScript, outline the method, and explain how each objects work.

-----

To make an HTTP Request to the server, we need to instantiate a class called XMLHttpRequest. Surprisingly, Microsoft popularized this object. If you want to know its history. Ref: https://en.wikipedia.org/wiki/XMLHttpRequest

-----

##### **Reference:**
- [What's AJAX? - Getting Started](https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started)
