---
layout: post
title: "Simple instructions for Drupal Minor Updates"
date: 2016-04-01 12:26:55
tags:
- drupal
---

This blog post tackles implementing **Minor Updates** on Drupal websites. Its a short, simple, and pretty straight-forward instructions.

-----

### References and Tools

- [Update procedure (minor version change)](https://www.drupal.org/node/1223018)
- [Use Drush to Export/Import a Drupal MySQL Database Dump File](http://tylerfrankenstein.com/code/use-drush-export-import-drupal-mysql-database-dump-file)
- [Drush Commands](http://drushcommands.com)

### Two ways to check for Drupal Update Status

- via Website GUI
  - `http://www.website-name.com/admin/reports/updates`
  - `Reports > Available Updates`
- via CLI
  - `drush pm-updatestatus`

-----

### Preparation before Updating a Drupal website

1. Backup database via Drush
  - `drush sql-dump > name_of_site-date.sql`
2. Backup core files by compressing directory containing drupal core files
  - `tar -czf site_name_date.tar.gz /path_to_site_directory/`
3. Show a report of available minor updates to Drupal core and contrib projects.
  - `drush pm-updatestatus`
4. Backup `.htaccess` by making a copy and dumping outside of drupal website directory
  - `cp .htaccess ../`

-----

### Implementing Minor Updates on Drupal sites

Only _Security Updates_ of core and modules will be performed. Updating Modules with `Update available` message may conflict with other module or drupal core version.

1. cd to drupal website directory and run `drush up drupal` to update drupal core
2. run `drush pm-updatestatus` again to check for other module updates
3. run `drush up <name of module>` to update a module
