---
layout: post
title: "A Sample Vue.js Communication Pattern"
date: 2017-09-03 20:18:14
tags:
- vuejs
---

I've been learning alot about Vue.js and just grasping the concept of how components communicate. One of the hurdles I cam across when developing in Vue.js is when I would do a simple jQuery click event with class swapping of active or inactive.

In Vue.js, this is done complete different. A sample code below is just an outline of how some of Vue.js objects are used in components for them to interact.

Another good reference is: [Vue.js Component Communication Pattern](https://alligator.io/vuejs/component-communication/)

The code below kinda gave me an Aha moment with Vue.js. Hopefully this will help you too to think in components rather than in jQuery.

```
child = {
	template: '#child-template',
	data: function () {
	},
	props: ['index', 'key'],
	computed: {
		isActive: function() {
			return this.$parent.activeIndex == this.index
		}
	},
	methods: {
		handleClick: function () {
			this.$emit('childSelected', index)
		}
	}
}

parent = {
	template: '#parent-template',
	data: function() {
		activeIndex: 0
	},
	components: {
		child: child
	},
	methods: {
		updateSelectedChild: function(selectedChildIndex) {
			this.activeIndex = selectedChildIndex
		}
	}
}

// on template
:class="{ active: isActive }"
@childSelected="updateSelectedChild"
```
