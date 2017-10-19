---
title: httpd with SElinux
author: Sahil Ahuja
categories: [blog]
date: 2009-10-22 14:47:13
tags:
  - httpd
---

**Giving httpd access to other folders (apart from default SElinux allowed folders):**

*   system-config-selinux rocks!!
Go to System-&gt; Administration -&gt; SELinux Management (or system-config-selinux from command line).
Type httpd in Filter and press enter. You will see that files that allow httpd write access have the Selinux File Type **httpd_cache_t:s0**. So.. now you know what to do right? Say you want to give httpd write access to folder /var/lib/dokuwiki/data/cache, then add a new file labelling using the Add button with the following details:
`File specifications: /var/lib/dokuwiki/data/cache(/.*)?
File Type: all files
SELinux Type: httpd_cache_t
MLS: s0`
and then
`restorecon /var/lib/dokuwiki/data/cache`

**OR**

*   Go to /var/lib/dokuwiki/data and apply the selinux file type to cache directory`chcon -R -t httpd_cache_t /var/lib/dokuwiki/data/cache`
And now, httpd should have write access to this folder.
**Running httpd on other ports:**
Open /etc/httpd/http.conf and change
`Listen 80`
to
`Listen 81`

If you use VirtualHosts, you need to change the ports there instead (&lt;VirtualHost *:**81**&gt;)
**Giving httpd access to other ports:**
Go to Network Port in SELinux Administration and filter of "80" and press enter. You will see an entry for http_port_t. Create a similar new entry for port 81 for SELinux Port type http_port_1.
And that's it.
**Links to posts that helped me:**
[Dan Walsh's Blog](http://danwalsh.livejournal.com/9275.html)

[Notes on SElinux](http://equivocation.org/node/11)