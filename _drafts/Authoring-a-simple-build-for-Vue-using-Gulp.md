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

My purpose for this blog post is to build a POS system (Point of sales). While demonstrating my process of building one.

-----

# My method of authoring a buld script file

1. run `npm init`
	- this is to start a `package.json` file
2. install dependencies, we will need the ff. dependencies install
	- server
		- `json-server`
	- build process
		- `gulp`, `gulp-concat`, `gulp-sass`
	- javascript
		- `browserify`, `babelify`, `babel-preset-env`
	- vue
		- `vueify`, `vue`, `vue-router`, `vue-resource`, `vuex`
	- css
		- `foundation-sites`
3. create the directories
	- `css/`
	- `js/`
	- `public/`
	- `views/`
	- `images/`
	- `fonts/`
4. Now we write a simple `gulpfile.js`
	- start with foundation-sites sass files
	- inside `css/` directory, create the following files
		- `custom.scss`
			- these file will overwrite any styles from foundations
		- `foundation-includes.scss`
			- contains all sass components from foundation. you can also add new ones from if you have mixins and such
		- `foundation-settings.scss`
			- contains settings, variables, from foundation
