---
layout: post
title: "Beginning Mobile App Development Journey"
date: 2016-02-26 13:14:59
tags:
- app development
---

Consider this blog post as my notes on learning how to setup PhoneGap/Cordova locally, build and debug via PhoneGap Build.
If you want to know more about its history and detailed instructions, refer to this book: [Packtpub: PhoneGap Mobile Application Development Hotshot](https://www.packtpub.com/application-development/phonegap-3x-mobile-application-development-hotshot)

-----

I've been searching for a Mobile App Framework on which I can use languages I'm comfortable with (HTML, CSS, JavaScript) and also will be able to deploy on various devices utilizing native device sensors and functionalities.
I know performance will be an issue when using Mobile App Framework, but considering our usual project scope, given the timeframe and number of developers, using Mobile App Framework sounds proper.

### Why choose PhoneGap?

It's opensouce MIT license! and since Cordova powers PhoneGap, I might as well take advantage of the additional features that PhoneGap offers: PhoneGap Build! (this is to avoid installing and configuring any platform SDKs locally)

-----

### Installation

- Install node.js
  - From experience, node.js versions and path can get complicated, I recommended installing node.js via `nvm`
- install PhoneGap (includes PhoneGap CLI)
  - Adding the PhoneGap CLI enables the use of Adobe's remote building capabilities, which means you don't need to have the platform SDKs installed in order to build your app. (There are caveats here; it is best to refer to the PhoneGap Build website at http://build.phonegap.com for more information.) Installing PhoneGap CLI will also install Cordova CLI, since PhoneGap is powered by Cordova engine.
  - Install via npm: `sudo npm install -g phonegap`
  - Check if installed: `phonegap --version`

### Starting a project and Workflow

- [Create first project](#create-first-project)
- [Manage project's platforms](#manage-projects-platforms)
- [Manage project's plugins](#manage-projects-plugins)
- [Build my project](#building-our-project)
- [Deploy project to the simulator/device](#deploy-project-to-a-simulatordevice)

-----

### Two Environments

The PhoneGap command consists of two environments. The first is the local command environment. The local commands execute the command on your local machine. In this case, you must have the target device SDKs configured on your machine. For example, if you want to develop an Android application, you must acquire and configure the Android SDK on your machine.

The second environment is remote. Command-line commands execute the build process remotely using the cloud-based PhoneGap Build service. In this case, you don't need to configure any SDK on your local machine.

> I will only focus on remote commands, so I don't need to setup various platform SDKs locally

**Remote Commands via PhoneGap Build**

- Sign up an account: [http://build.phonegap.com](http://build.phonegap.com)
- Login via CLI: `phonegap remote login`

-----

### Create first project

To create a project with PhoneGap CLI, `cd` to your projects directory (ex. `/www` or `/home`)

Run: `phonegap create hello com.myapp.hello HelloWorld`

First argument `hello` specifies a directory for our project.<br>
Second argument `com.myapp.hello` is our application ID. Its in reverse domain style. We can create something like `com.yourdomain.applicationname`<br>
Third argument `HelloWorld` is our application name. This will be use as the application's display title. Its optional. If you are not setting the application name, it will use the name from the first argument. If you want to change the name, you can open config.xml and edit the name element.

Contains: Our code, Other platform-specific code, Other assets required to generate an app ready for you to run on a simulator or device

-----

### Manage project's platforms

PhoneGap Build, remote-based build automatically creates an iOs, Android, and Windows build for you.

-----

### Manage project's plugins

**For list of available plugins via PhoneGap Build:** [https://build.phonegap.com/plugins](https://build.phonegap.com/plugins)

**To install plugins:** `phonegap plugin add <source>`

Once a plugin has been successfully added to a project, the plugin APIs can be executed using JavaScript. Each plugin has its own way of accessing native APIs, so read the documentation for each plugin.

**Listing plugins:** `phonegap plugin list`

**Removing plugins:** `phonegap plugin remove <id>`

-----

### Building our project

PhoneGap Build compiles our application code and plugins only available in PhoneGap Build and builds our application in iOs, Android, and Windows.

**To build project remotely via PhoneGap Build:**<br>
`phonegap remote build <platform>`

-----

### Deploy project to a simulator/device

**Running and Debugging Remote:**<br>
`phonegap remote run <platform>`

Refer to [PhoneGap Build Documentation for instructions](http://docs.build.phonegap.com/en_US/index.html)

**Simulating with Ripple Emulator (locally):**

- Install [Ripple Emulator](https://chrome.google.com/webstore/detail/ripple-emulator-beta/geelfhphabnejjhdalkjhgipohgpdnoc?hl=en)
- Enable it
- Run `phonegap serve` to retrieve address
- Enter local address to Ripple Emulator

-----

**Notes on Submitting to app stores**

A Mac is required to generate the certificates necessary for iOS app signing (even with PhoneGap Build) and is definitely required for deployment to the App Store. The same is true for Windows; you need to deploy to the App Store from Windows only.


