---
layout: post
title: "JS Interview Question: Difference between: function Person(){}, var person = Person(), and var person = new Person()?"
date: 2016-01-14 10:47:13
tags:
- javascript
- interview question
---

### JS Interview Question: Difference between: function Person(){}, var person = Person(), and var person = new Person()?

There are different ways (not to be exact) we can use functions in JavaScript, but with the given code below highlights important differences on how functions work.

{% highlight javascript %}
function Person() {
  // code here
}
{% endhighlight %}

**Function Declaration** <br>
Code above declares a function statement (statements perform an action) but does not execute, however, it does get registered into the global namespace.

-----

{% highlight javascript %}
var person = Person()
{% endhighlight %}

**Function Expression** <br>
A variable ‘var person’ has been defined and contains a value reference to a Person function. Any JavaScript Expressions (including Function Expressions) always returns a value. This may also be an Anonymous function if no name has been assign to a function but wrapped in parenthesis to be interpreted as an expression.

-----

{% highlight javascript %}
var person = new Person()
{% endhighlight %}

**Function Constructor** <br>
By adding the keyword `new`. We are instantiating a new object of the Person class constructor. A function declaration is just a regular function unless it has been instantiated, it then becomes a class constructor.


-----

##### **References:**

- [Expressions versus statements in JavaScript](http://www.2ality.com/2012/09/expressions-vs-statements.html)
