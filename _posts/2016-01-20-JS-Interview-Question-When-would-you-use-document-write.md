---
layout: post
title: "JS Interview Question: When would you use document.write()?"
date: 2016-01-20 10:47:13
tags:
- javascript
- interview question
---

### When would you use document.write()?

When document.write() is executed after page load, it replaces the entire header and body tag with the given parameter value in string. An invocation could look like this:

```
document.write(‘<h1>hello world</h1>’);
```

When working with web application, it is uncommon task to overwrite an entire page, hence why using document.write() is bad practice. It cannot inject string text into a given node point unlike jQuery library selectors and native JavaScript methods. Ref: https://developer.mozilla.org/en-US/docs/Web/API/Document

Another reason not to use document.write() is it doesn’t support XHTML, but its not an issue since most web development uses HTML. Since document.write() fires after a page has finish loading, it causes performance issues and sometimes, may not even fire at all.

The only seem appropriate usage for document.write() is when working third parties like Google Analytics and such for including their scripts. This is because document.write() is mostly available in any browser. Since third party companies have no control over the user’s browser dependencies (ex. jQuery), document.write() can be used as a fallback or a default method.
