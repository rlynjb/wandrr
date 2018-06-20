---
layout: post
title: "Understanding Unit Testing"
date: 2018-06-16 13:35:39
tags:
- javascript
- js
- unittesting
---

# Using Mocha webpack

I wanna understand testing and start utilizing it to become a beter developer. I am using Mocha, Chai with Webpack. There is a npm module to easily integrate Mocha with Webpack.
ref: [Mocha Webpack Doc](zinserjam.github.io/mocha-webpack)

Since, I am using Vuejs alot, we can also integrate Vue-Test-Utils with mocha webpack. Vue-test-util is an npm module that aids unit testing Vue Components with Mocha.
ref: [Vue Test Utils Doc](https://vue-test-utils.vuejs.org/en/guides/testing-SFCs-with-mocha-webpack)
* Note: is `mocha-webpack` command doesnt work. We can explicitly run node path to mocha-webpack by running `node ./node_modules/mocha-webpack/bin/mocha-webpack --version`.

Below are links for writing unit testing:

- [Mocha](https://mochajs.org)
- [Sinon.js](https://sinonjs.org)
- [Chaijs](http://www.chaijs.com/)

To understand Uniting Testing with Mock, Stubs, Spies, and  Test Doubles. Refer to link below:
- [Sinon Tutorial: JavaScript Testing with Mocks, Spies & Stubs](https://www.sitepoint.com/sinon-tutorial-javascript-testing-mocks-spies-stubs/)

After understanding the basis or foundation of Unit Testing. Understand the reasons why Unit Testing is an important tool to become a better developer.
ref:

- [Why I now appreciate testing, and why you should too.](https://medium.freecodecamp.org/why-i-now-appreciate-testing-and-why-you-should-too-74d48c67ab72)
- [Unit Testing Front End](https://medium.com/front-end-hacking/unit-testing-front-end-38b9bf1de079)

To understand other Front-End Testing methods:
- [Testing Your Frontend Code](https://hackernoon.com/testing-your-frontend-code-part-i-introduction-7e307eac4446)

To understand what is Front End Testing Pyramid:
- [The Frontend Test Pyramid: How to rethink your testing](https://medium.freecodecamp.org/the-front-end-test-pyramid-rethink-your-testing-3b343c2bca51)
- [The Practical Test Pyramid](https://martinfowler.com/articles/practical-test-pyramid.html)

To take Unit Testing a step further with Integration Testing
- [All you need to know about Integration Testing: SuperTest, Mocha, Chai](https://www.codementor.io/olatundegaruba/integration-testing-supertest-mocha-chai-6zbh6sefz)

-----

# Method for writing Unit Test (the basic)

1. Start with Unit Test and use Test Doubles to to replace 3rd party modules.
  - Isolate each function/class or unit of code.
  - Isolate any 3rd party modules by using mock, stub, spies (these are test doubles).
2. Open code file you want to test.
3. Open your test file.
4. Import file or function you want to test in your test file.
5. Reading the constructor or methods inside a javascript object.
  - Describe a method and add iits description inside a **mocha** `describe` handler.
  - Read the next line of code
  - Check if its an `if condition`, `return` or other logic.
  - Also check [Mochajs Doc](http://www.mochajs.com) for other features.
  - Add a description in **mocha** `it` handler of what it does.
  - Define **System Under Test** (SUT) is the imported javascript object/class.
6. Pass in value in imported javascript object/class or its method.
  - We can use an node module called [Chance.js](chancejs.com/index.html) to generate random values.
7. Check Chai docs for choices of assertions.
  - [Chai.js](www.chaijs.com/guide/styles/)
  - Chai contains expert, assert, should-style assertions
