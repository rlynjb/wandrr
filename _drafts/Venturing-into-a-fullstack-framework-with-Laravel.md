---
layout: post
title: "Venturing into a Fullstack Framework with Laravel"
date: 2016-11-02 09:46:43
tags:
- php
---

Indeed, I feel like its time to venture out of Front-End Web Development and look into a Fullstack Framework. One of my favorite framework is Keystone.js. It is a Node.js Database-driven framework. But learning a framework based off of PHP is mandatory, and so I came across Laravel. I'm not going to necessarily drift away from Keystone.js. As a Front-End Web Developer, I love Javascript and I don't think I am going to give the language up easily.

My goal is to master atleast 1 or 2 Fullstack framework that is based off of 2 different language, Keystone.js and Laravel, but this blog post will focus on Laravel with a bit of comparison with Keystone.js and discusses about some of the features of what comprises a small-large scale web applications.

I've also took the time to do reseach and write a comparison chart. Below is my researched with a high-level view of what features I look for in a framework.

|                         | **Keystone.js**             | **Laravel**       |
|                         | http://keystonejs.com       | https://laravel.com/docs/4.2/introduction |
| ----------------------- | :-------------------------: | :---------------: |
| Language                | Node.js                     | PHP               |
| Templating, Routing     | Swig, Jade, handlebars. Yes | Blade. Yes         |
| RESTful                 | Yes                         | Yes               |
| CRUD, Database          | Yes, MongoDB                | Yes, MySQL        |
| ACL                     | Yes                         | Yes               |
| Authentication and Session Management  | Yes                         | Yes               |
| CMS                     | Yes, Automatically generated Admin UI          | No                 |
| Code Readability        | Simple and Clean            | Simple and Clean  |
| Programming Style       | MVC                         | MVC               |
| Server Maintenance      | NVM, easy switching of Nodejs versions in server, not too much dependencies |  |
| Application Maintenance | NPM, manages versions of modules in application |  |
| Security                | no credentials or keys are stored in code, they are stored in a separate |  |
| Documentation           | apidoc.js                             |  |
| Community Support       | Active github repo, future releases, books, tutorials, opensource community |  |

<br>

### Learning Resources

Since I'm discovering Laravel and the whole PHP realm, I've discovered a site called [envatotuts+](https://tutsplus.com/) which carries Laravel tutorials from beginner to advance level.

- [Get Started with Laravel 5](https://code.tutsplus.com/courses/get-started-with-laravel-5)
- [Build a CMS with Laravel](https://code.tutsplus.com/courses/build-a-cms-with-laravel)
- and more, there are various tutorials that covers what we can do with Laravel

<br>

### Getting started with Laravel

I first created a github repo and followed the instructions for [installing Laravel](https://laravel.com/docs/5.3/installation) via Laravel Installer on my Mac.

- On my local, I just ran `php artisan serve` to start a development environment
- Also take into consideration of Configuration. We also need to check for Directory permissions and Application Key.
- All of these information are available at [https://laravel.com/docs/5.3/installation](https://laravel.com/docs/5.3/installation)

Tranferring your Laravel local code to an Ubuntu stage server was a bit of a challenge.

- There were missing php dependencies, I had to collaborate with other developers to solve this issue.
- Set its Web Document Root to its `/public` directory.
- Copy `.env.example` file as `.env` file and run `php artisan key:generate`

There were no problem with transferring our Application code, it was more of setting its environment.

<br>

### Understanding Laravels' Front-End Workflow

Laravel comes with a default install of Bootstrap, Vue, SASS, Webpack, and uses Gulp.js to compile its assets, although, Laravel developed its own compiling tool which is built on top of Gulp.js called **Laravel Elixir**. It is an NPM module and is defined in `package.json`. Laravel also uses NPM to install the default Front-end packages.

Upon readings its [documentation on Laravel Elixir](https://laravel.com/docs/5.3/elixir), it seems like this tool makes it easy for developers to use Gulp.js. Though, the only drawback I forsee using Laravel Elixir is we can't further customize our build process and we will depend on Laravel Elixir's features.

Since I have a background with Front-End Development and I've growned accustomed to some front-end packages, I will be using my own [Front-End Workflow starterkit theme](https://github.com/rlynjb/frontendflow), instead re-installing NPM and Bower packages and redefining paths and build process in my Gulp.js file.
