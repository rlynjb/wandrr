---
layout: post
title: "A Method to remove Bower and use NPM for all dependencies"
date: 2017-07-27 16:54:20
tags:
- javascript
---

This is just simple method I came up with when removing Bower since its deprecated. Alternative is NPM or Yarn.

1. Make sure to have a clean local repo
2. Copy and Paste packages from `bower.json` to `package.json`
3. Make sure to remove ^ carat symbol before a module version.
  - This is to maintain its original version everytime an `npm install` is ran
  - With the ^ carat symbol before a module version means it will automatically update the module to the latest version
  - Also, double check on npmjs.org of module is available and which version to use
4. Next is `rm bower.json` file
5. Remove existing node_modules directory if there is, `rm -rf node_modules`
6. Then run `sudo npm install`, pretty self-explanatory here
7. On `gulpfile.js`, replace all instances of `bower_components` to `node_modules`
8. Run `gulp` or `gulp watch`
  - if error occurs, fix it
9. Test the site/app/project
10. Obviously, fix errors lol
