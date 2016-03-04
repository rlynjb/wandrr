---
layout: post
title: "Vanilla JavaScript Router and Templating"
date: 2016-02-29 12:42:24
tags:
- javascript
---

I'm working on a simple app that requires a vanilla JavaScript routing system. Did some readings and it turns out there are various ways we can implement a vanilla JS routing system, but I will only mention 3 common methods:

- Using [onhashchange event](https://developer.mozilla.org/en-US/docs/Web/API/Window.onhashchange) and [onload event](https://developer.mozilla.org/en-US/docs/Web/API/Window.onload)
  - I believe is the simplest method so far.
- Using [HTML5 History API](https://developer.mozilla.org/en-US/docs/Web/API/History_API)
  - Still buggy for cross-browser compatibility
- Using small JS plugin called [History.js](https://github.com/browserstate/history.js)
  - This extends HTML5 History API and fixes cross-browser compatibility issues.
  - More info on their [Github Gist - Intelligent State Handling](https://developer.mozilla.org/en-US/docs/Web/API/Window.onload)

For this app project, I will use the first method. Thanks to:

- [Joakim Carlstein's - A JavaScript router in 20 lines](http://joakim.beng.se/blog/posts/a-javascript-router-in-20-lines.html) and
- [John Resig's - JavaScript Micro-Templating](http://ejohn.org/blog/javascript-micro-templating/).

-----

### Why go this Route?

Both each scripts only contains 20 lines of code, overall, its about 40 lines of code compare to using a 3rd-party JS plugin. I wanted to keep my code simple and understanding these scripts source code is easy. Its also a good way to learn Routing and Templating system as well. At the moment, I am not concern about cross-browser compatibility and other issues that may arise.

-----

**For complete example:**

<p data-height="268" data-theme-id="20698" data-slug-hash="RaNGvZ" data-default-tab="result" data-user="rlynjb" class='codepen'>See the Pen <a href='http://codepen.io/rlynjb/pen/RaNGvZ/'>vanilla javascript routing</a> by rlynjb (<a href='http://codepen.io/rlynjb'>@rlynjb</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

-----

**Update: 03-04-2016**

### Delegated Events - Click event doesn't work on dynamically generated elements

This was an issue I've come across while using this script. When binding a `click` event unto a dynamically generated element, we need to delegate that certain element to its parent element that holds the dynamically generated chiild elements.

Code would look as follows, using jQuery `on` event:

{% highlight javascript %}
$('#view').on('click', 'button#shuffle', function() {
  $('#view').html('');
  this.getData();
}.bind(this));
{% endhighlight %}

##### **References:**

- [Click event doesn't work on dynamically generated elements](http://stackoverflow.com/questions/6658752/click-event-doesnt-work-on-dynamically-generated-elements)
- [event delegation vs direct binding when adding complex elements to a page](http://stackoverflow.com/questions/8827430/event-delegation-vs-direct-binding-when-adding-complex-elements-to-a-page)
