---
layout: post
title: "Venturing into a Fullstack Framework with Laravel"
date: 2017-02-08 10:58:47
created_date: 2016-11-04 10:39:29
tags:
- php
- fullstack
---

Date Published: Nov 11, 2016

Indeed, I feel like its time to venture out of Front-End Web Development and look into a Fullstack Framework. One of my favorite framework is Keystone.js. It is a Node.js Database-driven framework. But learning a framework based off of PHP is mandatory, and so I came across Laravel. I'm not going to necessarily drift away from Keystone.js. As a Front-End Web Developer, I love Javascript and I don't think I am going to give the language up easily.

My goal is to master atleast 1 or 2 Fullstack framework that is based off of 2 different language, Keystone.js and Laravel, but this blog post will focus on Laravel with a bit of comparison with Keystone.js and discusses about some of the features of what comprises a small-large scale web applications.

Since I'm going back and forth with this blog post, writing my experience from choosing to mastering a framework, I've included a table of contents below.

-----

### Table of Contents

- [Comparison chart: Keystone.JS and Laravel](#comparison-chart)
- [Learning Resources](#learning-resources)
- [Getting started with Laravel](#getting-started-with-laravel)
- [Understanding Laravel's Front-End Workflow](#understanding-laravels-front-end-workflow)
- [Coding templates to populating static data from JSON file](#coding-templates-to-populating-static-data-from-json-file)
- [From Static data to implementing a Database](#from-static-data-to-implementing-a-database)
- [Simple Contact form, Sending Emails](#simple-contact-form-sending-emails)
- [Intro to Create in CRUD](#intro-to-create-in-crud)
- [Method for developing a project from scratch](#method-for-developing-a-project-from-scratch)
- [Defining my specs for a custom Admin Panel](#defining-my-specs-for-a-custom-admin-panel)
- [Building a CMS from scratch](#building-a-cms-from-scratch)

-----

# Comparison chart

I've also took the time to do research and write a comparison chart. Below is my researched with a high-level view of what features I look for in a framework.

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


-----


# Learning Resources

Since I'm discovering Laravel and the whole PHP realm, I've discovered a site called [envatotuts+](https://tutsplus.com/) which carries Laravel tutorials from beginner to advance level.

- [Get Started with Laravel 5](https://code.tutsplus.com/courses/get-started-with-laravel-5)
- [Build a CMS with Laravel](https://code.tutsplus.com/courses/build-a-cms-with-laravel)
- and more, there are various tutorials that covers what we can do with Laravel

-----


# Getting started with Laravel

I first created a github repo and followed the instructions for [installing Laravel](https://laravel.com/docs/5.3/installation) via Laravel Installer on my Mac.

- On my local, I just ran `php artisan serve` to start a development environment
- Also take into consideration of Configuration. We also need to check for Directory permissions and Application Key.
- All of these information are available at [https://laravel.com/docs/5.3/installation](https://laravel.com/docs/5.3/installation)

Tranferring your Laravel local code to an Ubuntu stage server was a bit of a challenge.

- There were missing php dependencies, I had to collaborate with other developers to solve this issue.
- Set its Web Document Root to its `/public` directory.
- Copy `.env.example` file as `.env` file and run `php artisan key:generate`

There were no problem with transferring our Application code, it was more of setting its environment.


-----


# Understanding Laravels' Front-End Workflow

Laravel comes with a default install of Bootstrap, Vue, SASS, Webpack, and uses Gulp.js to compile its assets, although, Laravel developed its own compiling tool which is built on top of Gulp.js called **Laravel Elixir**. It is an NPM module and is defined in `package.json`. Laravel also uses NPM to install the default Front-end packages.

Upon readings its [documentation on Laravel Elixir](https://laravel.com/docs/5.3/elixir), it seems like this tool makes it easy for developers to use Gulp.js. Though, the only drawback I forsee using Laravel Elixir is we can't further customize our build process and we will depend on Laravel Elixir's features.

Since I have a background with Front-End Development and I've growned accustomed to some front-end packages, I will be using my own [Front-End Workflow starterkit theme](https://github.com/rlynjb/frontendflow), instead re-installing NPM and Bower packages and redefining paths and build process in my Gulp.js file.


-----


# Coding templates to populating static data from JSON file

Below is a link to an a quick and simple overview of an MVC Application structure:

[Creating a Basic Laravel 5 MVC Application in 10 Minutes](https://selftaughtcoders.com/from-idea-to-launch/lesson-17/laravel-5-mvc-application-in-10-minutes/)

1. My method usually starts off with defining a route and creating a template file for that particular route.
2. Next is store sample data inside of JSON file and load file in a Controller
  - [Creating Static And Dynamic Web Pages In Laravel](http://vegibit.com/creating-static-and-dynamic-web-pages-in-laravel/)
  - [http://vegibit.com/json-in-laravel/](http://vegibit.com/json-in-laravel/)


> My rule is, if a website contains less than 15 or 20 items, keep it data static
> But, if items grow to 20 or more AND will contain a CRUD method, then proceed with Database.

-----


# From Static data to implementing a Database

Coming from a front-end web development and a bit of MVC background, Database concepts was new to me. Although I did dabbled a bit into sql queries, its still different from having the knowledge of Database tools available we can use in a Fullstack framework.

With Laravel, there are tools available that helps us manage our database. Features that came with Laravel are listed below with a bit of methodology when implementing a Database.

1. When we run `php artisan make:model User --migration` to create a Database, Laravel assumes you configured your database settings on `config/database.php` file. The generated Model and Migration script files are not aware of its configuration settings.


2. To create a Database, run `php artisan make:model User --migration` command. This will generate a **Eloquent ORM Model** and a **Migration** script.
  - **Eloquent ORM** - Model allows us to easily query and insert data in our tables.
  - **Migration** - Creates a Table; Builds our Database Schema; Preserves Database Schema, revision control


3. Seeding
  - is a way to create data fast. It populates data into a Database Table.
  * [https://sheepy85.wordpress.com/2014/09/19/database-seed-migration-in-laravel-5-0/](https://sheepy85.wordpress.com/2014/09/19/database-seed-migration-in-laravel-5-0/)
  * [http://www.fullstack4u.com/laravel/laravel-5-load-seed-data-from-json/](http://www.fullstack4u.com/laravel/laravel-5-load-seed-data-from-json/)


[Understanding Database with Laravel](https://www.youtube.com/watch?v=y0y3-m05Emc)


-----


# Simple Contact form, Sending emails

There are tons fo tutorials on the web about creating a conact form with Laravel but it doesn't seem to explain the basics. The link below though,

[Sending Emails](https://code.tutsplus.com/courses/get-started-with-laravel-5/lessons/sending-emails)

seem to explain the simplest and plainest method of how we can implement a Contact form in Laravel using Route `Route::get...` and Mail Facade `Mail::send...`.
From this tutorial, we can further build our Contact form to use Controller for code separation and gather User input from Views. We will be able to store Contact form data in database.

There are 2 ways to compose an email.

- Raw text
- From a View

<br>

### Raw Text

1. Create a Route where we can send emails from.
2. Define a Mail Facade and inside, define an instance of Illuminate Message to build mail properties.
3. Sign up for Mailtrap.io and configure `.env` file
4. Now, when we visit `/contact`, it should send test email defined inside of Mail facade.
5. Mail should be sent in Raw format located under Raw tab.

```
Route::get('/contact', function() {
  // define a Mail facade
  Mail::raw('kirby this is a test', function($message) {
    /*
      inside we will have an instance of
      Illuminate\Mail\Message

      inside of this closure, we can set other prooerties of email
    */
    $message->subject('testing')
            ->to('bill@mail.com')
            ->from('non@mail.com');
  });

  return 'email has been sent';
});
```

### From Views template

1. Define a Route again.
2. Instead of Mail Facade Raw `Mail::raw...`, we will use Mail Facade Send `Mail:send...`
3. Once URL is visited, it will send email to Mailtrap.io for test.
4. Mail should be sent in HTML format under HTML tab.

```
// this will get data from view or user input
Route::get('/contact/view', function() {

  //  param1 = path to view template
  //  param2 = array of data
  //  param3 = closure to setup message that we will be sending
  Mail::send('conact-view', ['name'=>'Bob'], function($message) {
    $message->subject('testing')
            ->to('bill@mail.com')
            ->from('non@mail.com');
  });
});
```


-----


# Intro to Create in CRUD

Below are the resources I used in learning basic CRUD, form handling in Laravel, and AJAX form post.

- [Forms and Data Validation](https://code.tutsplus.com/courses/get-started-with-laravel-5/lessons/handle-form-input)
- [Laravel 5 can't use ajax post request](https://laracasts.com/discuss/channels/requests/laravel-5-cant-use-ajax-post-request)
- [How to get All input of POST in Laravel 5](http://stackoverflow.com/questions/32718870/how-to-get-all-input-of-post-in-laravel-5)
- [Database: Getting Started](https://laravel.com/docs/5.4/database)

### Dealing with Global variables

- [Global variable in laravel controller](http://stackoverflow.com/questions/32942379/global-variable-in-laravel-controller)
- [Laravel 5 - global Blade view variable available in all templates](http://stackoverflow.com/questions/29715813/laravel-5-global-blade-view-variable-available-in-all-templates)

### Method for creating a Contact Form to storing to DB

1. Template Contact form
  - include validation (Zurb Foundation Abide or HTML5 validation)
  - include `name=""`, `maxlength=""` on input fields
  - include `{{ csrf_field() }}` before Submit input button
    - provided by Laravel, a secure way to manage POST forms
  - include a Thank You and Error messages
2. Author JavaScript submit ajax code
  - include `e.preventDefault();` to prevent page refresh
  - on Ajax, serialize data coming in from form
  - input url POST data in defined in routes
3. Define Routes
  - since we are posting, use POST instead of GET
  - ex: `Route::post('/contact/create', 'ContactController@create');` 
  - define url and Controller and its public function that will handle database form submission and other logic associated with create task.
4. Create Controller
  - on root directory, run `php artisan make:controller ContactController`
  - inside `ContactController.php`, define facades
    - ex: `use DB;`, `use Illuminate\Support\Facades\Mail;`
  - inside its public function
    - assign form input values to variables
      - these are the fields defined in form
    - write code to store on database, ref: [https://laravel.com/docs/5.4/database](https://laravel.com/docs/5.4/database)
    - write code to send data to email, ref: [https://laravel.com/docs/5.4/mail](https://laravel.com/docs/5.4/mail)
5. Setup database
  - go to phpmyadmin and create a database, enter credentials, and create a table
  - create columns and defined the ff.
    - form fields
    - include ID: int, auto_increment, primary
    - include submitted_at: timestamp, current_timestamp
  - on `.env` file, configure database settings
6. Setup Mailer
  - go to `.env` file and input settings
  - we are using [From Views Template](#from-views-template) code
  - using Mail facade requires additional steps
    - create a Requests by running `php artisan make:requests SendContact`
    - inside SendContact.php, input the ff.
      - set authorize to true
      - input fields on rules function
    - create a template under `resources/views/emails/contact.blade.php`
    - to test, we can use our email address temporarily

-----


# Defining my specs for a custom Admin Panel

My admin panel specs are:

- simple navigation (straightforward, simpler than wordpress)
- able to do CRUD unto json files
- contains just fields or forms (simple)
- display contact form data from contact form fields
- uses miminal text editor features with instructions
  - user will be using HTML tags
  - bold text
  - links
  - breakline/ new line
- image or assets uploader and manager
  - contains fields for seo input (img alt, title)


-----

# Building a CMS from scratch

- [Read-Write JSON file using PHP](http://www.kodecrash.com/javascript/read-write-json-file-using-php/)
- [Creating a SCRUD System Using jQuery, JSON and DataTables](https://www.sitepoint.com/creating-a-scrud-system-using-jquery-json-and-datatables/)


-----

# Method for developing a project from scratch

### Setting up a project

1. Setup Laravel, server, github repo, and configure FEF theme.


### Coding a theme with FEF Theme

[FEF Theme](https://github.com/rlynjb/frontendflow) is my baby project. It includes my front end workflow with css framework and javascript plugins I often used. It also includes a collection of solutions to common interaction and browser compatibility issues.

1. Code layout per page including UX.
  - place image placeholders and text.
  - determine responsiveness
  - determine user interaction of different components to be use
2. Code overall style, brand, typography
3. Add in basic CSS3 transitions


### Structuring Content with JSON

1. Per page, define fields and determine if its content type, regular page, form, etc.
2. Code fields into json file
3. Convert json files to be editable
  - modify Routing and Controllers
  - modify Views to use data passed from json to Controllers
