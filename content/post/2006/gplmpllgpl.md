---
title: GPL/MPL/LGPL
author: Sahil Ahuja
categories: [pcbo]
tags:
  - gpl
  - opensource
date: 2006-06-25 07:57:00
---

I was trying to decide which license to use for my [PCBO](http://pcbasedoscilloscope.blogspot.com).

So I had to do a bit of research on the usable licenses. These two sites were very helpful -

*   [http://en.wikipedia.org/wiki/Open-source_license](http://www.blogger.com/img/gl.link.gif)
*   [http://www.opensource.org/licenses/](http://www.opensource.org/licenses/)
<span style="font-size:130%;">Basically [<span style="font-weight:bold;">GPL</span>](http://en.wikipedia.org/wiki/GNU_General_Public_License) is like a virus</span>.
All derived and any larger work of which a GPL code is part of, must be open sourced and licensed under GPL.

But this imposes a lot of restriction on libraries like glibc which are used in almost every project. <span style="font-size:130%;">
So, the [<span style="font-weight:bold;">LGPL</span>](http://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License) (Library or Lesser GPL) was deviced which allows the LGPLed code to be </span><span style="font-style:italic;font-size:130%;">linked</span><span style="font-size:130%;"> by a non-(L)GPLed program</span>. The LGPL places copyleft restrictions on the program itself but does not apply these restrictions to other software that merely links with the program.

<span style="font-size:130%;">The [<span style="font-weight:bold;">MPL</span>](http://en.wikipedia.org/wiki/Mozilla_Public_License) states that derived may not be under MPL </span><span style="font-style:italic;font-size:130%;">but </span><span style="font-size:130%;">must contain a documentation of all the changes made</span>.
Here is a [link](http://www.croftsoft.com/library/tutorials/gplmpl/) to a great discussion about the differences of GPL and MPL.

Under a [<span style="font-style:italic;">copyleft</span>](http://en.wikipedia.org/wiki/Copyleft) form of copyright license, the restrictions imposed are that the work cannot be copied, modified or used in any subsequent work unless the author of that subsequent work agrees to grant the same copyleft rights to the public to freely copy, use and modify the subsequent work. There are [two types](http://en.wikipedia.org/wiki/Copyleft#Strong_and_weak_copyleft) of copylefts -

1.  Strong copyleft : Which implies derived works of all kind has to have the same copyleft rights. Example is GPL.
2.  Weak copyleft : Allows other software to link to the library, and then be redistributed without the legal requirement for the work to be distributed under the library's copyleft license. Examples are MPL and LGPL.
Then there's also the [<span style="font-weight:bold;">Apache License</span>](http://en.wikipedia.org/wiki/Apache_license) which states that all derived work must contain text messages indicating that a work under apache is being used. But PCBO is not <span style="font-style:italic;">derived</span> from apache or tomcat. It runs on them.