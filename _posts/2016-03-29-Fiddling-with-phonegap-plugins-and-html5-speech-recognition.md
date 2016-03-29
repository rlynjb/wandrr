---
layout: post
title: "Fiddling with PhoneGap Plugins and HTML5 Speech Recognition"
date: 2016-03-29 09:42:14
tags:
- app development
---

Hello! Again this is a continuation of my previous blog posts. I am attempting to develop a simple app while blogging my experience and issues I've come across. Below are my previous blog post in order.

- [Beginning Mobile App Developmet Journey](/Beginning-mobile-app-development-journey)
- [Beginning Small Web App Development with AngularJS](/Beginning-Small-Web-App-Development-with-AngularJS)

Just a recap, from my recent blog post [Beginning Small Web App Development with AngularJS](/Beginning-Small-Web-App-Development-with-AngularJS), I was able to:

- Setup Zurb Foundation for Apps by creating a directory `www-dev` inside of my phonegap project instance.
- Use Zurb Foundation for Apps project directory for development.
- Modify `gulpfile.js` to dump `build` files on `www` directory.
- Renamed original `www` directory to `www-default` for a copy of original app files.
- Designed a simple mobile layout and navigation using Zurb Foundation for Apps.
- Learn and leverage Zurb Foundation for Apps AngularJS integration.
- Use AJAX to request data stored in a `.json` file locally.

My next goal is to extend my app by using Speech Recognition. A typical user scenario would be:

- App has option to use Voice Recognition or Simple Reload Button
- If User chose Voice Recogntion, app will enable phone's voice command sensor
- When User says _'shuffle'_, app will reload new data

-----

### WebViews, Browsers, and Hybrid App

While learning how to install and use PhoneGap plugins, I've come across terms which I think are essential to understanding how native device sensors works in Hybrid Apps and how we can levarage HTML5 technology.

- [What is a Hybrid Mobile App](http://developer.telerik.com/featured/what-is-a-hybrid-mobile-app/)
- [What is a WebView](http://developer.telerik.com/featured/what-is-a-webview/)

-----

### Discovering HTML5 Speech Recognition and Speech Synthesis

Cordova provides a documentation for registered plugins [Cordova Official Documentation Plugins](http://cordova.apache.org/plugins/), but since I'm using PhoneGap Build to build my app, its best to refer to its phonegap plugin page and find the plugin you wish to to use. I've also found the plugin's original Github repo and a Youtube video demonstrating Speech Recognition:

[Github.com: macdonst - Speech Recognition Plugin](https://github.com/macdonst/SpeechRecognitionPlugin)
<iframe width="560" height="315" src="https://www.youtube.com/embed/oXiel-iZOos" frameborder="0" allowfullscreen></iframe>

Video pretty much explains how speech recognition works and discusses various speech recognition APIs available and its brief history. He also showcased sample code and its use cases. His examples are based of off [W3C Community Group Final Report on HTML5 Speech Recognition API](https://dvcs.w3.org/hg/speech-api/raw-file/tip/speechapi.html).

It took me awhile to have Speech Recognition plugin worked on my app and device. It was a trial and error process, from installing a PhoneGap plugin, configuring the plugin, testing and debugging on actual device via PhoneGap Build.

**Process of getting Speech Recognition to work on actual device**

1. Understanding what happens to PhoneGap project config files when a PhoneGap plugin has been added.
  - This is crucial, there are various `config.xml` files located in `/platform` and `/plugins` directories.
  - When `phonegap plugin add <source>` is ran, PhoneGap automatically adds references to these `config.xml` files except for the `config.xml` file located on project's root directory.
  - In my case, I needed to add `<plugin name="com.aserputko.speech.speechrecognition" spec="0.1.0" source="pgb" />` to my `config.xml` file located in my root directory.
  - Also, important to note that some plugins require additional steps.
  - A good updated book I've come across is **Packt Publishing - PhoneGap 4 Mobile Application Development Cookbook**.
2. Added a plugin I've found on [https://build.phonegap.com/plugins](https://build.phonegap.com/plugins)
  - [Beginning Mobile App Development Journey: Manage Projects Plugins](/Beginning-mobile-app-development-journey/#manage-projects-plugins)
3. Added a sample Speech Recognition code from [W3C Community Group Final Report on HTML5 Speech Recognition API](https://dvcs.w3.org/hg/speech-api/raw-file/tip/speechapi.html) unto my `app.js` and `index.html` file.
4. Build my app via PhoneGap Build by running `phonegap remote build <platform>`
  - [Beginning Mobile App Development Journey: Building Our Project](/Beginning-mobile-app-development-journey/#building-our-project)
5. Once built, installed my app by scanning QR Code on my [https://build.phonegap.com/apps](https://build.phonegap.com/apps) dashboard page.
6. Once installed, debugged my app by using [PhoneGap Build's Remote Debugging Tools](http://docs.build.phonegap.com/en_US/debugging_remote_debugging_tools.md.html)
  - This is an awesome tool! hehe

> Steps 4 through 6 was an iterative trial and error process.<br>
> Debugging JavaScript objects inside of PhoneGap's Debug Console doesn't seem to display contents inside of that object. A workaround I've come across was to use my Chrome console to check `SpeechRecognition` object since HTML5 and the plugin uses the same API. A good article that delved inside HTML5 Speech Recognition object is [HTML5 Speech Recognition API](http://shapeshed.com/html5-speech-recognition-api/).

-----

### Writing Speech Recognition code to fit my App's functionality needs

After going through the process and successfully ran Speech Recognition on my phone, below are articles I find useful for exploring HTML5 Web Speech and Speech Synthesis API further.

- [Introduction to the Web Speech API](https://developers.google.com/web/updates/2013/01/Voice-Driven-Web-Apps-Introduction-to-the-Web-Speech-API)
- [Introduction to the Speech Synthesis API](https://developers.google.com/web/updates/2014/01/Web-apps-that-talk-Introduction-to-the-Speech-Synthesis-API)
- [TeamTreeHouse - Accepting Speech Input in HTML5 Forms](http://blog.teamtreehouse.com/accepting-speech-input-html5-forms)

My goals for this functionality are:

- On initial app load, Speech Recognition is disabled
- When user clicks on _"Speak"_ button, Speech Recognition is enabled throughout session
- When user says _"Shuffle"_, Speech Recognition detects keyword and reloads data
- Speech Recognition is enabled unless user clicks _"Speak"_ button again
