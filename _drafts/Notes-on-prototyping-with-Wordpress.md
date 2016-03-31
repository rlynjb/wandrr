---
layout: post
title: "Notes on Prototyping with Wordpress"
date: 2016-03-30 11:00:51
tags:
- wordpress
---

This is a continuation of my [Front-End workflow with Wordpress](/Front-End-workflow-with-Wordpress) blog post, containing notes and personal opinion on tools/frameworks used for prototyping, getting more indepth with top 2 of my chosen Wordpress Foundation Themes.

-----

### Why use a CSS Preprocessors

Reason why I included this segment, working with different developers, each has their own preference and opinion towards modern development tools. Not all agree with Node.js and modern front-end development tools. As a Front-End Developer though, I've experience the learning curve and benefits of using such tools. Below are articles regarding CSS Processor - SASS.

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
