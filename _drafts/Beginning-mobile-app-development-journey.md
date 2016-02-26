---
layout: post
title: "Beginning Mobile App Development Journey"
date: 2015-02-25 13:31:14
tags:
- mobile development
---

I decided to play aorund with Phonegap CLI which is powered with Cordova engine as well.

I will cover the necessary steps to develop apps with PhoneGap.
We can develop apps using either PhoneGap CLI or PhoneGap Desktop app.
For emulating your app, we can either install and configure SDKs or use PhoneGap Build.

-----

### Requirements and important initial step

- install node.js and configure platform SDKs (if not using PhoneGap Build)
- install PhoneGap
  - Adding the PhoneGap CLI enables the use of Adobe's remote building capabilities, which means you don't need to have the platform SDKs installed in order to build your app. (There are caveats here; it is best to refer to the PhoneGap Build website at http://build.phonegap.com for more information.) Installing PhoneGap CLI will also install Cordova CLI, since PhoneGap is powered by Cordova engine.

- create first project
  - contains:
    - our code
    - other platform-specific code
    - other assets required to generate an app ready for you to run on a simulator or device
- manage project's platforms
- manage project's plugins
- build my project
- deploy project to the simulator/device

When testing our app on a simulator, we either need to install platform SDKs if we where to test it locally.
To avoid installing and configuring such SDKs, we can rely on PhoneGap Build for this simulating on different OS (Android, iOS, Blackberry, Windows) https://build.phonegap.com

But a Mac is required to generate the certificates necessary for iOS app signing (even with PhoneGap Build) and is definitely required for deployment to the App Store. The same is true for Windows; you need to deploy to the App Store from Windows only.

-----

### Create first project

to create a project with PhoneGap CLI

run: `phonegap create ./PGHelloWorld com.phonegaphotshot.pghelloworld PGHelloWorld`

the first parameter indicates that a project should be created in a directory specified by the second parameter. The third parameter is the project ID, which must be unique and should be specified in reverse domain-name order. The final parameter is the name of the project.

-----

### manage project's platforms

in this step, we will specify the platforms that the projects support. besides adding platforms, we can also remove, update, and list out the supported platforms.

**to add platform**

`cordova platform add platform-name`

- ios: The iOS platform
- android: The Android platform
- blackberry10: The BlackBerry 10 OS platform
- firefoxos: The Firefox OS platform
- wp7: The Windows Phone 7 platform
- wp8: The Windows Phone 8 platform
- windows 8: The Windows 8 platform

**listing the available platforms**

`cordova platform ls`

**removing platforms**

`cordova platform remove platform-name`

**updating platforms**

`cordova platform update platform-name`

-----

### manage project's plugins

Plugins are the mechanism Cordova uses to provide native functionality to your app. 
Plugins can be managed using either the Cordova CLI or the PhoneGap CLI (which ends up using the Cordova CLI in the background). The important detail to remember when you use the PhoneGap CLI is that plugins must be installed locally (not remotely).

**installing plugins**

`phonegap local plugin add plugin-name`

http://cordova.apache.org/docs/en/dev/cordova/plugins/pluginapis.html#Plugin%20APIsZ

- phonegap local plugin add org.apache.cordova.device
- phonegap local plugin add org.apache.cordova.network-information 
- phonegap local plugin add org.apache.cordova.battery-status
- phonegap local plugin add org.apache.cordova.device-motion
- phonegap local plugin add org.apache.cordova.device-orientation 
- phonegap local plugin add org.apache.cordova.geolocation 
- phonegap local plugin add org.apache.cordova.camera 
- phonegap local plugin add org.apache.cordova.media 
- phonegap local plugin add org.apache.cordova.media-capture 
- phonegap local plugin add org.apache.cordova.file 
- phonegap local plugin add org.apache.cordova.file-transfer 
- phonegap local plugin add org.apache.cordova.dialogs 
- phonegap local plugin add org.apache.cordova.vibration 
- phonegap local plugin add org.apache.cordova.contacts 
- phonegap local plugin add org.apache.cordova.globalization 
- phonegap local plugin add org.apache.cordova.splashscreen 
- phonegap local plugin add org.apache.cordova.inappbrowser 
- phonegap local plugin add org.apache.cordova.console

**listing plugins**

`phonegap local plugin list`

**removing plugins**

`phonegap local plugin remove plugin-name`

-----

### building our project

Building involves compiling all the native code using the platform SDKs on your machine and then packaging your HTML, JavaScript, and CSS (and any assets) with this code so that it can be deployed to a simulator or device.


