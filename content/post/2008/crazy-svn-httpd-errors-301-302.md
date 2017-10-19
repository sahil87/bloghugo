---
title: 'CrAzY SVN / HTTPD Errors!!! (301, 302 .....)'
author: Sahil Ahuja
categories: [nitt]
tags:
  - errors
  - httpd
  - svn
id: 39
date: 2008-05-11 14:47:18
---

Yup.

SVN IS MAD.

Sorry, SVN and HTTPD team up to drive people crazy.

I just came across two (or maybe three) of their misdoing in my effort to setup SVN on http://repos.nitt.edu

1) First, with this nitt.edu.conf in /etc/httpd/conf.d directory :
```
<VirtualHost *:80>
    ServerName                          repos.nitt.edu
    DocumentRoot            "/var/www/html"</pre>
I got an error
<pre><span style="color:#ff0000;">RA layer request failed
svn: PROPFIND request failed on '/pragyan'
svn: PROPFIND of '/pragyan': 302 Found (http://repos.nitt.edu)</span>
```
I found this article : [http://ynniv.com/blog/2005/12/troubling-svn-error.html](http://ynniv.com/blog/2005/12/troubling-svn-error.html)

It said that the error occurs when some cms meddles with the way non existent file message (404) is shown. This,... was my case. (Thanks to my [Praygan CMS](http://pragyan.sf.net)). So then I changed my document root to /var/www/svn.

Then with
```
<VirtualHost *:80>
ServerName                          repos.nitt.edu
DocumentRoot            "/var/www/svn"</pre>
I got an error
<pre><span style="color:#ff0000;">RA layer request failed
svn: PROPFIND request failed on '/pragyan'
svn: PROPFIND of '/pragyan': 301 Moved Permanently (http://repos.nitt.edu)
</span>
```
Article that helped me in this grave time of need was : [http://subversion.tigris.org/faq.html#http-301-error](http://subversion.tigris.org/faq.html#http-301-error)

It said that the error occurs because, when configuring SVN to work with httpd, the virtualhost document root shouldn't contain the repository location (or httpd gets confused or something). My repos location was /var/www/svn/pragyan (which was within Document root). I simply changed the DocumentRoot to /var/www/svn/DocumentRoot and all started working well again.