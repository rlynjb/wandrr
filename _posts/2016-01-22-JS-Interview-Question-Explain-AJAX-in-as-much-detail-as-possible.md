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
AJAX, as in its acronym states, is Asynchronous in nature. This means, it can receive data through user interaction or automation event without the need to refresh the page, thus, updating and reloading certain portion of the page.

There are many ways we can implement AJAX, via jQuery or native JavaScript. Since this is for learning purposes, I am going to use native JavaScript, outline the method, and explain how each objects work.

-----

**A bit of History** <br>
To make an HTTP Request to the server, we need to instantiate a class called XMLHttpRequest. Microsoft developed this object called XMLHttp, and then Mozilla developed their own version and called it XMLHttpRequest. Other browsers, Safari, including Microsoft, followed and implemented XMLHttpRequest object as well. If you want to know its history. 
[Ref: Wikipedia - XMLHttpRequest](https://en.wikipedia.org/wiki/XMLHttpRequest)

{% highlight html %}
<!--
  This is just a simple AJAX example.
  credits to developer.mozilla.org for sample code.
  comments are explained by me. :-p
-->

<span id="ajaxButton" style="cursor: pointer; text-decoration: underline">
  Make a request
</span>

<script type="text/javascript">
  /*
    here, we are using an IIFE to wrap our code so our
    variables and closures doesn't pollute the global namespace
  */
  (function() {
    var httpRequest;

    /*
      this is an event handler,
      once user clicked on ajaxButton html element,
      it will execute the onclick function and call the
      makeRequest function with a given 'test.html' value on its parameter.
      the 'test.html' url is just a sample api url which we'll be
      making a request from a server and expect a server response.
    */
    document.getElementById("ajaxButton").onclick = function() {
      makeRequest('test.html');
    };

    function makeRequest(url) {
      /*
        as mentioned above, we need to instantiate a new class 
        of XMLHttpRequest so we can make a HTTP request to the server.
        we are assigning this class to a variable defined on our
        outer scope so its accessible throughout our IIFE scope.
      */
      httpRequest = new XMLHttpRequest();

      /*
        were doing a Feature Detection here.
        as the name implies, we are just checking if
        XMLHttpRequest host object is NOT available and
        setting an alert action to notify user if
        XMLHttpRequest is not available on their browser/environment.
      */
      if (!httpRequest) {
        alert('Giving up :( Cannot create an XMLHTTP instance');
        return false;
      }

      /*
        before sending our HTTP server request,
        we need to set a handler for our server response.
        We can do this by assigning a function to our
        XMLHttpRequest object property 'onreadystatechange'.
        Or
        We can also assign an anonymous function, so 'onreadystatechange'
        doesn't need to carry a reference to a function.
        But for organization, we will just use the former method.
      */
      httpRequest.onreadystatechange = alertContents;

      /*
        Now that we have set our request server response handler, 
      */
      httpRequest.open('GET', url);
      httpRequest.send();
    }

    function alertContents() {
      if (httpRequest.readyState === XMLHttpRequest.DONE) {
        if (httpRequest.status === 200) {
          alert(httpRequest.responseText);
        } else {
          alert('There was a problem with the request.');
        }
      }
    }
  })();
</script>
{% endhighlight %}

-----

##### **Reference:**
- [What's AJAX? - Getting Started](https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started)
