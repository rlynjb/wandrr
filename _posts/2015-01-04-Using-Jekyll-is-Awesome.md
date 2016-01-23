---
layout: post
title: "Using Jekyll is Awesome!"
date: 2015-01-04 10:47:13
tags:
- site static
- jekyll
---

hello world! welcome to the wonderful world of front end development! Using Jekyll has been an eye opening for me lately, discovering and learning new front end tools that I never knew exis ted! From Github pages to migrating from Wordpress to Jekyll, it has been wonderland for me. No more database, server stuff, and monthly payment for web hosting. Yey! and everything is pret ty much accessable through CLI interface :-)

I started learning Jekyll through its official site and documentation. [http://jekyllrb.com](http://jekyllrb.com)

Followed the Getting Started documentation and voila! I have Jekyll running on my local dev.

I then, migrated my wordpress blog posts, not by using jekyll plugin, but by manually creating a post in Markdown (.md) file format. I did it this way to atleast familiarize myself on getting around jekyll directory structure and its documentation.

After that, I’ve created its own Github repo, Github page, and pushed the files there.

I did ran unto a couple of issues with Github failed to generate a page due to some error.

For troubleshooting, it led me to this link:
[http://help.github.com/articles/using-jekyll-with-pages#troubleshooting](http://help.github.com/articles/using-jekyll-with-pages#troubleshooting)

-----

### Transferring Custom Domain to Github Page

After troubleshooting, next step was to redirect my domain from my old wordpress website to my new Github Jekyll page. :-D
The link below pretty much solved this issue.
https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages

Simply by creating a CNAME file unto the source directory of my jekyll website and typing my domain name.

Next, use dig command to retrieve the IP address of your github page (ex. -username-.github.io)

{% highlight javascript %}
dig -username.github.io- +nostats +nocomments +nocmd
{% endhighlight %}

And use it on your domain DNS Zone file by creating a A (Host) record type. Wait for acouple of minutes and voila! it should work!

-----

### Creating JSON api with Jekyll!

Now the fun part begins! I always wanted to create an api of my blog contents so I can use it on other projects I develop! and thought of using Jekyll as my CMS. I used wordpress before but since I want to develop myself as a Front End Developer, I want to avoid setting up and configuring server-side CMS, mysql databases and such and invest my time on focusing on front end to ols.

So with Jekylls’ templating system, it was really simple and elegant to create a .json file of my blog posts. Thanks to the Developmentseed.org team for this post. http://developmentseed.org/blog/2011/09/09/jekyll-github-pages/

You can find a detailed description of this method (also base from Developmentseed.org) through this link. https://alexpearce.me/2012/04/simple-jekyll-searching/

Moving on, on the source directory where the feed.xml resides, create a -whatevernameyouwant-.json file, in my case, it was blog.json.

Inside, I’ve typed:

{% highlight javascript %}
—-
—-
[
  {
    “site_title”: <% site.title | jsonify %>,
    “description”: <% site.description | jsonify %>,
    “site_url”: “<% site.url %><% site.baseurl %>/”
  },

  <% for post in site.posts %>
  {
    “title”: <% post.title | jsonify %>,
    “date”: <% post.date | date: “%a, %d %b %Y %H:%M:%S %z” | jsonify %>,
    “content”: <% post.content | jsonify %>,
    “link”: <% post.url | prepend: site.baseurl | prepend: site.url | jsonify %>
  },
  <% endfor %>

  null
]
{% endhighlight %}

The first and second line are empty YAML front matter. This is just to let Jekyll know that this is a Liquid Template and we can also use the Liquid Template filters and tags.

The first object contains site information and the second object are the posts wrapped in a template for loop tag. At the very end is a null, this is to avoid EOF (End of File) error when v alidating in http://jsonlint.com/, also Liquid Template Filters are also useful http://jekyllrb.com/docs/templates/ for cleaning up values and catch missing curly brackets, commas, and such .

After creating and cleaning your json file. on your CLI interface type:

{% highlight javascript %}
jekyll serve
{% endhighlight %}

it should give you a local address to where you can view your site locally or push to you github repo.
you should see your final result on -youraddress.com-/blog.json or again, in my case, its http://rlynb.com/blog.json

Soo all in all, it took me about 3 days to complete this the migration. Ran into some issues, but it really is just about googling it (lol) and research.
