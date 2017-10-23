---
title: Installing xgnokii for n-gage (in Fedora Core 5)
author: Sahil Ahuja
categories: [blog]
tags:
  - gnokii
  - nokia
date: 2006-07-09 07:58:00
---

There's no nice guide for this!! So, I made one for myself.
I own  a Nokia N-Gage RH-29 (The one for Asia ... or something like that). Now, I refuse to use windows for seeing all my contacts on the computer. But for using the tool for linux (xgnokii) for Nokia phone doesn't work right away for Nokia N-Gage.

Here is how to make it work -

1.  Install gnokii and xgnokii - "yum install gnokii xgnokii".
2.  Follow instructions in the [xgnooki wiki](http://wiki.gnokii.org/index.php/Serie60Config) <span style="font-weight:bold;">with the modifications in steps 3 and 4</span>.
3.  For installing the gnapplet.sis in N-Gage (and Nokia 6600), you have to get the one in [here](http://marc.theaimsgroup.com/?l=gnokii-users&amp;m=109389464621857&amp;w=2). And in gnapplet.ini file, you have to set irda_support = 0\. For that copy the file to computer (through memory card reader or any other way), edit it (change 1 to 0 against irda_support), and copy it back to phone's memory.
4.  Now here's the tricky part - if you use the bluetooth dongle like me for bluetooth connection (or even otherwise), how do you find the bluetooth address for that device ? Here's how - 1) Plug the device in. 2) login console as root (su) and type "hcitool inq". The bluetooth address must be displayed in console.
5.  Start xgnokii as root ("su";"xgnooki &amp;").... and then the app starts.