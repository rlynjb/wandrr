---
layout: post
title: "Useful techniques for configuring and managing server"
date: 2015-01-01 01:01:01
tags:
- linux
---

Below is a gist of what this post contains.

- Some Server stuff techniques
- Benefits of checking /var/log/
- Checking for CPU or Port processes

-----

### Some Server stuff techniques

#### **PHP and Apache2**

To check a website's php info: <br>
You can use either cli command `php` or create a file with phpinfo().<br>
Former solution will check for system wide php info.<br>
Latter solution will check specific site php info.

- create a `foo.php` file
- add ff code `<?php phpinfo(); ?>
- visit url 'your-domain.com/foo.php' and this will display all php configs on a specific website

**Sample uses**

- When updating a `php.ini` file and you want to see what a specific website is using. Because there can be multiple `php.ini` file somewhere.


#### **NPM and Nodejs**

Use NVM when managing different nodejs and npm versions on a server. Saves time!

-----

### Benefits of checking /var/log/

**Sample uses**

- Monitor a certain IP address activity hitting your server or certain file
- Monitor suspicious IP address activity

-----

### Checking for CPU or Port processes

Use `htop` or `top` commands

- [htop]()
- [top]()

Check for an open port by `ps aux | grep jekyll`

Kill a process or port by `kill -9 PID#`
