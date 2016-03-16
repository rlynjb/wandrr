---
layout: post
title: "Describe event bubbling"
date: 2016-02-02 12:08:15
tags:
- javascript interview questions
---

Event bubbling is when handlers on a nested DOM are triggered starting from the child element up to its parent element.

This means, eventhough we clicked on a child element, its parent element which contains a handler, will be triggered as well. That's why it's called **Event bubbling**, it is triggered from innermost child element that has been clicked up through topmost parent element.

-----

### this and event.target

When the innermost child element has been triggered, the event is called _'the target'_, _'the originating element'_, or `event.target`. Internet Explorer uses `event.srcElement` while all W3C-compliant browsers use `event.target`.

Cross-browser code usually looks like this:

{% highlight javascript %}
var target = event.target || event.srcElement;
{% endhighlight %}

When handlers on its topmost parent elements are triggered, the event is called `this`.

So when a Event Bubble occurs, `this` object changes its value going from innermost triggered child element to its topmost parent element, while `event.target` contains the same value as it holds _'the originating element'_.

-----

### stop the event bubbling

An event bubble will occur as long as its topmost element contains a handler, even in `<html>` element.
We can stop the event bubbling in a certain handler by invoking the following method:

{% highlight javascript %}
// For W3C-compliant browsers
event.stopPropagation();

// For IE<9
event.cancelBubble = true;

// Cross-browser code:
element.onclick = function(event) {
  event = event || window.event // cross-browser event;

  if (event.stopPropagation) {
    // W3C standard variant
    event.stopPropagation();
  } else {
    // IE variant
    event.cancelBubble = true;
  }
}
{% endhighlight %}

Here is a one-line variant:

{% highlight javascript %}
event.stopPropagation ? event.stopPropagation() : (event.cancelBubble=true);
{% endhighlight %}

_* Multiple handlers, initiated in the same element, will get executed._

There is a reverse version of Event Bubbling called 'Capturing', but I will not go further into it. You can click on the link below for more info.



-----

##### **References:**

- [Bubbling and capturing](http://javascript.info/tutorial/bubbling-and-capturing)
