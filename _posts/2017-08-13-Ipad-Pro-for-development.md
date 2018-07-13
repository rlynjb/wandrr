---
layout: post
title: "Ipad Pro for Development"
date: 2017-08-13 20:18:14
tags:
- web development
- app development
- code editor
- front end development
---

Inpired by this article [I swapped my MacBook for an iPad + Linode](http://yieldthought.com/post/12239282034/swapped-my-macbook-for-an-ipad). I decided to jump in the bandwagon of developers using iPad for development. Since I specialized in Front-End Development. I just needed to add additional tools to my workflow.

### Why use Ipad?

Everybody has its reasons for using Ipad for development. My personal preference are:

- its portable
	- I can easily toss an ipad without having to worry about internal hardware breaking
- I always bring my backpack of laptop with me
	- due to vegas heat, I hate leaving my laptop in my car, with iPad, its easier to carry it around, not much weight
- sometimes, i love going to coffee shops or eating out somewhere
	- its nice to have convenient access to the internet and my code

### Devices:

- iPad Pro 10.5
- Bluetooth keyboard (optional)
	- [Helpful Keyboard Shortcuts](https://support.apple.com/en-us/HT205237)
- Sprint unlimited data plan

### Apps:

- Textastic for code editor and SSH access to remote servers
  - from most of the IDEs i've tried, this is really awesome. It provides a tab bar above the ioad kehboard for easy access to special characters we often used in coding.
  - and they also recently included SSH terminal and a window tab for files that are opened.
  - Vim is usually my go to editor but it can be difficult to code on ipad with it.
- Working Copy
  - this cost 15.99 though but its worth it. A code editor that is tightly integrated with Git but also has SSH upload capability.
- Inspect - Web development tool for ios
  - this tool has pretty much of what i needed when developing front end.
  - has an element inspector, console, responsive viewports. i prefer this better than Coda
- Digital Ocean - remote servers
  - this is for running Node.js server or frontend build tools
- and other remote servers or Baas like Heroku or Firebase


-----

As for my remote server setup **Digital Ocean droplets**. I'm using a LAMP server.

Its pretty easy to create a server image using Digital Oceans and alike services. Just create an account and follow the remaining instructions. Usually these remote server services offer a variety of preinstalled applications on their server.

As for what I need to setup my dev environment.

- I will need to be able to handle multiple projects using a single IP address
- Hence, I will access my projects using ports or subdirectory url
- Since my dev stack are: HTML5, CSS3, JavaScript, Node, PHP. I decided to use LAMP stack.

-----

### Method for setting up my remote server

1. Log in to your Digital Ocean account
2. Create a server image with LAMP on 16.04 ubuntu version
3. Once Droplet is complete. Open you **Reflection** app
4. Access your remote server by using SSH. `ssh root@given_ip_address`
5. Change your unix password to your new preferred password
6. After accessing your remote and server and changing your new password. Open Chrome browser or MIHTool browser and point to the given IP Address
7. Install Nodejs by running `sudo apt-get install nodejs`. This should include **NPM** as well
8. Now, go to your public directory where an `index.html` is being served. `cd /var/www/html/`
9. On this directory `/var/www/html/` you can `git clone` your projects and serve each on a part of subdirectory url
