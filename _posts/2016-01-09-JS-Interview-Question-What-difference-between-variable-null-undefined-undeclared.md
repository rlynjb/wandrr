---
layout: post
title: "JS Interview Question: What’s the difference between a variable that is: null, undefined or undeclared?"
date: 2016-01-09 10:47:13
tags:
- javascript
- interview question
---

### What’s the difference between a variable that is: null, undefined or undeclared?

### How would you go about checking for any of these states?

From what I understand, in Javascript, `undefined` and `null` are somewhat related on what value a variable contains. The case for `undeclared` differs. It tackles on how a variable is defined and how javascript treats these variables. So I am going to discuss undefined and null first since both are on Data Type category.

-----

`undefined` is a variable that has been declared but no value exists and is a type of itself 'undefined'.

`null` is a value of a variable and is a type of object.

We use `console.log();` and `type of` to check if a variable is `undefined` or `null`.

[JavaScript data types and data structures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)

-----

`undeclared` variables is a variable that has been declared without `var` keyword.

{% highlight javascript %}
testVar = "hello world";
{% endhighlight %}

as opposed to

{% highlight javascript %}
var testVar = "hello world";
{% endhighlight %}

When former code is executed, `undeclared` variables are created as global variable and they are configurable (ex. can be deleted).

[JavaScript data types and data structures: var](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)
