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

Inpired by this article [I swapped my MacBook for an iPad + Linode](http://yieldthought.com/post/12239282034/swapped-my-macbook-for-an-ipad). I decided to take the bandwagon of developers using iPad for development. Since I specialized in Front-End Development. I just needed to add additional tools to my workflow.

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
- Bluetooth keyboard
	- [Helpful Keyboard Shortcuts](https://support.apple.com/en-us/HT205237)
- Sprint unlimited data plan

### Apps:

- MIHTool for debugging websites/web apps
- Reflection for SSH access to remote servers
- Digital Ocean - remote servers
- Vim - code editor

-----

**Reflection** and **Vim** are pretty self-explanatory tools. I've always use the CommandLine and Vim as my main tools. Advantages of learning Vim is that you can SSH any remote server and use that as your development environment. I'm glad I took the time to learn Vim and get myself use to the CommandLine. I love simplicity. Having these two tools, I didn't need to have multiple softwares open to develop. And Oh Yea, I forgot to add **Tmux**.

Another tool to avoid opening multiple terminal windows is to use **Tmux**. It's a terminal multiplexer, this means you can use a single Terminal window and open multiple panes and windows inside a single terminal window.

So there we have it, my 3 main tools: Reflection, Vim, and Tmux.

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

-----

So this is how I am able to develop using an iPad Pro. Next review will be on **MIHTool** app. This is **Chrome Development tool** browser alternative for iPad.
