---
layout: post
title: "What is a closure, and how/why would you use one?"
date: 2016-01-12 10:47:13
tags:
- javascript
- interview question
---

### What is a closure, and how/why would you use one?

Closures are inner functions inside of an outer function. They have their own local scope and has access to outer function’s scope, parameters (but NOT arguments object), and they also have access to global variables.

From what I understand, Closures is a neat way to deal with scope issues. Reasons we use Closures is because Javascript is a function-level scope rather than as with other languages, block-level scope and Javascript is an asynchronous/event driven language. Example that Closure is frequently used is jQuery (ex. click()).

-----

**This is how Closures work.** <br>
1. After its outer function has been executed and has returned a value, closures can still run.
2. Closures store references to the outer function’s variable, hence, we will always have access to the updated values of outer function’s variables.
3. Since we have access to the updated values of outer function’s variables. We will have issue/bugs when a variable changes via for loop, but this can be fixed by using IIFE, Immediately Invoked Function Expression.

-----

Below is a sample code of using Closure with IIFE.

** _Note, IIFE or Immediately Invoked Function Expression is another Javascript concept._

<iframe height='268' scrolling='no' src='//codepen.io/rlynjb/embed/vLZeyq/?height=268&theme-id=20698&default-tab=js' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/rlynjb/pen/vLZeyq/'>learning javascript closures</a> by rlynjb (<a href='http://codepen.io/rlynjb'>@rlynjb</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>


-----

##### **References:**

- [Understand JavaScript Closures With Ease](http://javascriptissexy.com/understand-javascript-closures-with-ease/)
