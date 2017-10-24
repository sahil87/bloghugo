---
title: "Researching PNG Resizing"
date: 2017-10-24T13:33:58+05:30
author: Sahil Ahuja
tags: [ "png", "todo" ]
categories: [ "blog"]
---
A lot has been written about resizing PNGs and the comparison of different tools that allow it.

The following are my top picks:
<!--more-->

1. [pngquant](https://pngquant.org/) - fastest of the lot. Also has a node interface
1. [optipng](http://optipng.sourceforge.net/) - Changes PNG compression algo
1. [pngnq](http://pngnq.sourceforge.net/) - Reduces the colorspace used by the PNG image

If not using pngquant, the best result is by first using pngnq to reduce colorspace, and then using optipng to compress it further.

### ToDo

I want to integrate with the current PNG resizer into a on the fly url based resizer. We currently use [image resizer](https://github.com/jimmynicol/image-resizer) which is internally based on [sharp](https://github.com/lovell/sharp). The problem with sharp is that it doesn't work well with PNGs quality reduction.

Found a very [customizable resizer](https://github.com/aheckmann/gm) that can probably integrated with [pngquant](https://pngquant.org/) for on the fly PNG quality reduction.
