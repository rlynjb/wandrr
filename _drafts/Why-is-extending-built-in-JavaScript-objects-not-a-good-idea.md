---
layout: post
title: "Why is extending built-in JavaScript objects not a good idea?"
date: 2016-02-03 12:46:53
tags:
- javascript
- interview question
---

Extending Built-in Native Javascript Objects is most likely an opinion base rather than facts.
Common reasons why extending built-in native Javascript objects is not a good idea:

- Extending native objects isn't bad as long as were considering about **standard objects and methods**
- Extending native built-in with custom methods immediately makes "collision" problem apparent
- It violates [don't modify objects you don't own principle](https://www.nczonline.net/blog/2010/03/02/maintainable-javascript-dont-modify-objects-you-down-own/)
- It makes code not future-proof



-----

##### **References:**

- [Extending Built-In Natives. Evil or not?](http://perfectionkills.com/extending-native-builtins/)
- [Extending Built-In Objects in Javascript](https://www.kirupa.com/html5/extending_built_in_objects_javascript.htm)
