---
layout: post
title: "React.Js Projects Workflow"
date: 2017-06-22 14:12:02
tags:
- reactjs
- javascript
- js
---

#### Gist

- [Scaffold](#scaffold)
- [Destructuring the Layout](#destructing-the-layout)
- [Create a sample Database of products](#create-a-sample-database-of-products)

-----

# Scaffold

There are two ways we can start a React.js project.

1. Setup and build the script using a Build Tool.
  - Ex: Gulp, Webpack, NPM script
2. Use server-side to start a web server and build the script using Browserify, Babelify, and Express.

Since I am familiar with the build tools such as Gulp.js. Why not use something different, I'm going for #2 method in doing this project.

### Method

1. Create a repo and `git clone` to your local server
2. Run `npm init` and go through the process
3. `npm install --save` the following npm modules listed on the link below:
  - [webshop - package.json](https://github.com/rlynjb/webshop/commit/91c354d610f836b6c954e9412e05671e4839b2a0#diff-b9cfc7f2cdf78a7f4b91a753d10865a2)
4. Create the following directories: `mkdir public && mkdir source`
5. Create server file `touch server.js` to start webserver and code the script to transpile our React.js files
  - [webshop - server.js](https://github.com/rlynjb/webshop/commit/91c354d610f836b6c954e9412e05671e4839b2a0#diff-78c12f5adc1848d13b1c6f07055d996e)
6. Create your main file `touch source/app.jsx` thats linked to our `server.js` file
  - [webshop - source/app.jsx](https://github.com/rlynjb/webshop/commit/91c354d610f836b6c954e9412e05671e4839b2a0#diff-bcb4667827379fd27bf22df4d9dfeabc)
7. Last, `touch .gitignore` and add `node_modules, node_modules/*` to avoid pushing massive amount of file to our repo

-----

# Destructing the Layout

This is when we compartmentalize the layout structure of our React.js app. For this section, we will be using the following npm modules:

```
npm install --save react-bootstrap
npm install --save react-router-bootstrap
npm install --save react-router-dom
```

Create our `touch public/index.html` file and load our chosen CSS framework, polyfills, and necessary meta tags.

### Method

We will start by setting up the **Route** and **Layout of our app** which usually consist of Header, Menu, Main Contents, and Footer.

### 1. This is the initial setup of our **Routing System**. On `source/app.jsx` file

```
/*
  We are declaring use strict just for a javascript module security and debugging repercussion
*/
'use strict';

/*
  Next, we declare the methods from npm modules we need
*/
import React from 'react';
/*
  We will create this file next
*/
import Routes from './routes.jsx'; 
import render from 'react-dom';

/*
  We are rendering the Routes which will consist of our Layout and main contents as well and
  attaching it to an HTML element with id of container
*/
render(
  Routes,
  document.getElementById('container')
);
```

If you notice, we are compartmentalizing our code so it doesn't get cluttered in the long run. I know, its confusing at first, but its good to have a clean code for readability.

### 2. Next, create `touch source/routes.jsx` file

```
'use strict';

import React from 'react';
import Layout from './layout.jsx'; // the usual, we will create this file next
import { BrowserRouter, Route, Link } from 'react-router-dom';

const Routes = (
  <BrowserRouter>
    <Layout/>
  </BrowserRouter>
);

module.exports = Routes;
```

This file is where we actually define out Routing system by using `react-router-dom` instead of `reat-router`. While coding, there where version conflicts I came across, [react-router issue](https://github.com/ReactTraining/react-router/issues/4752#issuecomment-286556728).

As of React v4, we are to use `react-router-dom` instead of `react-router`.

[How to use react-router-dom module](https://medium.com/@pshrmn/a-simple-react-router-v4-tutorial-7f23ff27adf) explains difference bet. `<BrowserRouter>` and `<HashRouter>`, and which to use.

### 3. Create our `source/layout.jsx` file

```
'use strict';

import React from 'react';
// as discuss from prev step, there is a tutorial on how to use these methods
import { Switch, Route } from 'react-router-dom';

/*
  These are 2 main components of our layout.
  Names are pretty self-explanatory
*/
import Menu from './components/menu.jsx';
import Footer from './components/footer.jsx';

/*
  These are static pages
*/
import Home from './pages/home.jsx';
import Products from './pages/products.jsx';
import Company from './pages/company.jsx';

const Layout = React.createClass({
  render() {
    return (
      <div>
        <Menu />

        <main>
          <Switch>
            <Route exact path='/' component={ Home } name='home' />
            <Route path='/products' component={ Products } name='products' />
            <Route path='/company' component={ Company } name='company' />
          </Switch>
        </main>

        <Footer />
      </div>
    );
  }
});

module.exports = Layout;
```

The code above is pretty simple. I think theres not much to explain to it. Its pretty much a component of overall layout of our app. Which uses **Route** to **Switch** from different static page depending on which link the user clicks.

The component also loads our Menu and Footer and these stays displayed throughout the app.

-----

I guess from this point, its safe to stop going further into creating those other components (Pages, Components). We can probably create those on our own.

The Method above is to explain in detail on how we are able to destructure a layout, create its own component and what latest version of Routing system to use and how to use it.

-----

# Create a sample Database of products

Since we are using Express, we create a sample json object data, but I assume we can use any API endpoint products file.

### Method

- create a `products.json` data and store in `/public/`
  - each item has the ff. fields
    - SKU, price, savings, description, image, title
  - items are categorized by:
    - main offerings, sale offerings
- implement code to fetch data on `server.js` file

```
app.get('*.json', function (req, res) {
  res.sendFile(__dirname + "/public/" + req.path);
});
```

-----

#### References:

- [ReactJS Blueprints](https://www.packtpub.com/web-development/reactjs-blueprints)
