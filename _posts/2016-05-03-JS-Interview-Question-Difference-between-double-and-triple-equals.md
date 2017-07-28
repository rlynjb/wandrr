---
layout: post
title: "What is the difference between == and ===?"
date: 2016-05-03 14:00:07
tags:
- javascript interview questions
---

JavaScript has two sets of **_Equality operators_** archived under [Comparison operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators):

- equality `==` & inequality `!=`
- strict equality `===` & strict inequality `!==`

We use these operators when comparing 2 operands. They differ on what type of operands are being compared to against.

For example, equality `==` or inequality `!=` signs compares 2 values without type conversion. 
<br>
While strict equality `===` or strict inequality `!==` signs compares 2 values with type conversion.

{% highlight javascript %}
'1' == 1 // true < all it matters is the value
'1' === 1 // false < they are not the same type

1 == true // true
'1' == true // true

1 === true // false
'1' === true // false
{% endhighlight %}

-----

##### **References:**

- [Does it matter which equals operator (== vs ===) I use in JavaScript comparisons?](http://stackoverflow.com/questions/359494/does-it-matter-which-equals-operator-vs-i-use-in-javascript-comparisons)
- [Comparison operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators)
