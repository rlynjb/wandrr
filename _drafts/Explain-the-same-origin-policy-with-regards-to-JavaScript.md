---
layout: post
title: "Explain the same-origin policy with regards to JavaScript"
date: 2016-05-03 14:14:59
tags:
- javascript interview questions
---

Same-origin policy restricts scripts from other websites to be executed on your website. It is an important security measure as it isolates known malicious attacks such as Cross Site Scripting.

In two pages with url, an **origin** is defined if its **protocol**, **host**, and **port** are the same for both pages.

An example via [MDN - Same-origin policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy):
<br>
Compare `http://store.company.com/dir/page.html` to the table below.

URL | Outcome | Reason
--- | --- | ---
`http://store.company.com/dir2/other.html` | Success | -
`http://store.company.com/dir/inner/another.html` | Success | -
`https://store.company.com/secure.html` | Failure | Different protocol
`http://store.company.com:81/dir/etc.html` | Failure | Different port
`http://news.company.com/dir/other.html` | Failure | Different host


-----

##### **References:**

- [MDN - Same-origin policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy)
- [Same-origin Policy in layman terms](http://stackoverflow.com/questions/11474336/same-origin-policy-in-layman-terms)
