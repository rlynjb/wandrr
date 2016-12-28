---
layout: post
title: "Using ES6 Modules in client-side"
date: 2016-12-28 11:08:39
tags:
- javascript
---

I came into a halt where I need to split my JavaScript code. Prototyping an application, code can be done in one file but as it grows and add-on features are requested, lines of code will eventually increase. I've heard a few names of javascript module loaders, both for client and server. But what I really wanted to take advantage of is JavaScript's new module feature, 'ES6 Module' `import` `export` (commonly used in Nodejs, server-side).

Projects I've been handling are focused on Front-End, so I need a module compiler for client-side. Most browsers still does not support ES6 Module feature, that's why there are Client side JS module loaders available such as Browserify, Webpack, Rollup [ref](http://stackoverflow.com/questions/19059580/client-on-node-uncaught-referenceerror-require-is-not-defined)

I am still learning JavaScript modules but for simplicity, I'm going to use Browserify, Babel, and Gulp.

Below is a step-by-step scenario of how these tools are connected and how it transforms our ES6 code.

1. We write code using ES6 capabilities inclduing (but not limited to) ES6 module loading.
2. Babelify translates this code to ES5-compatibility code with `require` statements included.
3. ES5 code with `require` statements is transformed to the version that is fully understandable by browsers by Browserify

[ref](http://egorsmirnov.me/2015/05/25/browserify-babelify-and-es6.html)

Additional method....

- Gulp.js then compiles all dependencies and scripts and outputs the final (minified and compressed) javascript file.

A sample **Gulp.js** task should look like this:

```
var gulp = require('gulp');
var browserify = require('browserify');
var babelify = require('babelify');
var source = require('vinyl-source-stream');

gulp.task('build', function () {
  return browserify({entries: './app.jsx', extensions: ['.jsx'], debug: true})
  .transform(babelify)
  .bundle()
  .pipe(source('bundle.js'))
  .pipe(gulp.dest('dist'));
});
```

-----

**Side note**

I'm looking forward on taking advantage of what Babel plugins has to offer to replace Browserify and Babelify.

- [Babeljs.io](https://babeljs.io/)
- [Exploringjs.com](http://exploringjs.com/es6/ch_modules.html)

-----

**References:**

- [Client on node: Uncaught ReferenceError: require is not defined](http://stackoverflow.com/questions/19059580/client-on-node-uncaught-referenceerror-require-is-not-defined)
- [Browserify, Babelify and ES6](http://egorsmirnov.me/2015/05/25/browserify-babelify-and-es6.html)
- [Babeljs.io](https://babeljs.io/)
- [Exploringjs.com](http://exploringjs.com/es6/ch_modules.html)
- [ES6 Export Overwriting Function](http://stackoverflow.com/questions/32793404/es6-export-overwriting-function)
