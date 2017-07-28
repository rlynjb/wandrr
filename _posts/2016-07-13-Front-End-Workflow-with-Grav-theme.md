---
layout: post
title: "Front-End Workflow with Grav theme"
date: 2016-07-13 12:09:47
tags:
- static site
---

This blog post explains on how I have setup a custom basic Grav theme with modern front-end workflow.

This idea have come into mind when I was assigned a project that requires the use of a CSS framework and other plugins for animations/transitions. Since I will be building websites with the same requirements, why not create a **Grav Starter Theme with Front-End Workflow**.

I will be updating this theme with tested CSS animations/transitions plugins that I think will play well with Grav and meets client's business requirements.

For documentation and updates, refer to its github repo: [Grav Theme - Front-End Flow](https://github.com/rlynjb/gravtheme-frontendflow)

-----

**Contents**

- [Before starting](#before-starting)
- [Every website project will have](#every-website-project-will-have)
- [Developing starter kit theme](#developing-starter-kit-theme)
  * [gulpfile.js setup](#gulpfilejs-setup)
  * [importing foundation components and overriding settings file](#importing-foundation-components-and-overriding-settings-file)

-----

### Before starting:

Install the following globally as it is required to run Bower and Gulp in your local dev.

- Node
- NPM or NVM if you deal with multiple node versions
- After installing Grav
  * refer to ff. link for Getting Started with Grav: []()
- `git clone` this repo inside of `/user/themes/` directory
- inside of `/user/themes/gravtheme-frontendflow/` directory, run:
  * `npm install -g`
    * required to run Bower and Gulp
  * `bower install`
    * installs 3rd-party plugins used on this theme
  * `gulp && gulp watch`
    * builds our sass files. We've carefully chose each Foundation components to avoid CSS bloats and overriding of styles.

-----

### Every website project will have:

- **Grav + Admin core**
  * To get fresh install: [Get Grav](https://getgrav.org/)
- **Basic Grav Theme setup**
  * Follow tutorial to get started: [Get Grav - Theme Tutorial](https://learn.getgrav.org/themes/theme-tutorial)
- `package.json` file
  * installs **Bower**, **Gulp.js**, and other gulp dependencies for build system and front-end workflow aid
  * go to [npmjs.com](https://www.npmjs.com/) to search for more packages
- `bower.json` file
  * installs required 3rd-party assets
  * go to [bower.io](http://bower.io) to search for more packages
  * or install packages via **Github repos**
    * [bower.io - api](https://bower.io/docs/api/)
    * [Installing a dependency with Bower from URL and specify version](http://stackoverflow.com/questions/19348076/installing-a-dependency-with-bower-from-url-and-specify-version)
- setup `gulpfile.js` file
  * Why use **Gulp.js**?
    * **Sass** seem to not support building multiple `scss` files. It require either Compass, Grunt, or libsass (same Build system concept as Gulp.js)
    * **Grav's Asset Manager** lacks support for sass and its still quite buggy

> Check this project's github repo for **package.json**, **bower.json**, and **gulp.js** updates.<br>
> [Grav Theme - Front-End Flow](https://github.com/rlynjb/gravtheme-frontendflow)

-----

### Developing starter kit theme

During developing **Grav Theme - Front-End Flow** starter kit theme, I have come across issues that I think worth noting.

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
