---
layout: post
title: "Difference between document load event and document ready event?"
date: 2016-02-23 15:08:26
tags:
- javascript interview questions
---

`window.onload` event fires only when contents (images, css, scripts, other 3rd party sources), including the DOM has finished loading.

`$(document).ready()` event fires when the HTML DOM has finished loading. It also fires earlier than `window.onload`. It will not wait for contents to load.


-----

##### **References:**

- [window.onload vs $(document).ready()](http://stackoverflow.com/questions/3698200/window-onload-vs-document-ready)
