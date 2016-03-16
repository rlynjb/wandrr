---
layout: post
title: "What’s the difference between host objects and native objects?"
date: 2016-01-13 10:47:13
tags:
- javascript interview questions
---


### What’s the difference between host objects and native objects?

From what I understand, objects are divided from which environment and language they are supplied: **Host Objects** and **Native Objects**.

**Host Objects** are objects supplied by a certain environment. They are not always the same because each environment differs and contains host objects that accommodates execution of ECMAScript. Example, browser environment supplies objects such as window. While a node.js/server environment supplies objects such as NodeList.

**Native Objects** or Built-in Objects are standard built-in objects provided by Javascript. Native objects is sometimes referred to as ‘Global Objects’ since they are objects Javascript has provided natively available for use.

-----

There are various articles categorizing these native global objects but its number differs, so for accuracy (I believe), I recommend the official Mozilla Doc as reference.
[Ref: developer.mozilla.org - Global Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects)

Javascript is mainly constructed by these categorized native global objects. These objects can be used either as Constructor (String(), Number(), Boolean()) or as Primitive Value, like literally as a value :-D (‘string’, 123, true).


-----

##### **References:**

- [Host objects Vs Native objects In JavaScript](https://programmerinnervoice.wordpress.com/2013/07/22/host-objects-vs-native-objects/)
- [Standard built-in objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects)
