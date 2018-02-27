---
layout: post
title: "Mapping it out"
date: 2017-12-11 09:25:55
tags:
- javascript
- js
---

## Idea behind the app
- pen and paper first is always a brain refresher.

## Breaking down the idea
- Algorithms
  - There are many algorithms thats already been solved, but you can create your own
- The UX
  - Brainstorm how will the app work. Its user experience mostly. What will the users gain.
  - Tools that can be used are: Notepad & Pen!, [Draw.io](http://draw.io)

## Coding
- Topics I've learned when coding are:
  - using ES6 map/filter
  - Lodash
  - Mapping arrays
  - Error hadnling
    - Bailout error handling
  - Arrow functions and scoping
    - avoid using `const $this = this`
    - arrow functions already takes in the scope of its parent scope/function
  - When coding, consider readability
- Mozilla doc for error handling
  - ref: [Control flow and Error handling](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- also checkout Vuejs Style guide

## Consuming API
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
  - Still learning about API comsumptions
- Free public API
  - ref: data.gov and more


## User Authentication for JWT in Vue.js
- coming soon


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

### Setting up Quasar app with Digital Ocean and Nginx
- log into digitalocean and create a droplet with specs of
  - Ubuntu 16, Node app
- log into your new droplet
- install Nginx
  - [How to install nginx on ubuntu 16](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-16-04)
- ff [How To Set Up a Node.js Application for Production on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-16-04)
- ff install guide of quasar
  [Quasar install guide](http://quasar-framework.org/guide/)

## Architecting/Designing the Back-End
- checkout Nuxt.js
- Google maps/places API
- Google Cloud Platform
  - mobile app backend as a service
  - Firebase
- Google App Engine Nodejs. flexible environment documentation
- Feather.js
  - API Framework


## Wrapping Up
- Use environment variables
  - ref: [https://forum.vuejs.org/t/use-environment-variable/12574/4](https://forum.vuejs.org/t/use-environment-variable/12574/4)
- Use webpack config utils
  - ref: [https://www.npmjs.com/package/webpack-config-utils](https://www.npmjs.com/package/webpack-config-utils)

-----

## Setting Goals

- To learn more or improve on architecting the structure of app.
- To master tools we use, Quasar and Vue.js
- Set a method in building an App
  - Work on UI/UX first
  - implement API
  - use `json-server` to structure sample data and hit endpoints
- Main goal is to improve on UI/UX of form fields and validation
  - use Quasar since it already has pre-made components of form fields
- [Javascript Design Patterns](https://seesparkbox.com/foundry/javascript_design_patterns)
- Book [Vue.js Design Patterns and Best Practices](https://www.packtpub.com/web-development/vuejs-design-patterns-and-best-practices)
- [vuejsdevelopers.com](vuejsdevelopers.com)
- [laravel-vuejs.com](laravel-vuejs.com)
- AR.js with vue.js
- another extra read is [addyosmani.com/largescalejavascript](addyosmani.com/largescalejavascript)

-----

#### References:

- [A Map to Modern JavaScript Development 2017](https://hackernoon.com/a-map-to-modern-javascript-development-2017-16d9eb86309c)
- [Webpack: A Detailed Introduction](https://www.smashingmagazine.com/2017/02/a-detailed-introduction-to-webpack/)
