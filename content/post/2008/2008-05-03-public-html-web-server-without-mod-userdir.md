---
title: public_html web server - without mod_userdir
author: Sahil Ahuja
categories: nitt
tags:
  - httpd
id: 30
date: 2008-05-03 08:59:43
---

Hell, what does the title mean??

It means this :

Allow people to put files in the public_html folder in their home directories and allow it to be seen through the web server of that server in this format : http://servername/~username/hisorherfiles

Most people use mod_userdir to allow ~username directories in their webservers. However, there is simple rewrite rule workaround that eliminates the need for mod_userdir.  I needed this because we had the home directories on the server, but the users had no login accounts on the server and they needed their public_html to work.

Here is how it goes :
```
#First, disable the default thing : 
<IfModule mod_userdir.c>
    UserDir disable
</IfModule>
#Then the rewrite rule
</pre>
<pre>#To prevent access to files ~something.html and #something.html#
<Files ~ ".*(~|#)$">
    	   Order allow,deny
    	   Deny from all
</Files>
#To show public_html access
    RewriteEngine On
    RewriteCond %{REQUEST_URI}	^/~\w+/.*$
    RewriteRule /~(\w+)/(.*)	/webteam/$1/public_html/$2
    RewriteCond %{REQUEST_URI}	^/~\w+$
    RewriteRule /~(\w+)		/webteam/$1/public_html/
#To enable .htaccess rules in public_html
<Directory /webteam/*/public_html>
    AllowOverride All
</Directory>
```