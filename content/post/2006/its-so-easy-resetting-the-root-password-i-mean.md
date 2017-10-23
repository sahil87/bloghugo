---
title: It's so easy!!! (Resetting the root password I mean)...
author: Sahil Ahuja
categories: [blog]
tags:
  - reset
  - root
date: 2006-07-10 03:01:00
---

<span style="font-size:130%;">Look at this from  [Fedora FAQ](http://www.fedorafaq.org/basics/) -</span>
> <span style="font-size:85%;">Q:How do I reset my root password? </span>
> 
> <div><span style="font-size:85%;">A: If you've forgotten your root password, and you want to change it, don't worry!  It's possible. You need to boot into what's called "single-user  mode." You must be _in front of the computer_ to do this --  you _can not_ do it remotely: </span>
> 
> 
> 1.  <span style="font-size:85%;">Using the instructions in the [runlevel question](http://www.fedorafaq.org/basics/#runlevel) (under the "While You Are Booting the      Computer" section), boot into runlevel 1.</span>
> 2.  <span style="font-size:85%;">Set the new root password with by typing: </span><span style="font-size:85%;">passwd</span>
> 
> 
> <span style="font-size:85%;">And then enter your new root password when asked.</span>
> 3.  <span style="font-size:85%;">Reboot your machine, and you will now be able to log in as root with      the new password that you entered.</span>
> 
> </div>
<span style="font-size:130%;">And here's that runlevel question -</span>**
**
> <li><span style="font-size:78%;">**While You Are Booting the Computer**: </span>
> 
> 
> 1.  <span style="font-size:78%;">When you first start your computer, the GRUB screen (where you         choose your Operating System) appears. Select the Fedora that          you want to boot into, but press the <kbd>a</kbd> key instead of          pressing <kbd>Enter</kbd>.</span>
> 2.  <span style="font-size:78%;">You will see a line somewhat like the following: </span><span style="font-size:78%;">kernel /vmlinuz-2.6.9-1.667 ro            root=LABEL=/ acpi=on rhgb quiet</span>
> 
> 
> <span style="font-size:78%;">Add the number of your runlevel to the end of that line, and then           press <kbd>Enter</kbd>. For example, to boot into text-only mode,           the line would look like:</span>
> 
> 
> <span style="font-size:78%;">kernel /vmlinuz-2.6.9-1.667 ro           root=LABEL=/ acpi=on rhgb quiet 3</span>
> 
> <span style="font-size:78%;">You will then boot into the new runlevel this time only.</span></li>
<span style="font-size:130%;">This just shows how easy it is hack into our systems unless we [secure our grub](http://wiki.linuxquestions.org/wiki/Securing_GRUB)</span>!