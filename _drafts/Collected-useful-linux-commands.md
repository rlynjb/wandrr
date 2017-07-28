---
layout: post
title: "Collected useful Linux Commands"
date: 2015-01-01 01:01:01
tags:
- linux
---

### Changing user accounts

- [sudo su commands](https://help.ubuntu.com/community/RootSudo)

-----

### Commands for searching

These are just a list of commands I find usefule when searching for text or files thoughout Linux system.

- [find](https://help.ubuntu.com/community/find)
- [locate]()
- [grep](https://help.ubuntu.com/community/grep)

-----

### Commands for sorting files

- [ls]()
- [ll]()
- Sort files in date `ll -tr` to check which files has been modified recently
- Check for any suspicious injected files

-----

### SSH and SCP

scp with port

`scp -P 21 root@myhost /home/direc/file.tar username@secondhost:/home/dir`

Where -P stands for port number

-----

### Tar compress and extract

- compress: `tar -czf folder.tar.gz folder`
- extract: `tar -xzf folder.tar.gz`

-----

### Useful techniques for configuring and managing server

Below is a gist of what this post contains.

- Some Server stuff techniques
- Benefits of checking /var/log/
- Checking for CPU or Port processes

-----

### PHP and Apache2

To check a website's php info: <br>
You can use either cli command `php` or create a file with phpinfo().<br>
Former solution will check for system wide php info.<br>
Latter solution will check specific site php info.

- create a `foo.php` file
- add ff code `<?php phpinfo(); ?>
- visit url 'your-domain.com/foo.php' and this will display all php configs on a specific website

**Sample uses**

- When updating a `php.ini` file and you want to see what a specific website is using. Because there can be multiple `php.ini` file somewhere.

-----

### NPM and Nodejs

Use NVM when managing different nodejs and npm versions on a server. Saves time!

-----

### Benefits of checking /var/log/

- Monitor a certain IP address activity hitting your server or certain file
- Monitor suspicious IP address activity

-----

### Checking for CPU or Port processes

Use `htop` or `top` commands

- [htop]()
- [top]()

Check for an open port by `ps aux | grep jekyll`

Kill a process or port by `kill -9 PID#`
