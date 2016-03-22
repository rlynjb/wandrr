---
layout: post
title: "Fiddling with Phonegap's Speech Recognition"
date: 2016-03-16 12:38:53
tags:
- app development
---

Hello! Again this is a continuation of my previous blog posts. I am attempting to develop a simple app while blogging my experience and issues I've come across.

- [Beginning Mobile App Developmet Journey](/Beginning-mobile-app-development-journey)
- [Beginning Small Web App Development with AngularJS](/Beginning-Small-Web-App-Development-with-AngularJS)

From my recent blog post [Beginning Small Web App Development with AngularJS](/Beginning-Small-Web-App-Development-with-AngularJS), I was able to:

- Setup Zurb Foundation for Apps by creating a directory inside of my phonegap project instance.
- Use Zurb Foundation for Apps project directory for development.
- Transfer build files to phoengap's www directory for deployment.
- Designed and Developed a simple mobile layout and navigation using Zurb Foundation for Apps.
- Use AJAX to locally fetch a .json file and display data.

Now, I am extending my app by using Speech Recognition. A typical user scenario would be:

- App has option to use Voice Recognition or Simple Reload Button
- If User chose Voice Recogntion, app will enable phone's voice command sensor
- When User says 'shuffle', app will reload new data

-----

### Webviews, Browsers, and Hybrid App

While learning how to install and use PhoneGap plugins, I've come across terms which I think are essential to understanding the difference between Native Device Sensors/Features and HTML5 API and developing Hybrid Apps.

- [What is a Hybrid Mobile App](http://developer.telerik.com/featured/what-is-a-hybrid-mobile-app/)
- [What is a WebView](http://developer.telerik.com/featured/what-is-a-webview/)

-----

### Plugins and Documentations

Cordova provides a documentation for registered plugins [Cordova Official Documentation Plugins](http://cordova.apache.org/plugins/), but I was not able to find the plugin I needed. Instead, I've found the ff. on github and youtube:

<iframe width="560" height="315" src="https://www.youtube.com/embed/oXiel-iZOos" frameborder="0" allowfullscreen></iframe>
[Github.com: macdonst - Speech Recognition Plugin](https://github.com/macdonst/SpeechRecognitionPlugin)

Video pretty much explains how speech recognition works and discusses various speech recognition APIs available and its brief history. He also showcased sample code and its use cases.

- [HTML5 speech recognition in browser](http://shapeshed.com/html5-speech-recognition-api/)
- [W3C Community Group Final Report on HTML5 Speech Recognition API](https://dvcs.w3.org/hg/speech-api/raw-file/tip/speechapi.html)
