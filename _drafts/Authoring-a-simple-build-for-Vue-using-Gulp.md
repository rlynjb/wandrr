---
layout: post
title: "Authoring a simple build for Vue.js"
date: 2017-09-03 09:25:55
tags:
- vuejs
- gulp
- build tool
- javascript
- js
---

1. run `npm init`
	- this is to start a `package.json` file
2. install dependencies, we will need the ff. dependencies install
	- build process
		- `gulp`, `gulp-concat`, `gulp-sass`
	- javascript
		- `browserify`, `babelify`, `babel-preset-env`
	- vue
		- `vueify`, `vue`, `vue-router`, `vue-resource`, `vuex`
	- css
		- `foundation-sites`
3. Now we write a simple `gulpfile.js`
