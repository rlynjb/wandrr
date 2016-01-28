---
layout: post
title: "Explain 'hoisting'"
date: 2016-01-28 13:27:00
tags:
- javascript
- interview question
---

As defined in dictionary.com, Hoisting means to lift or raise. **In JavaScript**, Hoisting is when we declare variables and are hoisted to the top of a function scope or to the top of the global scope depending on where it is declared. Remember, JavaScript have a **function-level scope** as oppose to **block-level scope** in other languages.

** _Note, we must first understand the concept of JavaScript Variable Scope as this is the basis of Hoisting_

-----

### Variable Hoisting

Only **variable declarations** are hoisted to the top and not **variable initializations** (variable assignments or variables with assigned values).

**_First example,_**

{% highlight javascript %}
/*
  just a simple function declaration.
  this function declaration has its own scope.
  we are not declaring variables on global scope (outside of function)
*/
function showBar() {
  console.log('1st word ' + foo); // output: undefined
  /*
    Reason why its 'undefined' is we did not declare
    a variable called 'foo' before we called it.
    It cannot find variable foo.
  */

  // yey, we finally declared it
  var foo = 'bar';

  console.log('2nd word ' + foo); // output: bar
  /*
    Since we declared variable 'foo' after we called it.
    It now finds variable foo.
  */
}

showBar();
/*
  console output:
  1st word undefined
  2nd word bar
*/

{% endhighlight %}

**_Second example,_**

{% highlight javascript %}
/*
  same function declaration, but different Hoisting example
*/
function showBar() {
  /*
    here, we declared variable 'foo' first, and is
    located at the very top of function (Hoisting)
  */
  var foo;

  console.log('1st word ' + foo); // output: undefined
  /*
    still outputs 'undefined', why?
    eventhough we declared variable foo after we called it,
    variable foo doesn't hold any value.
    its just a variable declaration without a value.
  */

  foo = 'bar';
  /*
    here, we are now assigning variable 'foo' with a string value.
    though, variable assignments aren't hosted. that is why
    our 1st word display is outputting undefined.
  */

  console.log('2nd word ' + foo); // output: bar
  /*
    since we assigned a value to variable foo.
    it now has a value to display
  */
}

showBar();
/*
  console output:
  1st word undefined
  2nd word bar
*/

{% endhighlight %}

-----

### Function Declarations Overrides Variables Declaration When Hoisted

**Function declarations** and **variables declarations** will always be hoisted at the top of scope.<br>
**Function declarations** will always override **variable declarations**.

{% highlight javascript %}
var foo;

function foo() {
  console.log('bar');
}

console.log(typeof foo); // output: function
{% endhighlight %}

although, **variable declarations** will override **function declarations**

{% highlight javascript %}
var foo = 'buzz';

function foo() {
  console.log('bar');
}

console.log(typeof foo); // output: string
{% endhighlight %}

**Function expressions** (function assignments) as well as **variable initialization** (variable assignments) are not hoisted.

{% highlight javascript %}
var bar = function() {
  console.log('qux');
}

foo = 'buzz';
{% endhighlight %}

Also good to note that,

> In strict mode, an error will occur if you assign a variable a value without first declaring the variable. Always declare your variables.

-----

##### **References:**

- [JavaScript Variable Scope and Hosting Explained](http://javascriptissexy.com/javascript-variable-scope-and-hoisting-explained/)
