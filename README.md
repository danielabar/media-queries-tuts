<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [CSS Media Queries Inside Out](#css-media-queries-inside-out)
  - [What are Media Queries?](#what-are-media-queries)
  - [Viewport Width](#viewport-width)
  - [Simplifying Designs for print](#simplifying-designs-for-print)
  - [HTML and CSS Media Queries](#html-and-css-media-queries)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

CSS Media Queries Inside Out
==========

> Learning CSS Media Queries with Tuts Plus [course](http://webdesign.tutsplus.com/courses/media-queries-inside-out).

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
