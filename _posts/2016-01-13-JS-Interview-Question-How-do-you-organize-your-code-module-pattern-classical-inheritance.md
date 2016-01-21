---
layout: post
title: "How do you organize your code? (module pattern, classical inheritance?)"
date: 2016-01-13 10:47:13
tags:
- javascript
- interview question
---

### How do you organize your code? (module pattern, classical inheritance?)

There are several options in implementing Module Pattern. An option I mostly use is Object Literal Notation for encapsulating and organizing my code, but upon further readings, Module Pattern using Anonymous Closures, Global Import, and Module Export have sparked my interest as it provides more features for private and public var/methods. It still uses object literal but as to return values from the scoping function.

> In JavaScript, the Module pattern is used to further emulate the concept of classes in such a way that we’re able to include both public/private methods and variables inside a single object, thus shielding particular parts from the global scope.
>
> -- Addy Osmani, Learning Javascript Design Patterns

There are popular javascript module framework that specifically implemented Module Pattern such as Dojo, ExtJS, YUI, and jQuery. Good to know if your new to learning Javascript concepts and have heard of these technologies before those popular MVC frameworks (Angular.js, Ember.js, Backbone.js) emerged.

Another implementation of module pattern popularized Christian Heilmann (which I think is pretty clean and neat) is The Revealing Module Pattern. It’s pretty much the same with the standard Module Pattern except it uses the return object literal properties as references to variables and functions from the scoping function to export variables and methods.

-----

##### **References:**

- [Learning JavaScript Design Patterns](https://addyosmani.com/resources/essentialjsdesignpatterns/book/#modulepatternjavascript)
- [JavaScript Module Pattern: In-Depth](http://www.adequatelygood.com/JavaScript-Module-Pattern-In-Depth.html)
