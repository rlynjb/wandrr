---
layout: post
title: "Beginning Mobile App Development Journey"
date: 2016-02-26 13:14:59
tags:
- app development
---

Consider this blog post as my notes on learning how to setup PhoneGap/Cordova locally, build and test via PhoneGap Build.
If you want to know more about its history and detailed instructions, refer to this book:

[Packtpub: PhoneGap Mobile Application Development Hotshot](https://www.packtpub.com/application-development/phonegap-3x-mobile-application-development-hotshot)
<br>
<img src="https://d1ldz4te4covpm.cloudfront.net/sites/default/files/imagecache/ppv4_main_book_cover/7925OS.jpg"/>

-----

I've been searching for a Mobile App Framework on which I can use languages I'm comfortable with (HTML, CSS, JavaScript) and also will be able to deploy on various devices utilizing native device sensors and functionalities.

I know performance will be an issue when using Mobile App Framework, but considering our project scope, it will not be an issue. Given the timeframe and number of developers, using Mobile App Framework sounds proper.

Here are also some resources [Mobile Frameworks Comparison Chart](http://mobile-frameworks-comparison-chart.com/) and frameworks we've considered that I think worth noting: [Appgyver](http://appgyver.com), [Cordova](https://cordova.apache.org/), [Phonegap](http://phonegap.com/)

### Why choose PhoneGap?

It's opensouce MIT license! and since Cordova powers PhoneGap, I might as well take advantage of the additional features that PhoneGap offers: PhoneGap Build! (this is to avoid installing and configuring any platform SDKs locally)

-----

The following steps are a combination of instructions from mentioned book above and based off of my experience configuring my local development and using 3rd party cloud base services.

### Requirements and important initial step

**Installation**

- Install node.js
  - From experience, node.js versions and path can get complicated, I recommended installing node.js via `nvm`
- install PhoneGap (includes PhoneGap CLI)
  - Adding the PhoneGap CLI enables the use of Adobe's remote building capabilities, which means you don't need to have the platform SDKs installed in order to build your app. (There are caveats here; it is best to refer to the PhoneGap Build website at http://build.phonegap.com for more information.) Installing PhoneGap CLI will also install Cordova CLI, since PhoneGap is powered by Cordova engine.
  - Install via npm: `sudo npm install -g phonegap`
  - Check if installed: `phonegap --version`

**Starting a project**

- Create first project
  - Contains:
    - Our code
    - Other platform-specific code
    - Other assets required to generate an app ready for you to run on a simulator or device
- Manage project's platforms
- Manage project's plugins
- Build my project
- Deploy project to the simulator/device

**Additional notes on Build and Deploy**

When testing our app on a simulator, we either need to install platform SDKs if we where to test it locally.<br>
To avoid installing and configuring such SDKs:

- We can rely on [PhoneGap Build](http://app.phonegap.com/) to build the project and
- [Ripple Emulator](https://chrome.google.com/webstore/detail/ripple-emulator-beta/geelfhphabnejjhdalkjhgipohgpdnoc?hl=en) or [The PhoneGap Developer App](http://app.phonegap.com/) for simulating on different OS (Android, iOS, Blackberry, Windows). 

But a Mac is required to generate the certificates necessary for iOS app signing (even with PhoneGap Build) and is definitely required for deployment to the App Store. The same is true for Windows; you need to deploy to the App Store from Windows only.

-----

### Create first project

To create a project with PhoneGap CLI, `cd` to your projects directory (ex. `/www` or `/home`)

Run: `phonegap create ./PGHelloWorld com.phonegaphotshot.pghelloworld PGHelloWorld`

The first parameter indicates that a project should be created in a directory specified by the second parameter. The third parameter is the project ID, which must be unique and should be specified in reverse domain-name order. The final parameter is the name of the project.

-----

### Manage project's platforms

In this step, we will specify the platforms that the projects support. Besides adding platforms, we can also remove, update, and list out the supported platforms.

**To add platform:** `cordova platform add platform-name`

- `ios`: The iOS platform
- `android`: The Android platform
- `blackberry10`: The BlackBerry 10 OS platform
- `firefoxos`: The Firefox OS platform
- `wp7`: The Windows Phone 7 platform
- `wp8`: The Windows Phone 8 platform
- `windows 8`: The Windows 8 platform

**Listing the available platforms:** `cordova platform ls`

**Removing platforms:** `cordova platform remove platform-name`

**Updating platforms:** `cordova platform update platform-name`

-----

### Manage project's plugins

Plugins are the mechanism Cordova uses to provide native functionality to your app. 
Plugins can be managed using either the Cordova CLI or the PhoneGap CLI (which ends up using the Cordova CLI in the background). The important detail to remember when you use the PhoneGap CLI is that plugins must be installed locally (not remotely).

**To install plugins:** `phonegap local plugin add plugin-name`

[Official Documentation: Cordova - Plugin APIs](http://cordova.apache.org/docs/en/dev/cordova/plugins/pluginapis.html#Plugin%20APIsZ)

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

**Listing plugins:** `phonegap local plugin list`

**Removing plugins:** `phonegap local plugin remove plugin-name`

-----

### Building our project

Building involves compiling all the native code using the platform SDKs on your machine and then packaging your HTML, JavaScript, and CSS (and any assets) with this code so that it can be deployed to a simulator or device.

**To build project remotely via PhoneGap Build:**<br>
`phonegap remote build platform-name`

Building remotely using PhoneGap Build is a little different from building locally since you may not see the results of the build instantly; the service will build the code as soon as it has a chance. The only way to verify that things went as expected is to log on to your account at [https://build.phonegap.com/](https://build.phonegap.com/) and verify the results.

-----

### Deploy project to a simulator/device

Once we built a project, next is to **Test it**.
To do this, you can deploy the code to a simulator or deploy the code to a device. So far, I've only used [Ripple Emulator](https://chrome.google.com/webstore/detail/ripple-emulator-beta/geelfhphabnejjhdalkjhgipohgpdnoc?hl=en) to debug and simulate.

**To get started with Ripple Emulator**

- Install Ripple Emulator
- Enable it
- Run `phonegap serve` to retrieve address
- Enter local address to Ripple Emulator
