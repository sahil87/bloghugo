---
title: "Here is a way to Search Great Things through Google"
date: 2006-04-22T11:21:00+05:30
author: Sahil Ahuja
tags: [ "google" ]
categories: [ "blog" ]
---
I got it from [here](http://www.googletutor.com/2005/04/15/voyeur-heaven/).
<!--more-->

First of all, what’s an unprotected web directory? It’s one that does not have an “index” file created for it–index.htm, index.html, index.php or some other more rarely used file types. If you try to access a non-password controlled directory that does not have an index file, the system will build a listing of files that are within the directory. If you get that, you can then click on the files and run them with a viewer or player or even download them.

So, for starters here is a query that will give you a search results page of unprotected directories:

[-inurl(html|htm|php) intitle:”index of” +”last modified” +”parent directory” +description +size](http://www.google.com/search?hl=en&lr=&safe=off&c2coff=1&q=-inurl%28html%7Chtm%7Cphp%29+intitle%3A%E2%80%9Dindex+of%E2%80%9D+%2B%E2%80%9Dlast+modified%E2%80%9D+%2B%E2%80%9Dparent+directory%E2%80%9D+%2Bdescription+%2Bsize%5D&btnG=Search)

But, this is kind of boring. Too many unknown program files, text files, web pages etc. Let’s narrow it down. You can narrow it down by looking for something in the name of a file in the list, or by the file type, or both.

For example, this query tries to find any types of files about Jennifer Lopez. Within the directories I found music, image and movie files.

[-inurl(html|htm|php) intitle:”index of” +”last modified” +”parent directory” +description +size +”jennifer lopez”](http://www.google.com/search?hl=en&lr=&safe=off&c2coff=1&q=-inurl%3A%28htm+%7C+html+%7C+php%29+intitle%3A%22index+of%22+%2B%22last+modified%22+%2B%22parent+directory%22+%2Bdescription+%2Bsize+%2B%22jennifer+lopez%22&btnG=Search)

Let’s say that we wanted to find any movie files in WMV or AVI format:

[-inurl:(htm|html|php) intitle:”index of” +”last modified” +”parent directory” +description +size +(wmv|avi)](http://www.google.com/search?sourceid=mozclient&ie=utf-8&oe=utf-8&q=-inurl%3A%28htm%7Chtml%7Cphp%29+intitle%3A%E2%80%9Dindex+of%E2%80%9D+%2B%E2%80%9Dlast+modified%E2%80%9D+%2B%E2%80%9Dparent+directory%E2%80%9D+%2Bdescription+%2Bsize+%2B%28wmv%7Cavi%29)

You can get more specific by specifying both the file types and a search word to hopefully find in the name. For example, the following will attempt to find the infamous Paris Hilton video tape:

[-inurl:(htm|html|php) intitle:”index of” +”last modified” +”parent directory” +description +size +(wmv|avi) “paris hilton”](http://www.google.com/search?sourceid=mozclient&ie=utf-8&oe=utf-8&q=-inurl%3A%28htm%7Chtml%7Cphp%29+intitle%3A%E2%80%9Dindex+of%E2%80%9D+%2B%E2%80%9Dlast+modified%E2%80%9D+%2B%E2%80%9Dparent+directory%E2%80%9D+%2Bdescription+%2Bsize+%2B%28wmv%7Cavi%29+%22paris+hilton%22)

Or, you can even take a guess at the file name someone might call it:

[-inurl:(htm|html|php) intitle:”index of” +”last modified” +”parent directory” +description +size +(”paris_hilton.wmv”|”paris_hilton.avi”)](http://www.google.com/search?hl=en&lr=&safe=off&c2coff=1&q=-inurl%3A%28htm%7Chtml%7Cphp%29+intitle%3A%E2%80%9Dindex+of%E2%80%9D+%2B%E2%80%9Dlast+modified%E2%80%9D+%2B%E2%80%9Dparent+directory%E2%80%9D+%2Bdescription+%2Bsize++%2B%28%22paris_hilton.wmv%22%7C%22paris_hilton.avi%22%29&btnG=Search)

So there you go. You can combine various search terms and experiment with this. As you’ve seen, this is not an exact science. The directory pages you bring up may have many or even all files which are unrelated to what you are looking for. But, it does make some good hits very often.

`"parent directory "Xvid -xxx -html -htm -php -shtml -opendivx -md5 -md5sums`

