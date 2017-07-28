---
layout: post
title: "Getting Started with Magento Theming"
date: 2016-12-27 11:14:55
tags:
- cms
- ecommerce
- magento2
---

### Before starting to build a theme in Magento2

So before starting to build a theme, we need to know Magento 2's architecture and status.

- Magento 2 is extremely modularize (reminds me of Drupal)
- it is based off of Zend Framework
- Alot of Major and Minor updates/changes in each version
- and foremost, it is Not practical to theme from scratch (trust me, I tried, unless you are a certified Magento 2 developer or someone willing to put in alot of time)
- it comes with its own Front-End workflow (I think it uses Grunt, Less)

Although, from all the learning curves listed above, Magento 2 is:

- a really secure Ecommerce system
- It has everything you need to immediately setup an online store
- theming maybe tough, alot of overriding of templates (but we will try to keep CSS and JS minimal and will use our own [Front-end workflow](https://github.com/rlynjb/frontendflow))

-----

#### **Setting up a Child Theme**

Once Magento 2 is installed

- Enable Development Mode `sudo php bin/magento deploy:mode:set developer`
  - ref: [How di u set developer mode in magento2](http://magento.stackexchange.com/questions/13125/how-do-i-set-developer-mode-in-magento-2)
- Create a directory in `/app/design/frontend/<company name>/<theme name>`
- Copy Magento 2 blank theme `/vendor/magento/theme-frontend-blank/` to `/app/design/frontend/<company name>/<theme name>`
- Rename all theme titles and names in `composer.json`, `registration.php`, `theme.xml`
  - in `theme.xml` add `<parent>Magento/blank</parent>`
- Login to admin to change theme and clear-cache
  - locate admin URL in `/etc/config.php`


#### **Create a template for a page**

- Define a new page layout in `layouts.xml` by copy & pasting a column tag
- Copy `1column.xml` and rename to the name of page, ex. `homepage.xml`
- Go to admin and set a page to use new page layout defined
- Clear cache in admin configuration page or cli `php bin/magento cache:flush`
- Create a template `*.phtml` inside of `/templates` directory and use `<block>` tag inside of `homepage.xml` file to point to the template file


#### **Override Magento 2 core templates**

- Follow Magento 2 front end developer guide
- Copy & paste codebase from Magento 2 github repo

Tips:

- Analyze layout first
- Look at default modules under `app/code/Magento` files and reference in `Magento_Theme` base templates


#### **Loading Front-End flow assets**

After loading Front-End flow assets files, we will comment out unnecessary Blank theme styles. This is a matter of inspecting unnecessary styles and commenting it out from its default `.less` files

Comment out Magento 2's `imports` in its root `/web/css/*.less` file

- `web/css/styles-m.less`
- `web/css/_styles.less`
- `web/css/source/_sources.less`

Initially, we will keep Magento 2 Blank theme's Grid system and remove its theme styles. Go back and forth to files above to remove styles.


#### **Recompile default Blank theme styles and new Front-End flow styles**

1. Delete static files
  - `rm -rf pub/static/frontend/<company name>/<theme name>/*`
  - `rm -rf var/cache/*`
  - `rm -rf var/page_cache/*`
  - `rm -rf var/view_preprocessed/*`
2. Redeploy static files
  - `php bin/magento setup:static-content:deploy`
  - `php bin/magento cache:clean && php bin/magento cache:flush`
  - `chown -R www-data:www-data var/ pub/ && chmod -R 777 var/ pub/`


#### **Credential Requirements**

As stated in its document, Secure keys do not use the normal Magento2 Marketplace username and password, rather

- Once logged in, generate public and private keys
  - username is Public key
  - password is Private key

* Need to sign up a Magento Marketplace account to take advantage of their features or add-ons that can be install via composer

-----

### The Docker way

Installing manually was tedious so I've decided to use install Magento 2 via Docker and Docker Compose.

To get a glimpse of how Docker and Docker Compose works, I'ved jotted down notes here: [Notes on creating a convenient Local Development Workflow with Docker](Notes-on-creating-a-convenient-local-development-workflow-with-Docker)

Here is a sample `docker-compose.yml` file that installs Magento 2 [maginferno - magento2-docker-compose](https://github.com/mageinferno/magento2-docker-compose)

Grab a copy of Magento 2 files as well [Github - Magento](https://github.com/magento/magento2.git) and place it on your **host** and mount the necessary directories and files unto your **docker container**.

-----

