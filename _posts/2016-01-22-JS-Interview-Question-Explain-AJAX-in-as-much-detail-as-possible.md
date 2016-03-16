---
layout: post
title: "Explain AJAX in as much detail as possible"
date: 2016-01-22 10:47:13
tags:
- javascript interview questions
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

    /*
      MAKING AN HTTP REQUEST
    */
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
        we'll need to make the request.
        - 1st parameter, is the HTTP request method (GET, POST, DELETE, etc).
          There are other request methods, whichever our server supports.
          It's also good practice to define these request methods
          in capital letters as per the HTTP standard or there are browsers
          (Firefox) that may not be able to process the request.
        - 2nd parameter, is the url for the data we are requesting.
          Make sure to use the exact domain name or it will throw a 'Permission Denied' error.
          For security purpose, we cannot make a 3rd party request, if needed,
          this is a CORS issue,
          ref: https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS
        - 3rd parameter, just sets whether the request is asynchronous. This is
          optional and default is set to true.
      */
      httpRequest.open('GET', url);

      /*
        As the method name implies, this HTTP request object method opens/sends the request.
        If we are simply doing a 'GET' request, we can leave the parameter empty, but
        if we are 'POST'ing data, we can pass in a value formatted in either
        query string, JSON, SOAP, etc.
      */
      httpRequest.send();

      /*
        NOTE:
        If we want to POST data, we may need to set the MIME type of the request.
        Ex: httpRequest.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
      */
    }

    /*
      HANDLING THE SERVER RESPONSE
    */
    /*
      this is the same function declaration we've assigned to 
      'onreadystatechange' object property above.
    */
    function alertContents() {
      /*
        this if statement checks for the state of the request.
        if the 'readyState' has a value of XMLHttpRequest.DONE (evaluating to 4),
        it means the server response has been received and its OK for us to continue processing.
        ref: https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest#Properties
      */
      if (httpRequest.readyState === XMLHttpRequest.DONE) {
        /*
          Next, we'll check for HTTP Status Code. Most common HTTP Status Codes I've
          encountered are 200 OK, 403 Forbidden Error, and 500 Server Error.
          There is a list of HTTP Status Code available online with description of code.
          This if statement is just checking for which HTTP Status Code to respond to and
          execute code for whatever we want to do with the data.
        */
        if (httpRequest.status === 200) {
          alert(httpRequest.responseText);
        } else {
          alert('There was a problem with the request.');
        }

        /*
          There are 2 options to access data: httpRequest.responseText and httpRequest.responseXML
          Step above is only valid if asynchronous is set to true, if not, we don't need to specify
          a function.
        */
      }
    }
  })();
</script>
{% endhighlight %}

-----

##### **Reference:**
- [What's AJAX? - Getting Started](https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started)
