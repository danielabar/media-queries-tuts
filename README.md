CSS Media Queries Inside Out
==========

> Learning CSS Media Queries with Tuts Plus [course](http://webdesign.tutsplus.com/courses/media-queries-inside-out).

__Table of Contents__
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
- [CSS Media Queries Inside Out](#css-media-queries-inside-out)
  - [What are Media Queries?](#what-are-media-queries)
  - [Viewport Width](#viewport-width)
  - [Simplifying Designs for print](#simplifying-designs-for-print)
  - [HTML and CSS Media Queries](#html-and-css-media-queries)
  - [Max Width Media Queries](#max-width-media-queries)
  - [Resizing Content Based on Width](#resizing-content-based-on-width)
  - [Styling the Menu](#styling-the-menu)
  - [Creating a Menu Button](#creating-a-menu-button)
  - [Making the Menu Animate](#making-the-menu-animate)
  - [Logical Operators](#logical-operators)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## What are Media Queries?

CSS extension that allows for limiting the scope of styles.
Prior to 2010, media queries were primarily used to provide printer friendly versions of websites
by specifying completely different stylesheets that affected the printed page.

[2010 article](http://alistapart.com/article/responsive-web-design) introducing concept of _responsive web design_.

[W3C Media Queries Recommendation](http://www.w3.org/TR/css3-mediaqueries/)

## Viewport Width

[HTML](site01/index.html) | [CSS](site01/css/styles.css)

[Details](http://webdesign.tutsplus.com/articles/quick-tip-dont-forget-the-viewport-meta-tag--webdesign-5972)

Must have `viewport` metatag in the head section of document.

For example, to set the width of the content to the width of the device that it's being viewed on.
Otherwise mobile browsers may set the content width to wider than the device itself, causing horizontal scrolling.

```
<meta name="viewport" content="width=device-width, initial-scale=1">
```

Setting initial-scale to 1 makes it zoom out to 100%.

## Simplifying Designs for print

[HTML](site02/index.html) | [Print CSS](site02/css/print.css)

For example, when printing page, just show essential information, don't need navigation and advertisement.

To hide elements, for example navigation:

```
<nav class="main-menu">
  <ul>
    <li><a class="active" href="#">Home</a></li>
    ... menu items
  </ul>
</nav>
```

```css
.main-menu {
  display: none;
}
```

To make up the `print.css` stylesheet apply _only_ when the document is being printed,
use an html media query in the document head, specifying `print` as the _media type_.

```
<link rel="stylesheet" href="css/print.css" media="print">
```

Note that the main stylesheet defined just before is still applied.
Use `print.css` to _override_ styles that should be modified for printing.

## HTML and CSS Media Queries

[HTML](site03/index.html) | [CSS](site03/css/styles.css)

An alternative to media query in html, can specify it in the css file, for example, print styles:

```css
@media print {

  header h1 {
    background-color: transparent;
    color: #000;
  }

  .main-menu,
  .advertisement {
    display: none;
  }

}
```

One more way to specify media queries is with css `@import`, for example:

```css
@import url("print.css") print;
```

## Max Width Media Queries

[HTML](site04/index.html) | [CSS](site04/css/styles.css)

How to decide on breakpoints? Should be determined by _content_, so that content looks good at all sizes.

Media types are like `screen` or `print`, where styles contained in these will only be applied for that particular media type.

In this case, we're going to use a _media feature_, which works based on the browser's attributes.
For example, at maximum width of 960px, want layout to change.

Media features are defined in parentheses and look like css attributes.
For example, to change the appearance of the `container` class when the browser width is <= 960 px:

```css
@media (max-width: 960px) {

  .container {
    background-color: red;
  }

}
```

Styles in media queries _override_ properties set outside of the media queries.

## Resizing Content Based on Width

[HTML](site05/index.html) | [CSS](site05/css/styles.css)

For example, given a site with main content and side bar laid out in 960px wide container:

```css
.container { width: 960px; }
.main-content, .sidebar { float: left; }
.main-content { width: 600px; }
.sidebar { width: 300px; }
```

To adjust layout at browser width <= 960px:

```css
@media (max-width: 960px) {

  .container {
    width: auto; /* Otherwise fixed width of 960px overrides max-width */
    max-width: 800px;
  }

  /* Use percentages to have content automatically resize */
  .main-content {
    width: 67%;
  }

  .sidebar {
    width: 33%;
  }

  /* Make otherwise fixed width image also resize */
  .advertisement img {
    width: 100%;
  }

}
```

## Styling the Menu

[HTML](site06/index.html) | [CSS](site06/css/styles.css)

Make the text based menu disappear at smaller screen widths, and replace with bar that says the word "menu",
and have it animate in and out. Can be done mostly with css, and a little bit of JavaScript (will do in next lesson).

To have the main menu be fixed at the top left of the screen for smaller widths, set its position to fixed.
Also completely change the look of the menu to be vertical, different text and background colors etc.

```css
@media (max-width: 500px) {

  .main-menu {
    position: fixed;
    top: 0;
    left: 0;
    height: 100%;
    background-color: #999;
    width: 200px;
    border: none;
    margin: 0;
    margin-bottom: 0;
    padding: 10px;
  }

  .main-menu ul {
    margin: 0;
    margin-top: 20px;
  }

  .main-menu ul li {
    float: none;
    margin-right: 0;
    margin-bottom: 20px;
  }

  .main-menu ul li a {
    color: #fff;
  }

  .main-menu ul li a.active {
    color: #000;
  }

}
```

## Creating a Menu Button

[HTML](site07/index.html) | [CSS](site07/css/styles.css)

Start by making the text based menu "disappear" at smaller widths.

```css
@media (max-width: 500px) {

  .main-menu {
    /* ... other styles */
    margin-left: -100%;
  }

}
```

Then make add an activation control in the html that will make the menu appear.

```
<nav class="small-menu"><span class="nav-activate">+Menu</span></nav>
```

This control should only be visible on smaller widths and hidden in the default styles:

```css
nav.small-menu {
  display:none;
}

@media (max-width: 500px) {

  /* ... other styles */

  nav.small-menu {
    display: block;
    /* ... other small menu styles */
  }

}
```

## Making the Menu Animate

[HTML](site08/index.html) | [CSS](site08/css/styles.css) | [JS](site08/js/app.js)

At small widths, when menu button is clicked on, want to make the (hidden) vertical menu slide in.

Start by adding [jQuery CDN](http://jquery.com/download/) to html.

Then make the control (added in previous lesson) clickable:

```css
.nav-activte {
  cursor: pointer
}
```

Next add some JavaScript (with jQuery) to toggle an `active` class on the `body` element whenever the control is clicked

```javascript
$('.nav-activate').click(function() {
  $('body').toggleClass('active');
});
```

Finally, add css `transition` to small menu, and set `margin-left` to 0 when `body` has `active` class

```css
@media (max-width: 500px) {

  .main-menu {
    transition: .5s margin-left ease;
  }

  body.active .main-menu {
    margin-left: 0;
  }

}
```

## Logical Operators

So far all the media queries we've created have matched only one criteria.

Logical operators (and, or, not, only) can be used to create more complex media queries.
For example, this would only apply for `screen` _and_ browser width >= 500px

```css
@media screen and (min-width: 500px) {
  /* styles here... */
}
```

There is no "or" operator, but the same effect can be achieved using ",".
for example, apply to `screen` or `print` or browser widht >= 500px

```css
@media screen, print, (min-width: 500px) {
  /* styles here... */
}
```

`not` takes the opposite, for example, this will apply to anything that is not `screen`.

```css
@media not screen {
  /* styles here... */
}
```

`not` is generally the _last_ thing that's evaluated.
For example, first evaluate if its `print` and browser width >=500px,
then apply the `not` of that. If that results in true, then styles would be applied.

```css
@media not print and (min-width: 500px) {
  /* styles here... */
}
```

Exception to `not` rule above is if "or" (i.e. comma) is used.
For example, `not` only applies to `print` and min-width: 500px, and the max-width is considered a separate media query.

```css
@media not print and (min-width: 500px), (max-width: 700px) {
  /* styles here... */
}
```

`only` logical operator provides safeguard for older browsers that might not be compatible with media queries.
If older browser sees `only`, will ignore this media query.

```css
@media only screen {
  /* styles here... */
}
```
