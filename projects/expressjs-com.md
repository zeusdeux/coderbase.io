---
title: Expressjs.Com
permalink: expressjs-com
description: the expressjs.com website
homepage: 
languages: [javascript]
visible: false
order: 10
# Github Flavored Markdown reference
# https://help.github.com/articles/github-flavored-markdown
---


# ExpressJS.com

  The site for Express.

## Building

Setup:

```
$ npm install -g serve
$ npm install
$ make
$ serve . &
$ open http://localhost:3000
```

then rebuild changes with:

```
$ make
```

## Contributing

  - __don't__ edit the HTML directly, edit the _jade_.
  - don't commit any HTML changes, __only jade changes__.

## Showcasing

If you have an app you'd like to showcase on the express site,
do not just open an issue for it.
Instead, _open a pull request_ for it.
