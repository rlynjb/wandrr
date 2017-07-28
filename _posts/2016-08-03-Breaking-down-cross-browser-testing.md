---
layout: post
title: "Breaking down Cross-Browser Testing"
date: 2016-08-03 12:57:02
tags:
- testing
---

Below is my note on an article on smashing magazine. Article is mostly theory but I tried to take in the important info.

# Two Main Objectives

1. Discovering bugs
  * Entails trying to break your app to find bugs to fix.
2. Sanity-checking
  * Involves verifying that majority of your audience receives the expected experience.

-----

# Know your Statistics

- Audience statistics
- Browser usage statistics

### Simplify your browser usage statistics

**Desktop Browsers**

- we don't care about:
  * versions except IE
  * OS
- same argument applies with Portable Browsers
- new wave of browsers called: In-App browsers - browsers in social media platforms

**Portable Browsers**

- whats important:
  * version of the native Android browser used
  * version of iOS a device is running
    * very relevant as Safari versions are intrinsically linked to iOS

-----

# Three-Phase Attack

1. **Reconnaissance: Find Browser-Agnostic Bugs**
  * Try resizing to view responsiveness. Was there a funky breakpoint anywhere?
  * Zoom in and out. Have the background-positions of your image sprite been knocked askew?
  * See how the application behaves with Javascript turned off. Do you still get the core content?
  * See how the application looks with CSS turned off. Do the semantics of the markup still make sense?
  * Try turning both Javascript and CSS off. Are you getting an acceptable experience?
  * Try interacting with the application using only your keyboard. Is it possible to navigate and see all the content?
  * Try throttling your connection and see how quickly the application loads. How heavy is the page load?

2. **Raid: Test in High-Risk Browsers First**
  * Statistical Analysis of Bug Distribution
    * High-Risk are IE browsers
    * Medium-Rish are Safari, Opera
    * Low-Rish are Chrome, Firefox
  * Fixing bugs in bad browsers makes your code more resilient in good browsers
  * Identifying problematic browsers
    * [CanIUse](http://caniuse.com)
    * VirtualBox
  * Check on actual device or browser
  * Tools to rectify major compatibility issues:
    * [Modernizr](http://modernizr.com)

3. **Clearance: sanity checking**
  * By this stage, we should be 80:20
    * Figuratively, we've fixed 80% of the bugs after testing 20% of the browsers
    * Now, we verify the experience of 80% of audience through testing a different 20% of browsers
  * Prioritize the browsers
  * Use a 3rd-party service that checks on multiple browsers and device

-----

##### **References:**

- [High Impact, Minimal-Effort Cross-Browser Testing](https://www.smashingmagazine.com/2016/02/high-impact-minimal-effort-cross-browser-testing/)
