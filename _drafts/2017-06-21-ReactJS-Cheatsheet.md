---
layout: post
title: "ReactJS Cheatsheet"
date: 2017-06-21 09:30:02
tags:
- javascript
- js
- reactjs
---

### Gist

- [Component based](#component-based-component-specification)
  - [props](#props)
  - [states](#states)
  - [render](#render)
  - [statics](#statics)
  - [propTypes](#proptypes)
  - [displayName](#displayname)
- [Lifecycle Methods](#lifecycle-methods)
  - [componentDidMount](#componentdidmount)
  - [componentWillMount](#componentwillmount)
  - [shouldComponentUpdate](#shouldcomponentupdate)
  - [componentWillReceiveProps](#componentwillreceiveprops)
  - [componentWillUpdate](#componentwillupdate)
  - [componentDidUpdate](#componentdidupdate)
  - [componentWillUnmount](#componentwillunmount)
- [The Virtual DOM](#the-virtual-dom)
- [Synthetic Event Handlers](#synthetic-event-handlers)
- [Code Sample Explained](#code-sample-explained)
- [9 things every React.js beginner should know](https://camjackson.net/post/9-things-every-reactjs-beginner-should-know)

-----

# Component based (Component Specification)
  
- contains or has built-in set of methods and properties.
- purpose of these methods and properties are:
  - debugging (`displayName`, `propTypes`)
  - setting initial data (`getInitialState`, `getDefaultProps`)
  - component lifecycle (`componentDidMount`, `componentShouldUpdate`, more..)
- the `render` method (from React DOM) is the only required method in a component.


-----

# Props and States

### props

- data coming from outside of component.
- its better to rely on data outside of component for testability and immutability concerns.
- cannot be modified, should be treated as immutable.
- props data can be access using `this.props`
- `getDefaultProps` is used to set initial props and use them in later point in the components' lifecycle.

```
getDefaultProps() {
  return {
    greeting: ""
  }
}
```

### states

- data is instantiated inside of component.
- variables that are available within the component.
- state data can be access using `this.state`
- its only used when you make changes to variables within the component.

```
getInitialState: function() {
  return {
    random_number: ()
  }
},
componentDidMount() {
  setInterval( () => {
    this.setState({
      random_number: Math.random()*100;
    });
  }, 1000);
},
render() {
  return (
    <div>{ this.state.random_number }</div>
  );
}
```

### render

- only required method in a component
- return JSX structure
- it can also return `null` or `false` to indicate we don't need to use it.

### statics

- use to define static methods
- they don't have access to `props` or `states` within the component.

```
import React from 'react';

const App = React.createClass({
  statics: {
    myMethod: (foo) => {
      return foo = "bar";
    }
  },
  render() {
    return null;
  }
});

console.log( App.myMethod('bar') ); // true
```

### propTypes

- validates your props passed unto your component
- shows up in your `console.log` if the props passed
- optional help tool while you develop your app
- it can validate complex data

### displayName

- set automatically if not set explicitly
- use for debugging purposes


-----

# Lifecycle Methods

- set of functions that are empty and you can override in your component.
- initially, all are empty except for `shouldComponentUpdate` is set to true.

<br>

### componentDidMount

**Executed after the component is mounted**

- most common method
- functions run after the component has been rendered for the first time.

**PROS**

- have access to current contents of props and states
- never run `setState` as it triggers endless loops

**CONS**

- this will not run in server-side, use `componentWillMount` instead

```
componentDidMount() {
  // Executed after the component is mounted
}
```

<br>

### componentWillMount

- method will be executed before the component is rendered for the first time.

**PROS**

- have access to component's current state and props
- safe to run `setState`
- executed on both server-side and client-side

```
componentWillMount() {
  // Executed before the component is mounted
}
```

<br>

### shouldComponentUpdate

- invoked whenever the component receives new props or state changes
- returns true by default

**PROS**

- useful if you create a component that updates only if certain condition is met or should never be updated at all 
- speed increases when set to false

**CONS**

- can lead to bug when careless use
- can be hard to track down

<br>

### componentWillReceiveProps

- compare props before render method runs
- let you compare incoming props
- can be used as an opportunity to react to prop transition before the render method is called
- invoke this method `componentWillReceiveProps(object nextProps)` to access incoming props
- this will not execute on initial render

**CONS**

- not good for `setState` insteas use `componentWillUpdate``

```
componentWillReceiveProps(nextProps) {
  // you can compare nextProps with this.props
  // and optionally set a new state or execute functions
  // based on the new props
}
```

<br>

### componentWillUpdate

- execute before rendering once new props or states are received
- when the component receives new props or states
- this method is executed before the rendering but not the initial render
- invoke this method `componentWillUpdate(object nextProps, object nextState)` to access incoming props and states

**PROS**

- use `componentWillReceiveProps` instead

**CONS**

- can evaluate new state but `setState` will trigger and endless loop

```
componentWillUpdate (nextProps) {
  // you can compare nextProps with this.props
  // or nextState with this.state
}
```

<br>

### componentDidUpdate

- executed whenever the component receives new props or states
- and render method has been executed

```
componentDidUpdate() {
  // Execute functions after the component has been updated
}
```

### componentWillUnmount

- invoked before the component is unmounted from DOM
- useful if you need to clean up memory or invalidate timer

```
componentWillUnmount() {
  // Execute functions before the component is unmounted
  // from the DOM
}
```

-----

# The Virtual DOM

### The DOM

- its very forgiving
- you can write invalid HTML and still get the result you want
- ReactJS, JSX is not forgiving
- JSX is strict and it requires a match with opening and closing tag

### The Virtual DOM

- a simpler implementation of the real DOM
- doesn't work directly with the DOM
- it maintains a smaller and more simplified internal set of elements
- enables you to switch parts of your visible elements without affecting other elements
- **cannot make changes directly** like jQuery or `getElementById()` native JavaScript
- instead, **attach a reference** named `refs` to the elements to target
   - can be done by `ref="myReference"` to your element
   - w/ ex. above, reference is now available through `React.findDOMNode( this.refs.myReference )`

-----

# Synthetic Event Handlers

- event handlers in ReactJS are passed an instance of **Synthetic Event** instead of the native event handlers
- has the same interface as native event handlers **except** it's cross-browser compatible
- events are triggered in a **bubbling phase** ref [Describe event bubbling](/JS-Interview-Question-Describe-event-bubbling)
- to capture an event immediately
  - ex: for `onClick` use `onCickCapture`
- to stop propagation
  - `event.stopPropagation()` or `event.preventDefault()`
- ref: [for complete list of events](https://facebook.github.io/react/docs/events.html)

-----

# Code Sample Explained

<iframe height='800' scrolling='no' title='learning reactjs' src='//codepen.io/rlynjb/embed/QgEdLN/?height=300&theme-id=20698&default-tab=js&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='https://codepen.io/rlynjb/pen/QgEdLN/'>learning reactjs</a> by rlynjb (<a href='https://codepen.io/rlynjb'>@rlynjb</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

This example is slightly contrived. It could be shortened quite a bit, and storing props as states is generally something you should avoid, unless you have a very good reason for doing so. In my experience, working with a local state is the single most bug-prone code you will encounter and the hardest code to write tests for.

- per ReactJS Bluepriint book

-----

#### References:

- [ReactJS Blueprints](https://www.packtpub.com/web-development/reactjs-blueprints)
