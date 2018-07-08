---
layout: post
title: "Setting up Fullstack Nodejs App Project with GraphQL, Firebase, and Quasar Framework"
date: 2018-06-23 22:01:43
tags:
- javascript
- js
- graphql
- vuejs
- quasar
- heroku
---

# Designing UI and UX of App

- Use AppCooker ipad app

-----

# Method for Setting Up Quasar Framework with GraphQL and Firebase

### Installing Quasar Framework

1. Go to [quasar-framework.org] and install Quasar via Starter Kit
  - ref: [Quasar Framework - Starter Kit](https://quasar-framework.org/guide/index.html#Starter-Kit-Recommended)
2. Install Vue CLI, `npm i -g vue-cli`
3. Install Quasar CLI, `npm i -g quasar-cli`
4. Create new project with Quasar, `quasar init pj-name`
5. Go to project folder and install dependencies, `npm i`
6. Run `quasar dev` to run local dev

### Prototyping the App

- [Quasar Framework](https://quasar-framework.org)
- [Vue.js](https://vuejs.org/)
- [Vue Router](https://router.vuejs.org/)
- [Vuex - State Management](https://vuex.vuejs.org/)

### Building App Ideas

- [Learn these JavaScript fundamentals and become a better developer](https://medium.freecodecamp.org/learn-these-javascript-fundamentals-and-become-a-better-developer-2a031a0dc9cf)
- [How To Build Vue Components Like A Pro](https://blog.bitsrc.io/how-to-build-vue-components-like-a-pro-fd89fd4d524d)

-----

### Installing GraphQL with Apollo Server on Heroku

1. Create a repo for server and git clone on your dev.
2. Follow guide below to setup Apollo Server and GraphQL
  - [Apollo Server v2](https://www.apollographql.com/docs/apollo-server/v2/getting-started.html)
3. Guide to deploy on Heroku
  - [Deploying with Heroku](https://www.apollographql.com/docs/apollo-server/v2/deployment/heroku.html)
4. Start server with npm command. Add `node index.js` on `package.json` file
  - [Default web process type](https://devcenter.heroku.com/articles/nodejs-support#default-web-process-type)
5. Debug port on Heroku. Since Heroku automatically sets a port to every deploy.
  - Set `process.env.PORT` on apollo server listen method `{port: process.env.PORT}`
  - [heroku deploy fail](https://stackoverflow.com/questions/14322989/first-heroku-deploy-failed-error-code-h10)
6. Debug GraphQL playground on Heroku
   - since playground is disabled on production and introspection mode, set `NODE_ENV` to `development`
   - [GraphQL Playground](https://www.apollographql.com/docs/apollo-server/v2/features/playground.html)

### Designing and working on Schema

1. Open heroku app on browser
2. Go through apollo documentation regarding schema design
  - [Schema Design - Apollo GraphQL](https://www.apollographql.com/docs/guides/schema-design.html)
  

-----

### Building the Server Ideas

- [Living APIs, and the Case for GraphQL](https://brandur.org/graphql)

-----

#### Other Resources:

- [GraphQL basics and practical examples with Vue](https://medium.com/@lachlanmiller_52885/graphql-basics-and-practical-examples-with-vue-6b649b9685e0)
