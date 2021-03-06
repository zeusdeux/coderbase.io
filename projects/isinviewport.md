---
title: Is In Viewport
permalink: isinviewport
description: An ultra-light jQuery plugin that tells you if an element is in the viewport but with a twist.
homepage: 
languages: [javascript]
visible: true
order: 1
# Github Flavored Markdown reference
# https://help.github.com/articles/github-flavored-markdown
---


isInViewport.js
================
[![Build Status](https://travis-ci.org/zeusdeux/isInViewport.svg?branch=dev)](https://travis-ci.org/zeusdeux/isInViewport)   
An ultra-light jQuery plugin that tells you if the element is in the viewport, but with a twist.
Did you say [demo](http://experiments.muditameta.com/isInViewport/)?

Current version: `2.0.0`
- Added support for negative `tolerance` values that are now relative to the `viewport` height
- Added support for custom viewport selector (see [Advanced usage](#advanced-usage))
- Removed support for the old usage syntax in favour of the `:in-viewport` selector i.e.,
```javascript
//removed
$( selector ).isInViewport( {"tolerance" :100, "debug": true} )

//current usage
$( 'selector:in-viewport( 100 )' )
```
- Removed the `debug` option because, lets be honest, no one really used it.
- Removed the weird code that handled *end of page* condition in the core. It's the user's 
prerogative to do what he/she wants when their page is scrolled to *end of page*.

Previous version: `1.1.1`
- Added `bower` support.

Previous version: `1.1.0`
- Added support for `:in-viewport` selector as per [joeframbach's](http://www.reddit.com/user/joeframbach) suggestion.

Installation
----------------
- Get the release that you want from [releases/tags](https://github.com/zeusdeux/isInViewport/releases) ( or `bower install isInViewport` )
-  Copy either `isInViewport.js` or `isInViewport.min.js` from the `lib` folder to your folder containing your scripts
- Add it after you include `jQuery`
- You're ready to go!

Usage
----------------
<a name="bu"/>
#### Basic usage

```javascript
$( 'selector:in-viewport' )
```
When used as a selector it returns all the elements that match. Since it returns the element(s) it can *thus be chained* with other jQuery methods. 

###### Example:
```javascript
$( 'div:in-viewport' ).css( 'background-color', 'red' );
```
This will set the `background-color` as `red` for all `divs` that are in the viewport.

#### Advanced usage

```javascript
$( 'selector:in-viewport( tolerance[, viewport selector] )' )
```
This returns all the elements that are in the viewport while taking into account the `tolerance` criterion.   
Since it returns the element(s) it can *thus be chained* with other jQuery methods.   
When a viewport selector is specified, it uses that to calculate if the element is in *that* viewport or not.   
When a viewport selector is *not* specified, it defaults to *window* as the viewport.   
The viewport selector is any valid jQuery selector.

###### Defaults:
- `tolerance` defaults to `0`
- `viewport` defaults to `window`

###### Example:
```javascript
//example 1
//the height of tolerance region is 100px from top of viewport
$( 'div:in-viewport( 100 )' ).css( 'background-color', 'red' );

//example 2
//the height of tolerance region is (viewport.height - 100px) from top of viewport
$( 'div:in-viewport( -100 )' ).css( 'background-color', 'green' );

//example 2
$('#viewport > div.box:in-viewport( 100, #viewport )').css( 'background-color', 'blue' )
                                                      .text( 'in viewport' );
```
__Example 1__ will set the `background-color` as `red` for all `divs` that are in the viewport with a `tolerance` of `100px`.   

__Example 2__ will set the `background-color` as `green` for all `divs` that are in the viewport with a `tolerance` of `viewport height - 100px`. This lets the user conveniently provide a `tolerance` value closer to the viewport height without having to call `$(viewport).height()` all the time.   

__Example 3__ will set the `background-color` as `blue` and `text` as `in viewport` for all `divs` that are in the custom viewport given by `#viewport` and with a `tolerance` of `100px`.

With the advanced usage it becomes very easy to build things like menus with items that get auto-highlighted based on which section you are on, transition effects when an element comes into the viewport, etc.

See the examples in the `examples` directory for more clarity.

###### Note:  
- When `tolerance` is `0` or `undefined` it is actually *equal to* `tolerance: $(viewport).height()` and *not* `0`.   
This makes it easier for developers to have the whole `viewport` available to them as a valid `viewport`.

## Support
__Chrome, Firefox 3.0+, IE6+, Safari 4.0+, Opera 10.0+__

## Note
- `:in-viewport` selector *does* support chaining.
- To use with IE < 9 use jQuery <= 1.7.0
