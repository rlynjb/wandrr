---
layout: post
title: "What's the difference between an 'attribute' and a 'property'?"
date: 2016-02-02 12:13:01
tags:
- javascript
- interview question
---

### recalling basics of JavaScript

Everything in JavaScript is an object. These objects are categorized in different types (functions, boolean, string, number, etc) and can also contain properties and methods.

Objects doesn't just exist in the language itself (JavaScript), but in Browser Object Model (BOM) and Document Object Model (DOM) as well. [More info on browser environment](http://javascript.info/tutorial/browser-environment)

-----

### objects in DOM

Every element in the DOM is an object and these objects have properties as well. These properties are mapped to an attribute. An attribute is just a string in an element and contains an initial value or a value from its property.

{% highlight javascript %}
// html element
<a href='foo.html' class='test one' name='fooAnchor' id='fooAnchor'>Hi</a>

// element object
+-------------------------------------------+
| a                                         |
+-------------------------------------------+
| href:       "http://example.com/foo.html" |
| name:       "fooAnchor"                   |
| id:         "fooAnchor"                   |
| className:  "test one"                    |
| attributes:                               |
|    href:  "foo.html"                      |
|    name:  "fooAnchor"                     |
|    id:    "fooAnchor"                     |
|    class: "test one"                      |
+-------------------------------------------+
{% endhighlight %}



-----

##### **References:**

- [Browser environment](http://javascript.info/tutorial/browser-environment)
- [.prop() vs .attr()](http://stackoverflow.com/questions/5874652/prop-vs-attr/5884994#5884994)
- [HTML: The difference between attribute and property](http://jquery-howto.blogspot.com/2011/06/html-difference-between-attribute-and.html)
