---
layout: post
title: 'Why is it called a Ternary expression, what does the word "Ternary" indicate?'
date: 2016-05-05 16:22:31
tags:
- javascript interview questions
---

Ternary `?:` is an operator that takes 3 arguments and defines a conditional expression. It is a one-lined shorthand for an **if-then statement** and is also called Ternary operator or Conditional operator.

An example would be:

{% highlight javascript %}
if (fooTrue) {
  bar();
} else {
  fuzz();
}
{% endhighlight %}

Above code can be shortened with `?:`.

{% highlight javascript %}
fooTrue ? bar() : fuzz();
{% endhighlight %}

In JavaScript, conditional operators can be evaluated to an **Expression**, not just statement.

{% highlight javascript %}
// assigned to a variable
var isFoo = fooTrue ? "yes" : "no";

// passed as an argument in a function
getFoo(fooTrue ? "yes" : "no");
{% endhighlight %}

##### **References:**

- [Wiki - Ternary operation](https://en.wikipedia.org/wiki/Ternary_operation)
- [MDN - Expressions and Operators: Conditional (ternary) operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Conditional_(ternary)_operator)
- [How to use the ?: (ternary) operator in JavaScript](http://stackoverflow.com/questions/6259982/how-to-use-the-ternary-operator-in-javascript)
