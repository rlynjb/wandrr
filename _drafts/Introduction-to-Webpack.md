---
layout: post
title: "Introduction to Webpack"
date: 2017-05-11 09:25:55
tags:
- webpack
- javascript
- js
---

# Practical hands-on of Webpack

I am going to optimize my `gulp.js` file from my Front End Flow theme using Webpack. Following this [article](https://hackernoon.com/a-map-to-modern-javascript-development-2017-16d9eb86309c), it gave me more overview of the tools I missed these past months.

My current FEF theme uses:

- Package Management
  * NPM
- Bundling
  * Gulp.js
- JavaScript
  * ES6
- Transpiling
  * Babel and Browserify
- Linting
  * None
- Testing
  * None
- UI Framework/State management
  * React (but not indepth)
- DOM Manipulation and animations
  * jQuery (trying to stay way from it)
- Styling
  * SASS
- CSS Framework
  * Zurb Foundation
- Assets
  * Google Fonts

I know JavaScript tools are overwhelming but if we were to segregate each discipline like the list above, I think it can give us a better understanding so we can set up each tools base on their discipline.

I am going to minimize my FEF theme workflow with the following JS tools and add new features as well:

- Package Management
  * NPM, will take advantage of script `npm run start` or `npm run webpack`
- Bundling
  * Webpack
- JavaScript
  * ES6
- Transpiling
  * Babel
- Linting
  * ESLint
- Testing
  * mocha (test runner), chai (assertion library) and chai-spies (for spies, fake objects that you can query for certain events that should or shouldn’t have happened)
- UI Framework/State management
  * React and Vue.js
- DOM Manipulation and animations
  * Plain ES6 and jQuery (but will not be prioritized)
- Styling
  * SASS
- CSS Framework
  * Zurb Foundation (might need to check if supported with React or can play well with Vue.js)
- Assets
  * Google Fonts


-----


## Configuring Webpack the easy way.

There are reasons why Webpack has been popular lately and its been accepted over other module bundlers. [ref: Why Webpack](https://www.smashingmagazine.com/2017/02/a-detailed-introduction-to-webpack/)

First off, lets configure Webpack the easy way. Reason for me to include this method is what if I wanted to use NPM and Webpack immediately to compile JavaScript files with ES6 features without setting up a config file. So for this method, I am going to use NPM scripts to run webpack.

I assume you already have NPM installed and have created a `package.json` file by running `npm init`

1. Install Webpack via NPM locally `npm install --save-dev webpack`
2. Install Lodash as our sample dependency `npm install --save lodash`
3. Create `main.js` file as our entry file. We will import lodash on this file.

```
var map = require('lodash/map');

function square(n) {
      return n*n;
}

console.log(map([1,2,3,4,5,6], square));
```

Here, we are just using lodash to square off the numbers inside its map function. Notice the `require` function is NOT supported by browsers yet, that is why we need to use Webpack to bundle this script.

We will use *Webpack Command Line* for this simple example.

Inside our `package.json` file, add the ff. code:

```
"scripts": {
  "build": "webpack src/main.js dist/bundle.js",
}
```

Now when we run `npm run build`, this will bundle `main.js` file (along with the imported NPM modules) and out put it as `bundle.js` file.




-----

#### References:

- [A Map to Modern JavaScript Development 2017](https://hackernoon.com/a-map-to-modern-javascript-development-2017-16d9eb86309c)
- [Webpack: A Detailed Introduction](https://www.smashingmagazine.com/2017/02/a-detailed-introduction-to-webpack/)
