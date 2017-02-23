---
layout: post
title: "Front-End Design Specs"
date: 2016-07-28 10:58:40
tags:
- workflow
---

determing a workflow is hard but its even harder when we go through a laborious iterative process with designers.

since i have been using Zurb foundation, zurb foundation comes with a settings file that defines global variables for general design settings. This gave me the idea that responsive web design follows a certain pattern, same as Development.

process to determing on refining the design and developer workflow are:

- list down general design css properties
  * layout
    * max-width
    * number of columns grid
    * gutter width
      * small breakpoint
      * medium breakpoint

  * typography - header
    * header font
    * header font sizes
      * small breakpoint
      * medium breakpoint
    * header color
    * header alignment, leading, kerning
    * header opacity, filter
    * header font weight

  * typography - body
    * body font size
      * small breakpoint
      * medium breakpoint
    * body font color
    * body font family
    * body line height, leading, kerning
    * body font weight

  * spacing measurement
    * width and height
      * small breakpoint
      * medium breakpopint
      * large breakpoint
    * spacing bet object and canvas
    * spacing bet multiple objects
    * spacing bet text and objects

  * objects
    * fill color
    * stroke, color, size, style
    * opacity/filter
    * corner radius

  * color palette
    * primary, secondary, tertiary, quaternary
    * monotone
      * gray - light, medium, dark
      * black
      * white

after analyzing above data and visually looking at a design comp, these properties are already set on the provided design comp but not documented.

this is where PNG Express comes in, photoshop plugin tool.

after testing on a design comp and implementing it on theme development, it is indeed an ease for us developers.

so overview process would be:

- designer designs ui comp
- after design is complete, designer sets Design Specs with PNG Express
- pass the UI comp with design specs to front end developer
- front end developer implements these measurements on css styles sheets

* it does not need to be exact pixels, this is a good way to atleast get an estimate.

with this in set, this also gives Front end developers to compile a Style Guide and or components that can be resuable.

-----

##### **References:**

- [A Front-End Developer's Ode To Specifications](https://www.smashingmagazine.com/2014/10/front-end-development-ode-to-specifications/)
- [PNG Express](http://www.pngexpress.com/)
