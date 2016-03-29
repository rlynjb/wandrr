---
layout: post
title: "Doing drupal minor updates"
date: 2016-03-29 16:02:49
tags:
- drupal
---

h1. Updating Drupal sites

- Update procedure (minor version change) - https://www.drupal.org/node/1223018
- Use Drush to Export/Import a Drupal MySQL Database Dump File - http://tylerfrankenstein.com/code/use-drush-export-import-drupal-mysql-database-dump-file

- http://drushcommands.com/drush-6x/
link is redirected to drush 6, I believe we are using drush 6 on our 108 server - rlyn

- To check updates on website GUI, go to:
<pre>
http://www.website-name.com/admin/reports/updates

Reports > Available Updates
</pre>

-----


h2. Prepping and initial steps before updating/upgrading drupal sites

1. Backup database by Drush
<pre>
drush sql-dump > name_of_site-date.sql
</pre>

2. Backup core files by compressing public_html directory
<pre>
tar -czf site_name_date.tar.gz /path_to_site/public_html/
</pre>
here is also a link to reduce load of backup scripts with nice and ionice
http://www.faqforge.com/linux/reduce-load-of-backup-scripts-with-nice-and-ionice/
sample command would be:
<pre>
ionice -c2 -n7 nice -n19 tar -czf site_name_date.tar.gz /path_to_site/public_html/
</pre>

3. Show a report of available minor updates to Drupal core and contrib projects.
<pre>
drush pm-updatestatus
</pre>

4. Backup .htaccess and /sites/default/settings.php by making a copy and dumping outside of public_html directory
<pre>
cp .htaccess ../
cp sites/default/settings.php ../
</pre>

-----

h2. Implementing Minor Updates on Drupal sites

we will only update Modules (plugins) that require Security Updates. Updating Modules with Update available message may conflict with other module or drupal core version.

1. cd to public_html and run drush up drupal to update drupal core

2. run drush pm-updatestatus again to check for other module updates

-----

h4. After running Drupal core update, if 500 error occur whole drupal update, add this to htaccess:
<pre>
# Follow symbolic links in this directory.
Options +SymLinksIfOwnerMatch
</pre>
