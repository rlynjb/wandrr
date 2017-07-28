---
layout: post
title: "Explain why the following doesn’t work as an IIFE"
date: 2016-01-08 10:47:13
tags:
- javascript interview questions
---

### Explain why the following doesn’t work as an IIFE: function foo(){ }();. What needs to be changed to properly make it an IIFE?

**What is IIFE?** <br>
An IIFE (pronouced as ‘iffy’) is an abbreviation for Immediately Invoked Function Expression. It is a common Javascript design pattern used by popular JS libraries such as jQuery, Backbone.js. Purpose of using an IIFE is to maintain code inside of a local scope. This means, to be able to use global object inside of IIFE, you will need to pass it as arguments.

-----

As for an explanation, the following code doesn’t work as an IIFE because it is a function declaration, it does invoked immediately due to its parenthesis at the end, but there are downsides to using this approach.

{% highlight javascript %}
function foo() {
  
}();
{% endhighlight %}

> First, it unnecessarily takes up a name in the global namespace, increasing the possibility of name collisions. Second, the intentions of this code aren’t as self-documenting as an IIFE. And third, because it is named and isn’t self-documenting it might accidentally be invoked more than once.
>
> -- http://adripofjavascript.com/blog/drips/an-introduction-to-iffes-immediately-invoked-function-expressions.html

-----

For the above code to be considered an IIFE, it needs to be an anonymous function, a function without a name, this is because IIFE needs to be Invoked Immediately without invoking it a function name. We also need to wrap the anonymous function with parenthesis, so the Javascript parser treats our anonymous function as a function expression.

{% highlight javascript %}
(function() {
  
}());
{% endhighlight%}

A function expression is when you assign a function to a variable or property of an object. Anything that is a Javascript expression, including function expression, returns a value.


-----

##### **References:**

- [An Introduction to IIFEs - Immediately Invoked Function Expressions](http://adripofjavascript.com/blog/drips/an-introduction-to-iffes-immediately-invoked-function-expressions.html)
- [I Love My IIFE - Greg Franko](http://gregfranko.com/blog/i-love-my-iife/)
