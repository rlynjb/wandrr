---
layout: post
title: "Beginning Mobile App Development Journey"
date: 2016-02-26 13:14:59
tags:
- mobile development
---

This blog post is just my notes on learning how to setup PhoneGap/Cordova locally, build and test via PhoneGap Build.
If you want to know more about its history and detailed instructions, refer to this book:

[Packtpub: PhoneGap Mobile Application Development Hotshot](https://www.packtpub.com/application-development/phonegap-3x-mobile-application-development-hotshot)
<br>
<img src="https://d1ldz4te4covpm.cloudfront.net/sites/default/files/imagecache/ppv4_main_book_cover/7925OS.jpg"/>

-----

I've been searching for a Mobile App Framework on which I can use languages I'm comfortable with (HTML, CSS, JavaScript) and also will be able to deploy on various devices utilizing native device sensors and functionalities.

I know performance will be an issue when using Mobile App Framework, but considering our project scope, it will not be an issue. Given the timeframe and number of developers, using Mobile App Framework sounds proper.

Here are also some resources [Mobile Frameworks Comparison Chart](http://mobile-frameworks-comparison-chart.com/) and frameworks we've considered that I think worth noting: [Appgyver](http://appgyver.com), [Cordova](https://cordova.apache.org/), [Phonegap](http://phonegap.com/)

### Why choose PhoneGap?

It's opensouce MIT license! and since Cordova powers PhoneGap, I might as well take advantage of the additional features that PhoneGap offers: PhoneGap Build!

-----

### Requirements and important initial step

- install node.js and configure platform SDKs (if not using PhoneGap Build)
- install PhoneGap
  - Adding the PhoneGap CLI enables the use of Adobe's remote building capabilities, which means you don't need to have the platform SDKs installed in order to build your app. (There are caveats here; it is best to refer to the PhoneGap Build website at http://build.phonegap.com for more information.) Installing PhoneGap CLI will also install Cordova CLI, since PhoneGap is powered by Cordova engine.
  - install via npm: `sudo npm install -g phonegap`
  - check if installed: `phonegap --version`
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

**To build your project for a specific platform**

`phonegap local build platform-name`

To build your project remotely using PhoneGap Build, you need to have an account on PhoneGap Build and have all the necessary certificates and provisioning files set up.

`phonegap remote build platform-name`

[https://build.phonegap.com/](https://build.phonegap.com/)

Building remotely using PhoneGap Build is a little different from building locally since you may not see the results of the build instantly; the service will build the code as soon as it has a chance. The only way to verify that things went as expected is to log on to your account at http://build.phonegap.com and verify the results.

-----

### deploy project to a simulator/device

Once we built a project, next is to **Test it**.
To do this, you can deploy the code to a simulator (which is handy for debugging on your machine) or deploy the code to a device (which is a must to get a feel for how the app performs on a real device). You can do both using either CLIs, depending upon what the platform SDK supports. (For example, some platform SDKs may only support deploying to a simulator.)

To deploy using the PhoneGap CLI, it's important to remember that this only works for local builds. If you built remotely, you need to navigate to http://build.phonegap.com and install from there.

`phonegap local install platform-name`
