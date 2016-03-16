---
layout: post
title: "Explain Function.prototype.bind"
date: 2016-01-20 10:47:13
tags:
- javascript interview questions
---

### Explain Function.prototype.bind

It took me awhile to understand how `this` keyword works, but after reading about bind method, its starting to make sense regarding the context of an object set explicitly and being able to access with `this` keyword.

-----

**A common issue that arise when we use functions is dealing with a function’s scope and an object’s context.**

_** it’s important to understand the difference between function scope and object context._

Every function has its own scope with visible and accessible variables, but when we define closures, these inner functions creates its own scope as well. If we were to access the outer function’s context from inner functions (closures), we will need to declare a variable specifying the outer function’s context.

{% highlight javascript %}
var self = this;
{% endhighlight %}

To avoid polluting an outer function’s scope, we can use bind method instead. Once we invoked a function with bind method, it bounds our closure or inner function with the outer function’s scope.

{% highlight javascript %}
var foo = function() {
  // some content 
  console.log(this);
}.bind(this);
{% endhighlight %}

We are also able to pass in 2nd arguments if needed.

Though, IE8 and below doesn’t support `bind()`, there is a polyfill available to fix this issue.
[Polyfill here and more info](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)

-----

**There are other methods of setting the scope of a function.**
Other two are `apply() & call()`. Difference between `apply() & call()` and `bind()` method is:

Functions invoked with `apply() & call()` methods gets executed first and of course, we also pass along the function’s scope as well

… while …

Functions invoked with `bind()` method just sets the scope, but doesn’t get executed. Awesome! B-)

-----

**Now another issue is when we pass around functions.** Its function context actually changes as well depending on where the function is invoked. It doesn’t necessarily bound to a specific object as we expect it to be bound to, rather, it may also bound to a global object, other outer objects, or even an HTML element, depending on where we invoked the function.

_** Note, that invoking a function is different from creating a new instance of an object._

Below is an interesting (coz its new to me) Code sample with commented out explanation. It shows how `this` keyword can be mistakenly bound to an HTML element and how `bind()` can fix it.

<iframe height='268' scrolling='no' src='//codepen.io/rlynjb/embed/qbpZVX/?height=268&theme-id=20698&default-tab=js' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/rlynjb/pen/qbpZVX/'>Learning Javascript's bind method</a> by rlynjb (<a href='http://codepen.io/rlynjb'>@rlynjb</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

-----


##### **References:**

- [JavaScript's Apply, Call, and Bind Methods are Essential for JavaScript Professionals](http://javascriptissexy.com/javascript-apply-call-and-bind-methods-are-essential-for-javascript-professionals)
- [JavaScript: bind function](http://krasimirtsonev.com/blog/article/JavaScript-bind-function-setting-a-scope)
