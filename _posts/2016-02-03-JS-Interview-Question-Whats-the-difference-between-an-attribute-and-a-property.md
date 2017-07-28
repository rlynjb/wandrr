---
layout: post
title: "What's the difference between an 'attribute' and a 'property'?"
date: 2016-02-03 12:41:57
tags:
- javascript interview questions
---

### recalling basics of JavaScript

Everything in JavaScript is an object. These objects are categorized in different types (functions, boolean, string, number, etc) and can also contain properties and methods.
Objects doesn't just exist in the language itself (JavaScript), but in Browser Object Model (BOM) and Document Object Model (DOM) as well. [More info on browser environment](http://javascript.info/tutorial/browser-environment)

-----

### objects in DOM

Every element in the DOM is an object and these objects have properties as well. These properties are mapped to a set of attributes from an `html` markups. An attribute is just a string in an element (usually, `label='value'` pair).

Some of the element's properties get their initial values from attributes with the same or similar names. Some examples below:

- **href** property gets its initial value from the `href` attribute, but there is an interpretation involved.
- **className** property gets its value from `class` attribute.
- other properties get their initial values in other ways.
- an element always has a **style** property, whether it has a `style` attribute or not.
- a number of properties write back to the attribute they derived from if you set them, but some may have an interpretation involved. Example: `href`

Consider example below for points above.

{% highlight javascript %}
// html element markup
<a href='foo.html' class='test one' name='fooAnchor' id='fooAnchor'>Hi</a>

// element object
+-------------------------------------------+
| a                                         |
+-------------------------------------------+
| href:      "http://example.com/foo.html"  |
| name:      "fooAnchor"                    |
| id:        "fooAnchor"                    |
| className: "test one"                     |
| attributes:                               |
|    href:  "foo.html"                      |
|    name:  "fooAnchor"                     |
|    id:    "fooAnchor"                     |
|    class: "test one"                      |
+-------------------------------------------+
{% endhighlight %}


Most of the time, its better to work with properties. Their values and names tend to be consistent across browsers.
We'll only work with attributes when there is no properties set, example is custom attributes `data-foobar`.



-----

##### **References:**

- [Browser environment](http://javascript.info/tutorial/browser-environment)
- [.prop() vs .attr()](http://stackoverflow.com/questions/5874652/prop-vs-attr/5884994#5884994)
- [HTML: The difference between attribute and property](http://jquery-howto.blogspot.com/2011/06/html-difference-between-attribute-and.html)
