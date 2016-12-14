---
layout: post
title: "Getting Started with Magento Theming"
date: 2016-08-11 12:42:09
tags:
- cms
---

Installing manually was tedious so I've decided to use install Magento 2 via Docker and Docker Compose.

To get a glimpse of how Docker and Docker Compose works, I'ved jotted down notes here: [Notes on creating a convenient Local Development Workflow with Docker](Notes-on-creating-a-convenient-local-development-workflow-with-Docker)

Here is a sample `docker-compose.yml` file that installs Magento 2 [maginferno - magento2-docker-compose](https://github.com/mageinferno/magento2-docker-compose)

Grab a copy of Magento 2 files as well [Github - Magento](https://github.com/magento/magento2.git) and place it on your **host** and mount the necessary directories and files unto your **docker container**.

-----

### Issues I came across:

- [Admin Page 404 After Install Magento2 RC #2309](https://github.com/magento/magento2/issues/2309)
  * During the installation you entered unique admin URI (it generates automatically for you) eg. /admin_cr8w74 To get info about your URI use CLI command:
  * `/var/www/html/magento2$ php bin/magento info:adminuri`
- Admin username and password can be found in `docker-compose.yml` file
- resolving issue w/ Admin page
  * [There has been an error processing your request](https://community.magento.com/t5/Technical-Issues/There-has-been-an-error-processing-your-request/td-p/4905)
  * see comment with `In local.xml file you need to update all database credential`
    * this will display errors on `/admin_<unique hash>`
- install sample data:
  * `php bin/magento sampledata:deploy`, then `php bin/magento setup:upgrade`
  * if error occurs: clear cache, [Fatal error: Uncaught Error: Class 'Cli' not found](http://stackoverflow.com/questions/38668833/magento-2-cmd-fatal-error-uncaught-error-class-cli-not-found)
- retrieving your http://repo.magento.com credentials
  * [Get your authenticationn keys](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/connect-auth.html)

-----

### Useful commands and info

- clear cache via cli:
  * `php bin/magento cache:clean` and `php bin/magento cache:flush`
  * ref: [How to Flush, Enable, Disable Cache Command Line in Magento 2](https://www.mageplaza.com/kb/how-flush-enable-disable-cache.html)
- change to **Developer Mode** or other modes
  * `rm -rf <your Magento install dir>/var/di/* <your Magento install dir>/var/generation/*`
  * `magento deploy:mode:set developer`
  * ref: [Overview of setting Magento modes](http://devdocs.magento.com/guides/v2.0/config-guide/cli/config-cli-subcommands-mode.html)

-----

### Collections of Tutorials

- [Magento 2 tutorials from sessiondigital.com](http://www.sessiondigital.com/magento/magento-2-tutorials/)
- [Magento 2 - Frontend Developer Guide](http://devdocs.magento.com/guides/v2.0/frontend-dev-guide/bk-frontend-dev-guide.html)
- [Getting Started - Hands on with Theme from scratch](http://devdocs.magento.com/guides/v2.0/frontend-dev-guide/themes/theme-create.html)
  * This is to start building your theme from scratch, registering your theme and its directories
- [Magento theme structure](http://devdocs.magento.com/guides/v2.0/frontend-dev-guide/themes/theme-structure.html)
  * An indepth view of directory structure of a theme and what is required and optional
  * Discusses about CSS and JS assets, Static files is directly accessible from HTML link and script syntax while Dynamic files usage of CSS preprocessors
  * But my concern is more on **Magento2 Layout & Templating** since I will be implementing my [Front-End Flow](https://github.com/rlynjb/frontendflow) project
- [Indepth Magento 2 Templating system](http://www.sessiondigital.com/blog/magento-2-tutorial-how-to-use-the-new-front-end-templating-system/)
- [Intro to Layouts](http://magento.stackexchange.com/questions/118278/creating-a-custom-homepage-template-in-magento2)
- [Magento2 Theme - Layouts & Templates - Part1](http://excellencemagentoblog.com/blog/2016/04/11/magento2-theme-layouts-templates/)
- [Magento2 Theme - Layouts & Templates - Part2](http://excellencemagentoblog.com/blog/2016/04/11/magento2-theme-layouts-templates-part2/)

-----

### Starting with Magento2 Layouts and Templating

There is a steep learning curve with Magento2 Layout and Templating engine. Like any CMS, what builds a website display are mainly Layouts and Templates. Magento2 built their layout/templating engine with a strong emphasis of layout and content separation. So for the sake of learning and to simplify things, lets breakdown a Magento2 theme and start with Layout and Templates.

### Files and Directory structure inside Magento_Theme module
Files and Directory that we are concern are (this applies to other modules as well):

```
\theme_dir
  |-- \Magento_Theme
      |-- \layout
          |-- \override
              |-- \base
                  |-- default.xml
                  |-- default_header_blocks.xml
      |-- \page_layout
          |-- custom_home.xml
      |-- \templates
          |-- header.phtml
          |-- main-content.phtml
          |-- footer.phtml
      |-- layouts.xml
```

I'm overriding **Magento_Theme**'s `\layout` files and extending into **Magento_Theme**'s `\page_layout > custom_home_layout.xml` - `<referenceContainer name="page.wrapper">`

> There's a difference bet. Override and Extend

**Start it off by:**

- ref: [Magento2 Theme - Layouts & Templates - Part1](http://excellencemagentoblog.com/blog/2016/04/11/magento2-theme-layouts-templates/)
- Declare your layouts first on `layouts.xml`
- Create your page layout file inside `\page_layout`
- Then define your `<container>` along with name attr to hook it with Page Configuration files inside `\layout`

**Recall:**

#### Page Layout files
- An `*.xml` file where we define a page wireframe/structure.
  * Ex. Grid system
- Only uses Magento2's **containers** or `<referenceContainer name="" />`
- Should be declared on `layouts.xml` file for it to register.

#### Page Configuration files
- Uses a declared **Page Layout**
- Defines detailed structure, contents, meta info, etc (menu, nav, search box, widgets, links, contents, images) inside of header, main content, footer, columns.
  * Ex. Components

#### Generic Page Layouts
There is also another type of page layout that is not quite use often. For more info: [Magento2 Dev Doc - Generic layout](http://devdocs.magento.com/guides/v2.1/frontend-dev-guide/layouts/layout-types.html#layout-types-gen)

### Magento 2 Templating
- It seems like templating is just a matter of copy and pasting pieces of code that Magento 2 Modules provide.
- Use `<block />` to define a component inside a `<container />`
- Define a component class like so, `<block class="" />` and extend by defining a template to tweak template/customize HTML structure `<block class="" template="" />`

-----

### Further Templating Issues

- [How to load a phtml file only for homepage? (Magento 2)](http://magento.stackexchange.com/questions/108296/how-to-load-a-phtml-file-only-for-homepage-magento-2)

-----

up and running with magento 2 child theme

understadning templating

- [Frontend Developer Guide](http://devdocs.magento.com/guides/v2.0/frontend-dev-guide/bk-frontend-dev-guide.html)
