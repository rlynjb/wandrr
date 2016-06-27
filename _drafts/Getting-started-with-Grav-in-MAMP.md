---
layout: post
title: "Getting started with Grav on MAMP"
date: 2016-06-20 20:37:35
tags:
- static site
---

### install brew

[http://brew.sh/](http://brew.sh/)<br>
This is to install **git** and other development goodies 

### install MAMP

[https://www.mamp.info/en/](https://www.mamp.info/en/)<br>
You can use any webserver but I've used MAMP because it was the quickest way I can install a webserver eventhough we are not using mysql database.

### install grav

1. download the Grav core files from [https://getgrav.org/downloads](https://getgrav.org/downloads) and dump into `htdocs` directory.
  - You can choose either just Grav core or Grav core + admin plugins
2. Unzip the `grav-admin-v*.*.**.zip` file on the `htdocs` directory.
3. You can rename the grav directory to whatever project name you wish or move the grav core files to a github repo directory.
  - **tip:** make sure to move `.htaccess` file as well to avoid **404 Not Found** error when visiting subpages. for more info, check [https://learn.getgrav.org/troubleshooting](https://learn.getgrav.org/troubleshooting)

-----

### method for converting an existing HTML5 template to Grav theme

1. unzip the html5 zip file unto the `user/themes/` directory
2. register your theme by ff step 1 on link [https://learn.getgrav.org/themes/theme-tutorial](https://learn.getgrav.org/themes/theme-tutorial). 
3. Now we will add **Base Template**.

-----

### method for custom templating in Grav

1. ff procedure on https://learn.getgrav.org/themes to setup foundation of a website. ex. coding overall layout, header, footer, navigation.
  - this is converting psd/design comps to interactive Grav theme
2. convert static contents on template to **Grav Content - Modular Pages** https://learn.getgrav.org/content
  - this is basically chopping the templates further and separating html markups from contents, taking advantage of Grav Content
3. taking it further, we will install **Grav Admin** plugin https://learn.getgrav.org/admin-panel/introduction
4. after getting around admin, we will table **forms**
