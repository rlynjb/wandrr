---
layout: post
title: "Beginning Small Web App Development with AngularJS"
date: 2016-03-04 10:43:10
tags:
- javascript
- App Development
---

This is a continuation of my previous blog post [Beginning Mobile App Development Journey](/Beginning-mobile-app-development-journey/) as I further explore Hybrid (Mobile and Web) App Development. On my previous blog post, I have successfully installed PhoneGap and was able to run the default PhoneGap app on my Android phone.

For this blog post, I'm using AngularJS as my go-to JS Framework for prototyping, developing small apps, and testing with a Front-end framework: [Zurb Foundation for Apps](http://foundation.zurb.com/apps.html)

-----

### Why use Zurb Foundation for Apps? Why not build an app from scratch?

- To avoid spending time on developing the front-end architectural structure of directories and files.
- To avoid planning and coding front-end workflow and built process
- To avoid re-coding common JS components, such as Carousel, Modal, etc.
- To avoid re-coding CSS components, such as Grid system, consistent style of typography, buttons, utilities, etc.
- To produce a quick prototype to showcase to a prospect client.
- To further develop the prototype into a production app.

Above are reasons base on my personal opinion. There are different scenarios and situations why we use certain techonology and practice certain methodology. Each company comprise of their own development workflow that fits their business process and be able to produce product base on business requirements.

Following link is a solid and comprehensive response to a Quora question regarding which JavaScript Framework should we spend time learning which, I think also applies to how we approach a project: [I'm a bit lost in JavaScript framework hell. Should I spend time learning backbone.js or ember.js or can.js or angular.js?](https://www.quora.com/Im-a-bit-lost-in-JavaScript-framework-hell-Should-I-spend-time-learning-backbone-js-or-ember-js-or-can-js-or-angular-js/answer/Michael-Mullany-1?srid=Mz0n)

But if you are someone who is learning Front-End workflow, built process, and such concepts, I wouldn't recommend Zurb Foundation as it is an **automagic** framework, thus, preventing you from actual coding and structuring files. If given the time and resources, I honestly would still code in Vanilla JavaScript or choose a framework with less 'automagic' nature.

-----

### Details of AngularJS on Zurb Foundation for Apps

This blog post will only cover the AngularJS part of the framework. If you want to know how to setup and know more about the framework. Visit: [Zurb - Foundation for Apps](http://foundation.zurb.com/apps.html). Below are main AngularJS functionalities that Foundation as integrated unto their framework that comprise the basis of Web Application:

- [Dynamic Routing](#dynamic-routing)
  - [name, url, animationIn, animationOut, parent, controller, abstract](#yaml-front-matter-block)
- [Angular Includes](#angular-includes)
- [Enabling HTML5 Mode and working with Angular on a server](#enabling-html5-mode-and-working-with-angular-on-a-server)
- [Angular and UI Router Helpers](#angular-and-ui-router-helpers)
  - [ui-sref, ui-sref-active](#)

-----

## Dynamic Routing

These are the Views and State of a single-page apps. When approaching a project, initial step is we usually defined the url and template of an application. In Foundation for Apps - AngularJS, we approached this as follows:

Inside `clients > templates` directory is where we create our templates and define our routes and settings in YAML front matter block format.

{% highlight bash %}
# Foundation App directory structure

app
|-- bower_components
|-- build
|-- client
|   |-- assets
|   |-- templates # where we create our templates
|   |   |-- home.html
|   |-- index.html
|-- etc
|-- node_modules
|-- .bowerrc
|-- .gitignore
|-- bower.json
|-- gulpfile.js
|-- package.json
|-- readme.md
{% endhighlight %}

### YAML Front matter block

Settings inside template files.

{% highlight bash %}
# YAML Front matter block inside templates

---
name: parent.child
  # *required
  # The name of the view.
  # Refer to this when using ui-sref to link between views.
  # The name parameter can also use ui-router's dot notation to indicate a child view.
url: /child/:id
  # *required
  # Defines the URL at which a page can be directly accessed.
  # When setting up a child view, don't include the segment of the URL for the parent view—it will be inserted automatically.
  # In the above example, the final URL is /parent/child, assuming the URL of the parent view is /parent.
  # A URL can also contain parameters, which will be passed to the view's controller when it loads.
  # Learn more about URL parameters on ui-router's documentation.
  # https://github.com/angular-ui/ui-router/wiki/URL-Routing#url-parameters
animationIn: fadeIn
  # Sets a transition to play when the view animates in.
  # Refer to the Motion UI documentation to see the list of built-in transitions.
  # http://foundation.zurb.com/apps/docs/#!/motion-ui
animationOut: fadeOut
  # Sets a transition to play when the view animates out.
parent: name_of_parent_view
  # Defines the parent view for the current one.
  # You can use this as an alternative to the parent.child syntax.
controller: NameOfController
  # By default, all views use a controller called DefaultController, but this can be changed.
  # continue below
abstract: true_or_false
  # Defines a state as abstract. Abstract states can have child states, but can't be navigated to directly.
  # Check out the ui-router documentation to learn more.
  # https://github.com/angular-ui/ui-router/wiki/Nested-States-%26-Nested-Views#abstract-states
---
{% endhighlight %}

**controller**<br>
Among other things, the default controller passes a bunch of data through. For instance, all of your front-matter settings will be accessible via `vars` in your template. `angular` will return the name of your route while `templates/angular.html` will return the relative path to the template.

Note that override a controller disables front-matter settings (except dynamic routing). If you want to use your own controller AND keep this feature, you can extend the `DefaultController`:

{% highlight javascript %}
angular.module('application')
  .controller('MyController', MyController)
;

MyController.$inject = ['$scope', '$stateParams', '$state', '$controller'];

function MyController($scope, $stateParams, $state, $controller) {
  angular.extend(this, $controller('DefaultController', {$scope: $scope, $stateParams: $stateParams, $state: $state}));
  // Your code...
}
{% endhighlight %}

-----

## Angular Includes

If a template becomes complex, we can break it further into **partial** templates and use **Angular Includes** - `ng-includes` to inject into its parent template.
The use of single quotes inside the double quotes is **required**. The HTML inside the partial will be placed inside the element with `ng-include`.

{% highlight html %}
<div ng-include="'path/to/partial.html'"></div>
{% endhighlight %}

-----

## Angular and UI Router Helpers

-----

##### **Further reading**

- [Best books for AngularJS](http://www.fromdev.com/2015/06/best-books-for-angularjs.html)
- [Frontend Architecture for Design Systems By Micah Godbolt](http://shop.oreilly.com/product/0636920040156.do)
