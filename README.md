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

[HTML](site02/index.html) | [CSS](site02/css/styles.css)
