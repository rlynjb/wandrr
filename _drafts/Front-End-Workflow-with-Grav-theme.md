---
layout: post
title: "Front-End Workflow with Grav theme"
date: 2016-07-12 12:48:43
tags:
- static site
---

### Before starting:

Install the following **globally**. I've placed my `package.json` file on my `htdocs` root directory.

- node
- npm
  * start a `package.json` file by running `npm init`
- install `npm install bower --save-dev`
- install `npm install gulp --save-dev`

-----

### Every website project will have:

- Grav + Admin core install
- Basic Grav Theme setup
  * Follow the tutorial to get started: [Get Grav - Theme Tutorial](https://learn.getgrav.org/themes/theme-tutorial)
  * setup `bower.json` file to install required 3rd-party assets
    * foundation-sites
      * we will not be using `dist` ditribution files
      * we'll only take necessary files by using **gulp** to build our `css` and `js` files
    * skrollr
    * font-awesome
    * go to [bower.io](http://bower.io) to search for more packages
  * setup `gulpfile.js`
    * Why use **Gulp.js**?
      * **Sass** seem to not support building multiple `scss` files. It require either Compass, Grunt, or libsass (same Build system concept as Gulp.js)
      * **Grav's Asset Manager** lacks support for sass and its still quite buggy

-----

### gulpfile.js setup

After installing **foundation-sites** via bower. we will need to setup our `gulpfile.js` file.

Follow the youtube video tutorial to get started:

<iframe width="560" height="315" src="https://www.youtube.com/embed/De6H0eFrfvY" frameborder="0" allowfullscreen></iframe>

-----

### importing foundation components and overriding settings file

While setting it up, I've come across an issue. The following link helped me solved the issue.

[stackoverflow - Foundation 6 does not generate any styles](http://stackoverflow.com/questions/34537431/foundation-6-does-not-generate-any-styles)

Another issue i came across was overriding Foundation's settings file. It took me awhile until I figured out why its not overriding the default settings file. Solution is on my github repo

[GravTheme - Front End Flow theme](https://github.com/rlynjb/gravtheme-frontendflow)
