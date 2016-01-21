---
layout: post
title: "Responsive Email"
date: 2015-01-04 10:47:13
tags: css responsive email
---

I’ve been working on this new project, Creating Responsive Emails, and I thought of blogging my experience and sharing them to you! ☺..

I first found out about Responsive Email through this website, http://www.zurb.com/playground/responsive-email-templates. They offer pre-made html email templates ready for you to use. My experience using these templates is that they aren’t really compatible with most of the email web clients with older browser versions.

I used http://emailonacid.com/ to test these templates. It works on most mobile devices, but doesn’t on most web desktop clients except for apple mails, outlook express, and live mail.

I did more research and found this, http://www.campaignmonitor.com/guides/mobile/. Instead of using div tags and floats, we can actually use tables and its attributes.

Coding email templates for browser and email client compatibility issues was a trial and error experience. Bugs occur more on email web client with older browser version than on mobile devices. I’m surprise Gmail had more bugs than yahoo mail and aol.

I ended up coding my own Responsive Email layout template by using:

-----

### Table tags instead of Div tags
- CSS properties: max-width, width
- Table attributes: align=”left”, width=”400px” instead of floats
- cellspacing and cellpadding instead of margin and padding

-----

#### Also, here are some tips I found from campaignmonitor.com on coding html for emails.

- Set width in cell instead of relying on table. Use pixel instead or percentage.Use cellpadding parameter when setting padding for cells instead of using CSS padding.
- Nest tables inside your table. ☺
- set a background color on the container table, do not set it on body tag because some email clients ignore them.
- remove any whitespace
- use inline css or css inliner for repeated tags
- for images, always use alt attributes
- use captions for important images

-----

### refer to this link for css support 

- [campaignmonitor.com/css](http://www.campaignmonitor.com/css/)
- [campaignmonitor.com/guides](http://www.campaignmonitor.com/guides/)
- [putsmail.com](http://putsmail.com/)
- [beaker.mailchimp.com](http://beaker.mailchimp.com/inline-css)
