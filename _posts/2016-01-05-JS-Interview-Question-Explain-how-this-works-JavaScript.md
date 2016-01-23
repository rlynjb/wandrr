---
layout: post
title: "Explain how this work in JavaScript"
date: 2016-01-05 10:47:13
tags:
- javascript
- interview question
---

From what I understand, `this` refers to itself, to its own object or global object.

Using `this` are partitioned in 3 locations of code. These are in functions, outside of functions (global scope, ex: window object), and in Javascript’s eval() function.

Common pitfalls when using ‘this’ are usually relevant to scope issues in real functions, methods, and constructors. Though there are ways to fix these common issues by using ES5, bind() or ES6 arrow functions, =>

-----

##### **References:**

- [JavaScript’s “this”: how it works, where it can trip you up](http://www.2ality.com/2014/05/this.html)
