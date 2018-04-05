---
layout: post
title: "Mapping it out"
date: 2017-12-11 09:25:55
tags:
- javascript
- js
---

Modified at: Apr 5 2018

### Overview

- Idea behind the app
- Breaking down the idea
- Coding
- Unit Testing
- Consuming API
- User Authentication for JWT in Vue.js
- Architecting/Designing the Front-End
  - Setting up Quasar framework on Digital Ocean and Nginx for development
- Architecting/Designing the Back-End
- Wrapping Up
- Setting Goals

-----

## Idea behind the app

There are alot of applications we can build. Apps that can be use internally within a company or apps to engage public users.

We can also utilize technology such as VR and AR to accomodate and Voice or Keyboard commands to navigate these apps.

These are the gist of different apps and hopefully it inspires us enough to get an idea for an app.

-----

## Breaking down the idea

Figure out the basic functionality of an app

- Outline the features and determine its input and output values
- Algorithms
  - There are many algorithms thats already been solved, but you can create your own
- The UX
  - Brainstorm how will the app work. Its user experience mostly. What will the users gain.
  - Tools that can be used are: Notepad & Pen!, [Draw.io](http://draw.io)

-----

## Coding

- Topics I've learned when coding are:
  - using ES6 map/filter
  - Lodash
  - Mapping arrays
  - Error handling
    - Bailout error handling
  - Arrow functions and scoping
    - avoid using `const $this = this`
    - arrow functions already takes in the scope of its parent scope/function
  - When coding, consider readability
- also checkout Vuejs Style guide

-----

## Unit Testing

For Vue.js, use `@vue/test-utils` and mocha-webpack

- [Installation and Setup](http://zinserjan.github.io/mocha-webpack/docs/installation/setup.html)
- [Testing SFCs with mocha-webpack](https://vue-test-utils-vuejs.org/en/guies/testing-SFCs-with-mocha-webpack.html)
- [vue-test-utils mocha-webpack example](https://github.com/vuejs/vue-test-utils-mocha-webpack-example)
- [Five traps to avoid while unit testing vuejs](https://engineering.doximity.com/articles/five-traps-to-avoid-while-unit-testing-vue-js)

NOTE: with Environment variables, we can probably implement mock or fake

- [Testing vue web application with vuex data store and rest backend](https://www.cypress.io/blog/2017/11/28/testing-vue-web-application-with-vuex-data-store-and-rest-backend)


-----

## Consuming API

For Restful API:

- Promises, Async
  - learned how to implement Services and how we should separate api calls.
  - Use Vuex to share states, actions, mutations, and other global helpers
  - learened the difference between Promise and Async
- Proper way to read and use API
  - Use or learn Hypermedia API
    - My interpretation for this is more like **self-documenting** api
  - [On choosing a hypermedia format](https://sookocheff.com/post/api/on-choosing-a-hypermedia-format)
  - [Building an api for longevity spec driven development](https://www.nginx.com/blog/building-api-for-longevity-spec-driven-development)
  - [What is HATEOUS](https://www.recaffeinate.com/post/what-is-hateous)
- This is actually my first time realizing what Hypermedia are and its purpose, but I still have a few questions about it.
  - We will heavily rely on its API
  - What if we want to change APIs? or its contents
  - Still learning about proper API comsumption

Alternative to Restful consumption is:

- Another method to consume API is using GraphQL to write Schema and its Resolver.
  - For Schema and Resolver doc, refer to [http://graphql.com](http://graphql.com)
  - and [GraphQL tools - Connectors](https://apollographql.com/docs/graphql-tools/connectors.html)
  - NOTE: questions to ponder
    - How do we map third-party Rest API data to our new Schema
      - Restructure data from third-party API data
      - Retrieve data we only need
    - Just a theory: this is probably implemented in the Resolver part
- When integrating GraphQL schema to our Front-End app
  - Best practice is to use a GraphQL client library for your chosen JavaScript framework.
  - For Vue.js, its `vue-apollo` client

**Free public API**

- data.gov
- Google Places API

-----

## User Authentication for JWT in Vue.js

- coming soon

-----

## Architecting/Designing the Front-End

- link to Vue.js communication pattern blog post
- frameworks I work with and learned:
  - Vue.js, Vuex, Vue-router, vee-validate, vue-loader
  - to avoid UX design problems, use Quasar
  - checkout Delving into Software development blog post
- I've learned to use and be comfortable with the technology above
- Use Vuex to share States, Actions, etc.
- but use **Props, Emit Event** when converting a component into a reusable one that can be used to a different project.
- besides passing props as data attribute, we can also pass it through router.
  - ref: [Passing Props](https://router.vuejs.org/en/essentials/passing-props.html)
- setup Event hub to share events in components
- reusable Components relates to MVVM design pattern (Model, View, View-Model)
- **Large Scale Application Architecture**
  - all desc below are still in theory
  - use git submodule
    - ref: [https://github.com/blog/2014-working-with-submodules](https://github.com/blog/2014-working-with-submodules)
  - use nested Vue instances
    - ref: [https://stackoverflow.com/questions/44990583/nested-vue-instances](https://stackoverflow.com/questions/44990583/nested-vue-instances)
  - consider Vuex modules
    - ref: [https://vuex.vuejs.org/en/modules.html](https://vuex.vuejs.org/en/modules.html)


### Setting up Quasar framework on Digital Ocean and Nginx for development

- log into digitalocean and create a droplet with specs of
  - Ubuntu 16, Node app
- log into your new droplet
- install Nginx
  - [How to install nginx on ubuntu 16](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-16-04)
- ff [How To Set Up a Node.js Application for Production on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-16-04)
- ff install guide of quasar
  [Quasar install guide](http://quasar-framework.org/guide/)

-----

## Architecting/Designing the Back-End

- Firebase with Google Cloud and GraphQL
- Laravel
- GraphQL with Apollo Server and Express
  - [Quick start to GraphQL with Apollo Server and Express](https://www.apollographql.com/docs/apollo-server/example.html)

-----

## Wrapping Up
- Use environment variables
  - ref: [https://forum.vuejs.org/t/use-environment-variable/12574/4](https://forum.vuejs.org/t/use-environment-variable/12574/4)
- Use webpack config utils
  - ref: [https://www.npmjs.com/package/webpack-config-utils](https://www.npmjs.com/package/webpack-config-utils)

-----

## Setting Goals

Its always good to set goals. Goals are what usually drives us to keep learning and improve on our craft.

For mine, it would be:

To extend Quasar framework. Additional features would include:

- Unit Testing
- GraphQL schema and resolver
- GraphQL server with Apollo

-----

#### References:

- [A Map to Modern JavaScript Development 2017](https://hackernoon.com/a-map-to-modern-javascript-development-2017-16d9eb86309c)
- [Webpack: A Detailed Introduction](https://www.smashingmagazine.com/2017/02/a-detailed-introduction-to-webpack/)
