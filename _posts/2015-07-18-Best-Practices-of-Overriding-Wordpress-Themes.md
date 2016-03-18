---
layout: post
title: "Best Practices of overriding Wordpress Themes"
date: 2015-07-18 10:47:13
tags:
- wordpress
---

While working on websites using Wordpress and Divi theme, I have came across some best practices for overriding Wordpress themes. So I thought of listing it here as a personal note for when working with upcoming Wordpress projects.

- First important practice I’ve learned was to create a Wordpress Child Theme. Editing code on Parent theme is a BIG NO-NO as to editing or modifying code on core files/code. Found this Wordpress documentation that helped me get started with creating a Child Theme. https://codex.wordpress.org/Child_Themes
- Use remove_action() and add_action to override Wordpress functions from functions.php
- Use remove_shortcode() and add_shortcode to override Wordpress shortcode functions from functions.php
