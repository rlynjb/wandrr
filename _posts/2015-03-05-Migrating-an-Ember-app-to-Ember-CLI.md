---
layout: post
title: "Migrating an Ember app to Ember-CLI"
date: 2015-01-05 10:47:13
tags:
- ember.js
---

Turns out there are 2 major ways to migrate an Ember project to Ember-CLI.
Found this video very useful for finding ways of migrating to Ember-CLI.

[Moving to Ember CLI from Ember Appkit](http://www.sparkcasts.net/posts/12-moving-to-ember-cli-from-ember-appkit-pro)

So with this, I decided to go with Copy & Paste method. I’ve looked online on how people are doing this and I found this article.

[From Gulp.js to ember-cli](https://medium.com/p/450f1ffb1967)

-----

### Moving Forward..

So with these informations, I was ready to migrate my app to Ember-CLI. Along the way, I came across errors and issues. Below are some useful tips to solve errors.

- Solving errors along the way, Google Dev Console is our friend! So turn on the console to get started.
- If your new to writing ES6 modules syntax, here is a good resource [ES6 Modules Final](http://www.2ality.com/2014/09/es6-modules-final.html)
- Inside config/ -> environment.js.. uncomment out

{% highlight javascript %}
ENV.APP.LOG_RESOLVER = true;
ENV.APP.LOG_ACTIVE_GENERATION = true;
ENV.APP.LOG_TRANSITIONS = true;
ENV.APP.LOG_TRANSITIONS_INTERNAL = true;
ENV.APP.LOG_VIEW_LOOKUPS = true;
{% endhighlight %}

These will log errors and transitions in your Dev Console.
- Follow Ember-CLI’s documentation on **Getting Started** section > **Folder Structure and its Purpose**
- Another important topic is **Using Modules & The Resolver**

** _Note, that the name of the variable used in the exported module doesn’t have any influence on the resolver. It’s the filename that is used to resolve modules._

So with this, in my opinion, it seems like Ember-CLI has its own way of organizing files (as described “convention over configuration”). I was able to Export one module per file.
** _Please if you found a way to Export multiple modules per file, feel free to share._

- And Naming Convention section
- Also, keep in mind the file path when importing a module.
