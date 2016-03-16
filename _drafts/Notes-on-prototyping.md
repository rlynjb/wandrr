---
layout: post
title: "Notes on Prototyping"
date: 2015-01-01 01:01:01
tags:
- wordpress
---

This is a continuation of my [Front-End workflow with Wordpress](/Front-End-workflow-with-Wordpress) post.

This blog post contains notes and personal opinion with the tools used for prototyping. This is the actual part of getting dirty with the code and framework.

-----

### Advantages of using a CSS Preprocessors

Here is an interesting article about the [Power of SASS and its advantages for Front-End Engineers](http://1stwebdesigner.com/power-sass-why-use-css-preprocessors/)

Here are listed [features of CSS Preprocessors](http://blog.blakesimpson.co.uk/read/37-less-sass-the-advantages-of-css-preprocessing-explained)

[Debugging CSS Preprocessor on Chrome Dev Tool](https://developer.chrome.com/devtools/docs/css-preprocessors)


-----

### Choosing a WP theme with Foundation to work with

So remember my previous blogpost 'Front-End Workflow with Wordpress' and mentioned using 'FoundationPress'. After playing around with the theme further, I decided to go with 'JointsWP'.

with foundationpress, setting it up was easy and creating templates, but when I got to the header menu template. I was trying to understand what was going on with FoundationPress. It got really confusing on how the menu was set up and the theme itself doens't have much documentation.

So i looked further and played around with JointsWP.

My first impression was understanding with how they layout their menu was easy. and right off the install, they are using Foundation's Off-canvas menu. Though I am still wondering why most theme would breakdown its menu html markups to pieces of template.

JointsWP also provides documentation for its theme. So besides Zurb Foundation documentation, there is also JointsWP documentation.

although, FoundationPress provides documentation but it seems like its still underdevelope.

As with other themes, JointsWP did just that but not as confusing as FoundationPress.


-----

### Starting workflow...

Create main pages on wordpress dashboard.

work with header first.. set initial logo and menu items

set up Orbitz (carousel), go to zurb foundation documentation for instructions to implement carousel or any other js component.

-----

### Converting pieces of data to WP Custom Fields

For this task, I will be using this plugin called [AdvanceCustomFields](http://www.advancedcustomfields.com/)

It is easier to implement custom fields to posts, custom post type, pages and customize how form will be displayed on wp admin dashboard.

It is also developer friendly, providing proper documentation and API.
