---
layout: post
title: "JS Interview Question: What’s a typical use case for anonymous functions?"
date: 2016-01-12 10:47:13
tags:
- javascript
- interview question
---

### What’s a typical use case for anonymous functions?

Since Anonymous Functions are function expressions rather than the regular function declaration which are statements. Function expressions are more flexible. We can assign functions to variables, object properties, pass them as arguments to other functions, and even write a simple one line code enclosed in an anonymous functions.

Example:

{% highlight javascript %}
var squaredArray = inputArray.map(function(x) {
  return x * x;
});
{% endhighlight %}

With ES6 syntax this becomes even more concise.

{% highlight javascript %}
var squaredArray = inputArray.map( x => x * x );
{% endhighlight %}

Another typical example would be an anonymous function used by popular frameworks used as IIFE (Immediate Invoked Function Expression).

{% highlight javascript %}
(function() {
  
})();
{% endhighlight %}
