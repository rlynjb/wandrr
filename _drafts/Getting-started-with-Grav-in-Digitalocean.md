---
layout: post
title: "Getting started with Grav on DigitalOcean"
date: 2016-05-27 14:37:01
tags:
- static site
---

### create a droplet

- [https://learn.getgrav.org/hosting/vps/digitalocean](https://learn.getgrav.org/hosting/vps/digitalocean)

### debugging nginx with php5-fpm

- http://serverfault.com/questions/562062/nginx-with-php-fpm-got-502-bad-gateway-on-ubuntu-server-12-04
- http://stackoverflow.com/questions/1706111/where-can-i-find-the-error-logs-of-nginx-using-fastcgi-and-django

### fixing php 502 gateway page

- https://github.com/owncloud/core/issues/14187

-----

### tips on using configuration files, yaml:

- do not change configs in `/system/config/system.yaml` and `/system/config/site.yaml`
- do not change configs in `/user/plugins/`
- rather override them in `user/config/system.yaml`, `user/config/site.yaml`, `user/config/plugins/myplugin.yaml`

note: all yaml files are contructed by name spacing. Grav picks it up in a hierarchy order.

-----

### method for custom templating in Grav

1. ff procedure on https://learn.getgrav.org/themes to setup foundation of a website. ex. coding overall layout, header, footer, navigation.
2. convert static contents on template to **Grav Content - Modular Pages** https://learn.getgrav.org/content
