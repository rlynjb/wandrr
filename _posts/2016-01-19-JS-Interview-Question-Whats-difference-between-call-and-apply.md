---
layout: post
title: "What’s the difference between .call and .apply?"
date: 2016-01-19 10:47:13
tags:
- javascript interview questions
---

### What’s the difference between .call and .apply?

**Recalling the basics** <br>
Remember, in JavaScript, everything are objects, even Functions, and every objects has their properties and methods. Both `.apply` and `.call` are methods of Function object.

-----

**How do .apply or .call work?** <br>
Invoking a function with `.apply` and `.call` allows us to point an object to the invoked function by passing in the object as first argument and second argument (and so on) as its values.

The function’s `this` keyword will be manipulated when invoked with `.apply` or `.call`.

From what I understand, `.apply` and `.call` are methods we use to assign the `this` keyword from the invoked function to reference to an object for the duration of the method invocation.

Below is a code example with commented explanation.

<iframe height='268' scrolling='no' src='//codepen.io/rlynjb/embed/JGOmwp/?height=268&theme-id=20698&default-tab=js' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/rlynjb/pen/JGOmwp/'>learning JavaScript's .apply and .call</a> by rlynjb (<a href='http://codepen.io/rlynjb'>@rlynjb</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

-----

**So what’s the difference between .apply and .call?** <br>
Besides passing in an argument to a `.call` or `.apply` methods that references to the `this` keyword of an invoked function, we can also pass in a 2nd argument or more. A good mnemonic to explain their differences are:

_`.call` Counts the number of arguments separated by Comma_ <br>
.call method accepts one or more arguments as objects and requires to be listed explicitly, means, it is a fixed number of arguments.

{% highlight javascript %}
foo.call(object, “other argument”, “another one”);
{% endhighlight %}

_... while ..._

_`.apply` uses Array as an Argument_ <br>
.apply method requires an array as its 2nd argument. This method is used if you don’t know the number of arguments to be passed or the arguments is already in an array.

{% highlight javascript %}
foo.apply(object, [“argument1”, “argument2”, “argument3”]);
{% endhighlight %}

** _Open CodePen above for Code sample_


-----

##### **References:**

- [What is the difference between call and apply?](http://stackoverflow.com/questions/1986896/what-is-the-difference-between-call-and-apply/1987244)
- [Function.apply and Function.call in JavaScript](http://odetocode.com/blogs/scott/archive/2007/07/04/function-apply-and-function-call-in-javascript.aspx)
