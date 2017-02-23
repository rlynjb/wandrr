---
layout: post
title: "New stuff to learn"
date: 2017-02-22 16:29:22
tags:
- 3d
- webgl
- javascript
- crud
- laravel
- parallax
- ecommerce
- wordpress
---

Before delving into another new things to learn, I wanted to write a recap of what I've been doing lately. Can't really include all details but atleast write a summary of my experience.
You can read further if your interested. I blog to keep track of my learning progress about the web, I consider these as my personal note, but I don't mind sharing.

-----

## Wordpress and Static Sites

I've worked with alot of wordpress websites as sideline job and with designers and other developers. I noticed that everyone has their opinion about methods of how a work should get done. One important thing is, we should be able to deliver the product. It doesn't matter how it is built, as long as it works, its good.

- **When to code from scratch and when NOT to.**
  - I am a fan of coding things from scratch. I take into consideration how a website/application is built. But coding from scratch is not worth it when its just for sideline.
  - Things to note though are:
    * Plugins save my projects! lol
    * Follow how Wordpress, plugins work rather than customizing a workflow from scrtach.
- **Learning Woocommerce with a Fancy Product Designer plugin**
  - Came across a project that requires online sales, so we decided to use Woocommerce.
  - Components of a E-commerce website are:
    * Products have different variations
    * Shipping
    * Payment Gateway
    * again, Plugins are my hero! rather than delving into APIs
- **Static site generator**
  - Static sites are great alternative to wordpress if a website doesn't require E-commerce. But it does require learning curve for non-techie users.
  - Since static sites are new, it may not be prone to hackers like wordpress
  - Example tools are:
    * Grav - a PHP site generator, has a really nice optional Admin dashboard.
    * Jekyll - love it coz Github uses it, and you can easily publish your site for free. But doesn't have a nice Admin Dashboard like Grav.

-----

## Front-End tools and NPM community

So I just found out not all developers agree to the whole NPM community trend. IMO though, I love workflows and how easy it is to code with these tools. I love learning at the sametime, so I guess I fit into this type of development preference. 

- **Gulp.js and the whole NPM community.**
  - Gulp.js was the first built tool I learned. IMO, its an important tool so we can use other JavaScript/Front-End tools such as:
    * Template engines
    * JS transpilers
    * JS compilers
    * CSS compilers
    * workflow automation
    * testing
    * and more WOWs!
  - Most tools above are available via NPM modules.
- **Alternative to Gulp.js, such as webpack, yarn, and bash scripts**
  - It seems though built process are always evolving and we constantly have to change tools, thats why I am considering either consolidating my Gulp.js workflow to Webpack or author a simple built script.

-----

## Building my own Front-End Workflow Theme

I kinda figure I needed a codebase to collect solutions to common web problems that a CSS Framework was not able to accomodate. And also, to fit specifications of a project. So I decided to start a theme project called Front-End Flow (FEF) theme.

- **Delving deeper with Zurb Foundation**
  - Foundation is a great tool to start projects, I built my Gulp.js workflow to accomodate Zurb Foundation and other JavaScript framework/plugins.
  - But it still lacks some solutions to common web problems.
  - I may need to update FEF repo documentation though to specify these common web problems I've come across.
- **SASS/CSS part is good but JavaScript part still needs re-coding and cleaning up**
- **and converting my Gulp.js to Webpack or a bash script.**

-----

## JavaScript

These last 2 (JavaScript and FullStack/Ecommerce) are my favorite. This blog contains mostly about JavaScript concepts in theory, but this past year, I was able to put those theories in practice! I'm happy and glad I took the time to read and blog about JavaScript Interview Questions and took courses on FreeCodeCamp solving algorithms. I am 100% sure this is the route I want to go, JavaScript and becoming a Fullstack/Ecommerce developer!

Coding animations or a JavaScript SPA application, either concepts, I know I will take advantage of further practicing my coding skills and understanding of Fullstack concepts.

- **Demonstrated my JavaScript coding skills, creatively solving problems**
  - Authored code for a Personalization Platform
  - Separated my JS code using ES6 import export feature
- **Introduction to React.js**
  - I wanted to organize my JavaScript code and modularize it.
  - Coming up with code snippets to different problems is hard and I think it is worth keeping those code snippets for future use. Thats why I want to take advantage of Web Components and I heard React.js is fully developed for this usage.

-----

## Fullstack/Ecommerce

I was excited when I was able to build a simple contact form, submit it to MySQL database and display it on a Admin page. And also when I first started templating with Blade on Laravel.

Just using a MVC framework makes me think of possibilities I am able to build and how easy it is for me to be able to organize my code file structure and set naming conventions.

I'm starting to think I got this thing for Organization, cleanliness, and performance.
Anyways, below is a recap of what I've accomplished and what I want to tackle next:

- **Basic form submission and query data with PHP and MySQL**
  - This is the simple contact form and display of data.
- **Learned Laravel, from templating to submitting form with AJAX**
  - Learned how to setup Laravel
  - Templating in Blade
  - Storing and Querying data from JSON files rather than database. For performance purposes.
  - Learned how to use AJAX in submitting form in Laravel and storing it in database.
- **Introduction to CRUD with Laravel**
  - After having a glimpse and hands-on experience with Laravel, I was able to get an idea of how CRUD systems are structured in Laravel
  - yup! I want to build an Admin Dashboard where users are able to edit data coming from a JSON file.
  - kinda like building my own Jekyll or Grav but flexible enough to accomodate database
- **Introduction to E-commerce system with plain PHP, Javascript**
  - I was given a chance to author code for a Personalization platform. I was quite challenged with this project, solving problems creatively.
  - I've also learned how a JavaScript application is structured with an E-commerce system
    * Adding to cart by storing values to PHP Session
    * Using Session to keep data throughout Edit page, Add To Cart modal, Cart item page, Checkout page, and last, Order confirmation.

-----

So there it is, after blogging a recap of what I've learned, I should be able to distinguish my next set of concepts/topics to learn and skills to have under my belt.


### Moving forward:

- **Wordpress**
  - start a sideline business, hopefully it works well
- **Building FEF Theme**
  - convert gulp.js to webpack or script
  - organize JS files
  - use web components
- **JavaScript**
  - code more, blog more on JS Interview Questions
  - look into testing, interaction of application and inputting sample information
  - exciting new projects to learn:
    * 3d model product viewer
    * viewport scroll to snap then animation/transition starts
- **FullStack/E-commerce**
  - Continue building an Admin Dashboard
  - the whole CRUD shibang!
  and a mixture of static JSON data and database
- **HTML5/CSS3**
  - learn more about SVG
  - implement simple CSS3 transitions
