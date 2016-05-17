---
layout: post
title: "Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?"
date: 2016-05-16 11:03:37
tags:
- javascript interview questions
---

There are various reasons why Global Variables are bad. This can include performance, name collision, or bad code readability/organization.

Pointers below are from [Global Variables Are Bad](http://c2.com/cgi/wiki?GlobalVariablesAreBad) that were paraphrased in layman's term.

- **Non-locality** - Code is easier to understand when parts of an app is limited to its own scope. Its easy to forget what a variable is intended for, but setting local variables in its own scope can help alleviate bad code readability/organization.
- **No Access Control or Constraint Checking** - Any part of an app can easily get or set a global variable and this can cause an app to easily break.
- **Namespace pollution** - When setting a variable globally, they will be available in any parts of your code, thus, causing variable name collision and polluting the global namespace with unnecessary variables for certain parts of an app when executed.


-----

##### **References:**

- [Global Variables Are Bad](http://c2.com/cgi/wiki?GlobalVariablesAreBad)
