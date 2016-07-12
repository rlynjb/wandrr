---
layout: post
title: "Getting started and Theming with Grav"
date: 2016-06-20 20:37:35
tags:
- static site
---

# Getting Started on Digital Ocean

### create a droplet

- [https://learn.getgrav.org/hosting/vps/digitalocean](https://learn.getgrav.org/hosting/vps/digitalocean)

### debugging nginx with php5-fpm

- http://serverfault.com/questions/562062/nginx-with-php-fpm-got-502-bad-gateway-on-ubuntu-server-12-04
- http://stackoverflow.com/questions/1706111/where-can-i-find-the-error-logs-of-nginx-using-fastcgi-and-django

### fixing php 502 gateway page

- https://github.com/owncloud/core/issues/14187

### tips on using configuration files, yaml:

- do not change configs in `/system/config/system.yaml` and `/system/config/site.yaml`
- do not change configs in `/user/plugins/`
- rather override them in `user/config/system.yaml`, `user/config/site.yaml`, `user/config/plugins/myplugin.yaml`

note: all yaml files are contructed by name spacing. Grav picks it up in a hierarchy order.

### method for custom templating in Grav

1. ff procedure on https://learn.getgrav.org/themes to setup foundation of a website. ex. coding overall layout, header, footer, navigation.
  - this is converting psd/design comps to interactive Grav theme
2. convert static contents on template to **Grav Content - Modular Pages** https://learn.getgrav.org/content
  - this is basically chopping the templates further and separating html markups from contents, taking advantage of Grav Content
3. taking it further, we will install **Grav Admin** plugin https://learn.getgrav.org/admin-panel/introduction
4. after getting around admin, we will table **forms**

-----

# Getting Started on MAMP

### 1. Install Brew

This is to install **git** and **other development goodies** if you are a fan of commandline.

- [http://brew.sh/](http://brew.sh/)
- [http://commandlinepoweruser.com/](http://commandlinepoweruser.com/)

-----

### 2. Install MAMP

You can use any webserver but I've used **MAMP** because it was the quickest way I can install a webserver and setup a **local Apache** eventhough we are not using MySql database.

- [https://www.mamp.info/en/](https://www.mamp.info/en/)

-----

### 3. Install Grav

1. Download **Grav core + admin plugins** files from [https://getgrav.org/downloads](https://getgrav.org/downloads) and place into `htdocs` directory.
  - You can choose either **Grav core** or **Grav core + admin plugins**
  - If **Grav core** only, you have the option to install **Grav admin** later by running `bin/gpm install admin` on the root directory of your **Grav core** files.<br>
    More info: [https://learn.getgrav.org/admin-panel/introduction](https://learn.getgrav.org/admin-panel/introduction)
2. Unzip the `grav-admin-v*.*.**.zip` file on the `htdocs` directory.
3. You can rename the **Grav** directory to whatever project name you want.
  - You can also move the **Grav core files** to an empty **Github Repo directory**.
  - **Tip:** Make sure to move `.htaccess` file as well to avoid **404 Not Found** error when visiting subpages.
  - For more info, check [https://learn.getgrav.org/troubleshooting](https://learn.getgrav.org/troubleshooting)

- [https://getgrav.org/](https://getgrav.org/)

-----

### 4. Method for setting up a pre-made HTML5 template to Grav theme

1. Unzip the **HTML5 theme** zip file unto the `user/themes/` directory.
2. Register your theme by following **Step 1 - Base Theme Setup** on [https://learn.getgrav.org/themes/theme-tutorial](https://learn.getgrav.org/themes/theme-tutorial). 
  - For **Step 1 - Base Theme Setup** - #2<br>
    _Tip:_ You can use the same HTML5 theme directory name or you can clean up directory name by renaming and practicing proper naming convention.<br>
    _Ex:_ Avoid whitespace, avoid special characters except `_` and `-` following *camel case or snake case* naming convention.
  - For **Step 1 - Base Theme Setup** - #3<br>
    _Tip:_ I chose to follow **Grav's Theme directory structure** rather than to use the **HTML5 theme** default directory structure to avoid nested directory level, plus, Grav runs a _gpm_ engine which goes through each directories and yaml files to read data.
  - For **Step 1 - Base Theme Setup** - #4<br>
    _Tip:_ I believe this basically tells Grav that we are extending a Grav Theme class and our custom theme gets registered unto Grav core files.
  - For **Step 1 - Base Theme Setup** - #5<br>
    _Tip:_ This file just enables our theme, but later on, there are more theme configuration that uses this file.

-----

### 5. Method for loading assets and partial out the main index.html file

Now that we have setup our theme directory structures and registered our theme to Grav core files. We will continue on by:

- Load assets (css, js, images) in Head and Body tags.
- Introduction to using Twig templating engine.
- Organize our code in `index.html` file by using Grav's `/templates/partials`.

1. Now, we load our assets by moving HTML5 theme assets to Grav theme's asset directory structure. Ex: `/css`, `/fonts`, `/images`, `/js`, `/templates`
  - This step is a replacement for **Step 2 - Add Bootstrap**<br>
    We are not using Boostrap, instead we are using the HTML5's assets.
2. Next is to just follow the remaining steps, **Step 3 - Base Template** to **Step 8 - Testing**.
  - This step pretty much explains:<br>
    **Loading assets.** When to use `theme_url` twig variable and `do assets.add('')` twig function and how it relates with **Grav's Asset Manager**.<br>
    **Introduction to basic Twig syntax.**<br> Also, exploring some of Grav's global twig variables.
    **Partial out** the theme's header section, footer section, and main content section to maintain a cleaner `base.html.twig` file.

-----

### 6. Breaking our home page template file further by using Modular Pages

Most HTML5 themes comes with a home page designed similar to one-page website designs. For this step, we are going to breakdown this one-page website design into sections and use **Grav's Modular Pages** templating to separate and organize these sections.

1. Open `base.html.twig` template and analyze what HTML tag is used to contain contents of each sections.
  - _Tip:_ Usual container tags are `<section></section>` and `<div id=""></div>`
2. After determining the HTML tag container, convert these sections into **Grav's Modular Pages**.
  - Learn more about Modular Pages on the ff. link and ff. instructions: [https://learn.getgrav.org/content/modular](https://learn.getgrav.org/content/modular)
  - It is also a good idea to scheme through **Grav's Content** documentation page [https://learn.getgrav.org/content](https://learn.getgrav.org/content) to get a glimpse of the parts of a page.

-----

### 7. Creating custom fields to let users update data in theme by using Blueprint Pages

Now that we've broken our template further by each sections using **Modular Pages**. What if we wanted users to update contents or bits pieces of data in each section using **Grav's Administration Panel**?

In this step, we will use Grav's Forms called Blueprints [https://learn.getgrav.org/forms/blueprints](https://learn.getgrav.org/forms/blueprints) to convert **static data** into editable ones using Grav's `Admin dashboard > Pages`.

For an overview and how to setup a **Themes and Plugins Blueprints** or **Pages Blueprints**, go to this link [https://learn.getgrav.org/forms/blueprints](https://learn.getgrav.org/forms/blueprints).

My experience with setting up Blueprints for **Theme** configuration page and for each **Modular Pages** was quite challenging. Grav's documentation doesn't seem to provide detailed information on **how to define a field and which directory its information is stored**.

Although for **Theme Blueprint** it was pretty straight forward.

1. Create a `blueprints.yaml` file in the root directory of theme.
2. Follow the **Components of a Blueprint** in [https://learn.getgrav.org/forms/blueprints](https://learn.getgrav.org/forms/blueprints)
  - **Tip:** a YAML file will be generated for Theme configuration page in `user/config` directory.


It was trial and error for **Modular Page Blueprints** because its documentation seem to lack information on **how to define a field and which directory its information is stored**.

An overview method I find when working with Modular Page Blueprints are:

1. Create a `blueprints` directory under root template directory `yourtheme > blueprints`.
   - Since we are creating a blueprint for modular pages, we are going to store our blueprints (`*.yaml` files) under modular directory.
   - So with this, create a modular directory under `yourtheme > blueprints > modular`
2. Create a `some-modular-template-name.yaml` file that pertains to a modular template.
  - **Tip:** Make sure your `.yaml` file name matches a Modular template name you want to create Admin custom fields for.
3. When defining `*.yaml` file form, a good example would be the default **Grav antimatter theme**, [https://github.com/getgrav/grav-theme-antimatter/blob/develop/blueprints/modular/showcase.yaml](https://github.com/getgrav/grav-theme-antimatter/blob/develop/blueprints/modular/showcase.yaml)

**Also, an additional note to keep in mind when working with Page Blueprints**

Grav reads data in `*.yaml` files in sequence of how directories and files are structured, So when defining a field, it needs to be under a parent `header.` because blueprint pages store its data in pages headers. Also when uploading media files, Grav stores these media files under its page direcotory.
