---
layout: post
title: "JS Interview Question: What’s the difference between feature detection, feature inference, and using the UA string?"
date: 2016-01-20 10:47:13
tags:
- javascript
- interview question
---

### What’s the difference between feature detection, feature inference, and using the UA string?

These 3 are just practices of determining if a certain web technology feature exists in a user’s browser or environment. Though features may vary with not just modern web technology but with programming languages as well.

-----

***Feature Detection***

Feature detection is just a way of determining if a feature exists in certain browsers. A good example is a modern HTML5 feature ‘Location’.

{% highlight javascript %}
if (navigator.geolocation) {
  // detect users location here B-) and do something awesome
}
{% endhighlight %}

-----

***Feature Inference***

Feature Inference is when you have determined a feature exists and assumed the next web technology feature you are implementing unto your app exists as well. Its usually bad practice to assume, so its better to explicitly specify features you want to detect and plan a fallback action.

-----

***UA String***

UA String or User Agent String is a string text of data that each browsers send and can be access via navigator.userAgent. These “string text of data” contains information of the browser environment you are targeting.

If you open your console and run

```
navigator.userAgent
```

You’ll see it outputs a “string text of data” containing complete information of the environment you are currently using. Since this is an old way of doing detection, this method can be easily spoofed, thus, may not be the best route to take. Ref: https://en.wikipedia.org/wiki/User_agent

-----

***A JavaScript library I love using is Modernizr***

> Modernizr is a small piece of JavaScript code that automatically detects the availability of next-generation web technologies in your user’s browsers. Rather than blacklisting entire ranges of browsers based on “UA sniffing,” Modernizr uses feature detection to allow you to easily tailor your user’s experiences based on the actual capabilities of their browser.

[Modernizr: the feature detection library for HTML5/CSS3](https://modernizr.com/)

-----

#### References:

- [What's the difference between feature detection, feature inference, and using the UA string](http://stackoverflow.com/a/20105074/4538744)
