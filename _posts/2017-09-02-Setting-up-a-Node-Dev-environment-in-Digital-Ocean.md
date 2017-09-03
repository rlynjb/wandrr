---
layout: post
title: "Setting up a Node Dev Environment in DigitalOcean"
date: 2017-09-02 20:18:14
tags:
- web development
- app development
- front end development
---

This has been a frustration for a week now. During my spare time, I've been trying to configure an easy way for me to develop front end nodejs projects using DigitalOcean and its One-Click apps.

I found out that those One-Click apps uses Ubuntu version 16.04 I believe, and these ubuntu version doesn't play well with nodejs modules, especially with modules you have to install globally. It doesn't find its nodejs global link for some reason. So, I came up a way to rectify this issue.

For best Nodejs compatibility, use Ubuntu v14.04 instead.

1. Install Nodejs via link
	- [How to install nodejs on an ubuntu 14.04 server](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-an-ubuntu-14-04-server)
	- to avoid nodejs version conflicts, its best to install and use NVM as well
2. Install git by running `sudo apt-get install git`
3. Now install apache2 via link
	- [how to install linux apache mysql php lamp stack on ubuntu v14.04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04)

So far, I've installed all my repo and it works well.
