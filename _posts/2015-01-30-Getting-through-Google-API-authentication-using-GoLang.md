---
layout: post
title: "Getting through Google APIs’ authentication using GoLang"
date: 2015-01-30 10:47:13
tags:
- api
- authentication
---

Trying to get data from Google Analytics was tough, and I’m not just talking about Analytics, this includes any Google products.
You have to go through its authentication which uses OAuth2 and do research on its Documentation.
I do not have enough experience with server side scripting and authentication. This is probably why I had a hard time going through security. But with patience, patience, more patience, and one day, I just got it. (yes this kinda sounds like Tron.. ehe)
Working with Google API documentation using GoLang taught me to interact with other developers (ask for help) via Twitter, Github, Google Forums/Gmail and I’m surprise by how the community has responded quick especially its maintainers.

Below is a list of communication tools I found useful:
Github
Twitter
Google Forums
StackOverflow
and more, which ever you come across
Also, before starting to code, I atleast took some time to understand the following concepts and gather required credentials:

Cryptography (related with OAuth, atleast know the basics)
Learning how to read various API Documentation (I’ve worked with other APIs but Google was the hardest one)
Required API Credentials (in my case, Google credentials)
Reading material I found useful:
https://developers.google.com/accounts/docs/GettingStarted

Code gist
I’ve left comments on this code as a guide on where to get credentials and links that explains Service Account oauth flow and how the code works.
https://gist.github.com/rlynjb/a82a42e58ab0e7358861
