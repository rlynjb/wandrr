---
layout: post
title: "Setting up Fullstack Nodejs App Project with GraphQL, Firebase, and Quasar Framework"
date: 2018-06-23 22:01:43
tags:
- javascript
- js
- graphql
- firebase
- vuejs
- quasar
---

### Method for Setting Up Quasar Framework with GraphQL and Firebase

# Installing Quasar Framework

1. Go to [quasar-framework.org] and install Quasar via Starter Kit
  - ref: [Quasar Framework - Starter Kit](https://quasar-framework.org/guide/index.html#Starter-Kit-Recommended)
2. Install Vue CLI, `npm i -g vue-cli`
3. Install Quasar CLI, `npm i -g quasar-cli`
4. Create new project with Quasar, `quasar init pj-name`
5. Go to project folder and install dependencies, `npm i`
6. Run `quasar dev` to run local dev

# Installing GraphQL

1. Run `mkdir server && touch server/index.js` to create folder and index file
2. Install dependencies, `npm i --save express express-graphql graphql`
  - ref: [GraphQL - Running an Express GraphQL Server](https://graphql.github.io/graphql-js/running-an-express-graphql-server)

-----

#### Other Resources:

- [GraphQL basics and practical examples with Vue](https://medium.com/@lachlanmiller_52885/graphql-basics-and-practical-examples-with-vue-6b649b9685e0)
