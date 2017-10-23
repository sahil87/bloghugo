---
title: GPL Hijacking
author: Sahil Ahuja
categories: [pcbo]
tags:
  - gpl
  - open source
date: 2006-06-25 09:17:00
---

LGPL looked like the obvious choice for PCBO when the following problem cropped up - [GPL Hijacking](http://curl.haxx.se/mail/lib-2000-11/0004.html).

*   LGPL doesn't spread to other parts of an application and it does allow being linked with closed-source programs. LGPL is "compatible" with GPL in the sense that you can, at your option, convert a LGPLed program to a GPL one any time you want. Such a change is irreversible. For a small project, this is a risk. If a truly skilled person adds a lot of functionality and relicenses the code to GPL, the LGPLed one would swiftly be abandoned and the GPL-changes cannot be applied back in the LGPL version.

*   Where lies this license problem? MPL itself has no problems with the LGPL or GPL licenses, the problem is on the GNU side. GPL has a problem with MPL.