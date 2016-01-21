---
layout: post
title: "JS Interview Question: Explain how prototypal inheritance works"
date: 2016-01-05 10:47:13
tags:
- javascript
- interview question
---

Everything in Javascript is an object. Even when creating a Class is an Object via an Object Literal or Constructor Function. This is how Javascript does class-based programming as to other traditional Object-Oriented Programming languages where they use the keyword ‘class’ and ‘inheritance’.

Javascript’s version of class-based programming and other traditional class-based programming languages work with the same concept but does not work exactly similar. There are differences in its keyword, syntax, and how it works. There are also debates regarding pros and cons of Javascript’s version of class-based programming, but for simplicity’s sake and learning purposes, I do not want to go over those issues. See details here [http://www.2ality.com/2011/11/javascript-classes.html].

So, the core idea of Prototypal Inheritance is that an object can point to another object and inherit all its properties. The main purpose is to allow multiple instances of an object to share common properties, hence, the Singleton Pattern.

Below is a sample code with comments and caption to better see how it works:

After going through the code, its best to read further about Prototypal Inheritance from mozilla doc. Code example below is just one of many ways of implementing Prototypal Inheritance.

[developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

<iframe height='268' scrolling='no' src='//codepen.io/rlynjb/embed/xZqJNL/?height=268&theme-id=20698&default-tab=js' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/rlynjb/pen/xZqJNL/'>learning prototypal inheritance</a> by rlynjb (<a href='http://codepen.io/rlynjb'>@rlynjb</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

-----

#### Reference:

[htmlgoodies.com](http://www.htmlgoodies.com/html5/tutorials/javascript-prototypical-inheritance-explained.html#fbid=iKcMD3kLi8E)
