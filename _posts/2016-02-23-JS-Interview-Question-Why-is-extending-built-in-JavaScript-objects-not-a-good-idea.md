---
layout: post
title: "Why is extending built-in JavaScript objects not a good idea?"
date: 2016-02-23 13:04:54
tags:
- javascript
- interview question
---

From what I understand, extending built-in JavaScript objects is most likely an opinion-base rather than facts.
Before delving into its reasons why its not a good idea to extend built-in JS objects, I will tackle its purpose first to gain an understanding how it works and why its controversial.

-----

JS comes with essential built-in objects which we can utilize for text, numbers, boolean, data, dates, and much more. As we become familiar with these built-in objects, we'll find ourselves wanting to do more than what JS provides, that's where we create our custom built-in objects, hence, **_"Extending built-in JS objects"_**.

As an example, we can easily encapsulate our code using a function.

{% highlight javascript %}
function regexIt(input) {
  // do something with input and
  return input;
}
{% endhighlight %}

and use it by invoking `regexIt` function and passing in an argument, as shown below:

{% highlight javascript %}
var result = 'Hello World';
regexIt(result);
{% endhighlight %}

Now, let's say for instance, this function has become so useful that it should be part of JS String object methods. You know, how JS String has `replace()`, `indexOf()`, `slice()`, `substring()`, `toUpperCase()`, `toLowerCase()`, `split()`, just to name a few popular ones. We use these methods as shown below:

{% highlight javascript %}
var foo = 'Hello World, Foo Bar';
foo.split(',');
{% endhighlight %}

If we want our `regexIt` function to become a method of JS String object, meaning, to be able to use it like this, `foo.regexIt()` instead of `regexIt(foo)`, we'll need to use **prototype**.

-----

### prototype

`prototype` let's us insert our custom function to these JS Objects. All objects in JS contains a `prototype` property, even the variables we declare. Since we don't have access to the JS source code, thus, we cannot insert our custom functionality in `String` object by fiddling with JS source code, we use the `String` object's `prototype` as another approach to insert our functionality.

{% highlight javascript %}
String.prototype.regexIt = function() {
  /*
    Since were attaching our custom function to String object,
    we don't need an argument instead, we use 'this' to access our argument
    as it points to the String value attached.
  */
  var input = this;

  // do something with input and

  return input;
}
{% endhighlight %}

Now, we can use our `regexIt` method as shown below:

{% highlight javascript %}
var result = 'Hello World';
result.regexIt();
{% endhighlight %}

> This is because the prototype property provides you with direct access to your String's insides.
> Best of all, any new arrays you create will also have access to the shuffle functionality by default thanks to how prototype inheritance works.
> - kirupa

-----

### Controversials

We've seen how easy it is to extend a built-in object's functionality by declaring properties and methods, but there are contradictions to this practice.

- JavaScript may implement their own version of your custom method in the future (using the same name) and this will override your custom method.
- Modifying the behaviour of current built-in JS objects is not a good practice as it breaks its default functionality and it will break your code using that specific built-in JS object method or property.

When it comes down to extending a built-in JS object, it seems like you just use your best judgement. With given scenarios above, its easy to spot what should be avoided and what are the best approach to fix an issue.


-----

##### **References:**

- [Extending Built-In Objects in Javascript](https://www.kirupa.com/html5/extending_built_in_objects_javascript.htm)
