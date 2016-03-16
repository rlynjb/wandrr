---
layout: post
title: "Front-End Workflow with Wordpress"
date: 2016-01-29 12:07:09
tags:
- wordpress
- workflow
---

Prototyping and delivering an end product is one of the things I've been contemplating lately.
Being the only designer at work and yet, the one responsible for optimization and performance of Wordpress theme used, I have to find a way to satisfy both design and development.

Below are my usual workflow.

- **Gather requirements:**
  - What kind of website would it be?
  - Is there a sitemap or diagram provided?
  - How many regular pages will it contain?
  - What are their brand color scheme?
  - What's their choice of font/s?
  - Where can I access their existing assets, images, etc.
  - Are there sample websites they like?
  - Do they have an existing website?

These are atleast the initial questions that come to mind when gathering requirements.
Another one would be **planning it out**. At this phase, I will have to satisfy both our:

- _Project Manager_
  - Making sure I can deliver prototypes or layout design base from the gathered requirements.
  - Meet deadline.
- _Senior Backend Developer/Engineer_
  - Making sure I use modern technology, prefer opensource (MIT License).
    - Github.com will be your bestfriend on this :)
  - Use a theme that makes minimal http requests. This is usually up to me on how I build the dependencies/assets.
  - Convert some pages of wordpress to serve static page.
    - Example would be 404 page, convert it to static page so it doesn't need to make a request to DB often.
    - Wordpress has its way of doing alot of DB queries. Consider minimizing DB queries.
  - Use minimal plugins as possible. If there is a way to use default Wordpress features, take advantage of it.
  - When deploying, make sure to set Wordpress securities
    - Wordpress Hardening documentation
    - Wordpress Editing wp-config.php documentation
- _Also, consider other developers_
  - Make sure I use a documented theme so other developers can jump on the project as well.

Now with these rules in set. I have come to a conclusion to use [**FoundationPress**](https://foundationpress.olefredrik.com/).
We have used paid themes in the past, but the extra features included requires frequent update, no control over assets (HTTP requests) of theme, and in the long run, may not be performant. Also some themes, eventhough configurations was made easy for non-techie users, it makes alot of cpu processes and  database queries. Unnecessary features in theme and plugin dependencies may also become vulnerable to security attacks, bots injecting scripts unto Wordpress directories.
Rather than configuring themes and some plugins in wordpress admin dashboard, its recommended to do so in wordpress source files instead.

-----

### Why choose FoundationPress?

FoundationPress is basically Zurb Foundation framework, but created specifically to work with Wordpress as a theme.
I've been using Zurb Foundation for quite sometime, and with the recent upgrade they made on their framework, its more flexible on how we can include or exclude certain features of what builds a Responsive Website or Web Application, thus, customization of dependencies/assets and small filesize. Also, this framework is well-documented and support from its community is pretty responsive, I would file issues on their github repo and they are very helpful to resolve issues.

With regards to CSS Animations (yes, I've see trends lately where when you scroll a webpage, it would have those nifty animations), Foundation has released **Motion-UI** which is also included on FoundationPress.

- [Foundation Zurb](http://foundation.zurb.com/)
- [FoundationPress](https://github.com/olefredrik/foundationpress)

With the type of projects we received and working with only a few developers while meeting design approval and deadline, using a CSS framework is just proper.

- I don't need to re-code CSS styles. Good for rapid prototyping and optimize later.
- There are also pre-made JavaScript components. Again, good for rapid prototyping and optimize later.
- Documentation is on Zurb Foundation website, except custom documentation.
- FoundationPress handles the theme's architecture.
  - Just by looking at **package.json**, **bower.json**, and **gulp.js**, I can tell how the theme is architectured.
  - Except for SASS files. Its modules, settings, and dependencies are imported different than JavaScript files.
  - Motion-UI is still early in development and a bit tricky to implement, but I filed an issue related to setup. [Visit filed issue here](https://github.com/zurb/motion-ui/issues/56)

-----

### Wordpress Templating

To differentiate the files in FoundationPress, its good to get acquainted with [Wordpress Template Files](https://developer.wordpress.org/themes/basics/template-files/).

**Prototyping** is easy as adding a page on wordpress admin dashboard and create an instance of a `page.tpl` file and renaming with a given extension of the name of the page you added on wordpress admin dashboard `page-{slug}.php`.

Another technique is if you were to use an **approved design prototype** to multiple pages, you can just convert that `page-{slug}.php` file into a template `/FoundationPress/templates/template-name-here.php`, then disseminate it by setting it as a Template under `Name of page you added > Page Attributes > Template` at wp admin dashboard.

There are many ways you can fully customized a CMS like functionality with wordpress without the need of plugin. All you have to do is enable these features in `functions.php`.
Some features that are worth noting are:

- Custom Post Type
- Custom Category and Tags
- Custom Fields

You can also create a template or prototype for these Custom Post Types. Enable Custom Fields if required for users to input pieces of data and enable Custom Category if you want to sort or filter these items in theme or in wordpress admin custom post type dashboard.

-----

### WP Rest API

When building an application in certain pages of wordpress using JavaScript, we can also take advantage of this plugin [WP Rest API](http://v2.wp-api.org/).

-----

### Managing wordpress with WP-CLI

This has been really helpful especially with checking the status of your wordpress core, plugins, and themes. To avoid cpu usage on wordpress admin dashboard, you can manage your wordpress via cli! [WP-CLI](http://wp-cli.org/)
