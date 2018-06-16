---
layout: post
title: "Querying MySQL Database in Wordpress and ACF Plugin"
date: 2018-06-16 12:15:10
tags:
- wordpress
- mysql
---

We can query wordpress database using `wp cli`.

Below are a couple of commands to help query database. FYI, I dont have much experience with backend. I specialize in Front-End Development but this is my method of getting by backend issues.

Enter WP DB mysql prompt.
Run `wp db cli` in terminal.
ref: [WP CLI](https://developer.wordpress.org/cli/commands/db/)

To check fields inside of a table.
Run `DESCRIBE table;`.

To show all tables.
Run `show tables;`.

To query a table with condition.
Run `SELECT * FROM table WHERE post_type="acf"/G;`.
We've included `/G` to pretty format print out queries in terminal.

When dealing with ACF fields.
Where do ACF Fields live in database?
To start off, ref: [Where do fields live in the database](https://support.advancedcustomfields.com/forums/topic/where-do-fields-live-in-the-database)
