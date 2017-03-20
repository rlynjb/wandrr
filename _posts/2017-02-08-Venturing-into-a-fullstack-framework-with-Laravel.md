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
- [Intro to Create in CRUD](#intro-to-create-in-crud)
  - [Method for creating a contact form to storing in db](#method-for-creating-a-contact-form-to-storing-to-db)
    - ref: [Simple Contact form, Sending Emails](#simple-contact-form-sending-emails)
  - [Method for converting static data in template to JSON object value](#method-for-converting-static-data-in-template-to-json-object-value)
    - ref: [Coding templates to populating static data from JSON file](#coding-templates-to-populating-static-data-from-json-file)
    - ref: [From Static data to implementing a Database](#from-static-data-to-implementing-a-database)
  - Method for building Complete CRUD
- User Authentication and Roles
  - [Method for enabling user registration, login, and authentication](#method-for-enabling-user-registration-login-and-authentication)
  - Setting up User Roles and Permissions
  - Using User Roles in Controllers and Templates
  - Using User Roles in Middleware
  - [Intro to Middleware](#intro-to-middleware)
  - [Method for creating your own Middleware](#method-for-creating-your-own-middleware)
- CRUD Editor, plans, misc.
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

-----

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
7. Implement google recaptcha
  - retrieve site and secret key
  - load grecaptcha plugin and html tag
  - author validation google recaptcha code on contact form submit event
    - ref: [http://stackoverflow.com/questions/37294886/google-recaptcha-with-ajax-form](http://stackoverflow.com/questions/37294886/google-recaptcha-with-ajax-form)

```
if (grecaptcha.getResponse().length > 0) {
  ajax call
else {
  $('.recaptcha-response').append('Check recaptcha before submmitting form');
}
```


-----

### Method for converting static data in template to JSON object value

1. After templating
  - structure your JSON data with a template file values
  - use [http://jsoneditoronline.org](http://jsoneditoronline.org)
  - store file in `database/data/nameoffile.json`
2. Create a Controller
  - run `php artisan make:controller HomeController`
  - define public function to contain logic for displaying data from JSON file
  - write code to load JSON file and loop through JSON value
  - and define template at the bottom along with passing `$data` from looped json file
3. Define Controller in Route
  - replace define function in route to point to controller and its public function
4. In HomeController, define variables and assign value for JSON file
5. replace static data in templates to use variable from its controller
6. Handle Exceptions
  - [https://scotch.io/tutorials/creating-a-laravel-404-page-using-custom-exception-handlers](https://scotch.io/tutorials/creating-a-laravel-404-page-using-custom-exception-handlers)

-----


### Method for enabling User registration, login, and authentication

1. Make sure you have configured and have access to Database
2. Run `php artisan migrate` to setup database tables and its columns
  - this takes the script inside and creates database table and its columns in DB
    - ref: [Laravel Database: Migration](https://laravel.com/docs/5.4/migrations)
  - make sure you use PHP 7 on server-level rather than virtual (directory) level
  - while running command, i came across an issue
    - ref: [laravel 5.4 key too long issue](https://laravel-news.com/laravel-5-4-key-too-long-error)
  - idea: we can write our own database table migration script whenever we need to integrate a db into our forms
3. Run `php artisan make:auth`
  - controllers are automatically provided by Laravel
  - this will generate the ff. files for authentication
  - warning: this will overwrite your `HomeController`, `home.blade.php`, `layouts > app.blade.php`, and `layouts > footer.blade.php`
  - its best to run this command at the beginning of project or backup your code on github
4. Compare Auth generated template files to your original login system files
  - make the necessary changes (modify templates and mv to `/auth`)
  - there are if statements that Authentication may require
  - make sure they are synced in
    - display data for guest users
    - display data for logged in users
5. Redirect guest users to your own homepage display instead of Authentication's default login page
  - if were using all endpoints (`login`, `logout`, `register`, `password email`, `password request`, `password reset`), no need to remove `Route::auth` from `routes.php` file.
  - Remove `Route::auth()` from `routes.php` and manually declare endpoints
    - ref: [http://robboyland.com/laravel-auth-how-to-disable-registration](http://robboyland.com/laravel-auth-how-to-disable-registration)
    - ex. `Route::get('login', 'Auth\AuthController@showLoginForm');`
    - to display Route list, run `php artisan route:list`
  - Remove `Route::get('/home', 'HomeController@index');` from `routes.php` file
  - Remove `$this->middleware('auth');` on `app > Http > Controllers > HomeController.php` file
6. after login success, set redirection page
  - change path `protected $redirectTo = '/home'` in `app/Http/Controller/Auth`
  - ref: [login registration redirect fix](http://www.easylaravelbook.com/blog/2015/03/11/changing-the-laravel-redirect-location-after-login/)
  - same method goes with after Registration page
7. Add custom fields to Registration Form
  - ref: [Adding Custom Fields to a Laravel 5 Registration Form](http://www.easylaravelbook.com/blog/2015/09/25/adding-custom-fields-to-a-laravel-5-registration-form/)
8. Transfer old registration controller code logic to the new Auth registration controller
9. Protect private data or elements in templates from public view

```
@if ( Auth::guest() )
  // html elements or data here
@else
  // html elements or data here
@endif
```

**Next is to setup Middleware**

- [How to send mail after Laravel 5 default registration?](http://stackoverflow.com/questions/29173028/how-to-send-mail-after-laravel-5-default-registration)
- video ref: [https://www.youtube.com/watch?v=bqkt6eSsRZs](https://www.youtube.com/watch?v=bqkt6eSsRZs)


-----

### Intro to Middleware

Middleware is a way of protecting routes or running code before and after a route is run.

Defining Middleware in routes is ok, but since we are going to reuse this type of authentication, we need to transfer this code from route to a middleware or use a pre-existing Laravel Middleware.

```
Route::get('home', function () {
  if ( Auth::guest() ) {
    return Redirect::to('auth/login');
  } else {
    echo 'Welcome home ' . Auth::user()->email . '.';
  }
});
```

Middlewares can be seen at `app > Http > Middleware > Authenticate.php`

To Check which Middleware class to use `app > Http > Middleware > Kernel.php`

In `Route.php`, Middleware can be define as:

```
Route::get('home', ['middleware' => 'auth', function() {
  echo 'Welcome home ' . Auth::user()->email . '.';
}]);
```

video ref: [https://www.youtube.com/watch?v=bWhJJJwMvco](https://www.youtube.com/watch?v=bWhJJJwMvco)

doc ref: [Laravel Doc Middleware](https://laravel.com/docs/5.4/middleware)

-----

### Method for creating your own Middleware

We can create our own Middleware. ex would be Role Permissions

1. Run `php artisan make:middleware Admin`
  - this generates `app > Http > Middleware > Admin.php`
2. Since we are going to use the same Authenticate Middleware
  - Copy and Paste the ff. section of code from `app > Http > Middleware > Authenticate.php` at the beginning of Admin PHP class file.
    - `The Guard implementation`
    - `Create a new filter instance`
  - Copy and paste `use Illuminate\Contracts\Auth\Guard;`
  - Copy and paste code inside handle function
3. Write code at the 2nd ifelse statement
4. Route new Middleware in `app > Http > Kernal.php` by copy and pasting path below

```
protected $routeMiddleware = [
  'auth' => \App\Http\Middleware\Authenticate::class,

  'admin' => \App\Http\Middleware\Admin::class,
];
```

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
