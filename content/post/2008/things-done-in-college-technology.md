---
title: Things done in college - technology
author: Sahil Ahuja
categories: [nitt]
tags:
  - dalal
  - delta
  - fedora
  - ldap
  - nfs
  - pcbo
  - pragyan
  - ssl
date: 2008-05-20 02:35:28
---

Here is a list of things I have done in the past three years. I have written for the sake of personal record.

_As a member of Delta :_
Created a "[PC Based Oscilloscope](http://pcbasedoscilloscope.blogspot.com/)" in IIT Bombay, as a summer project. Used java servlets on the server side and a java applet on the client side. Was responsible for the whole of the software side - 2006 Summers
Worked in Pragyan CMS V1, which finally got implemented in our [college website](http://www.nitt.edu) - 2005-2007
Made [Dalal Street](http://pragyan.org/08/home/events/management/ds/), a stock market simulator using java servlets on the server side and using eclipse to make a java based ui compiled using gcj to eliminate the need of jvm to run the final executable - 2006 Dec - 2007 Jan
Used [CVS](http://en.wikipedia.org/wiki/Concurrent_Versions_System) for the development of Dalal Street, understood the importance of a code versioning system.

_As being a part of Delta Core (Technology Changes) :_
Implemented [**LDAP**](http://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol) using [openldap](http://www.openldap.org/), in Delta, allowing everyone to have a central authentication server, with a common login everywhere, where everywhere includes :
system login in Sun Lab comps
Implemented [NFS](http://en.wikipedia.org/wiki/Network_File_System_(protocol)) on Delta, which gets mounted on all Sun Lab comps, using the default nfs service provided by default on [fedora](http://fedoraproject.org/), so everyone has the same home irrespective of the comp they login to, which they do through their ldap accounts.
Implemented [pure-ftpd](http://www.pureftpd.org/) on Delta, configured it to work through ldap, allowing everyone to access their home drives even from "outside" (the user labs).
Setup, and advocated use of [Doku](http://wiki.splitbrain.org/wiki:dokuwiki) for information keeping, made it work through LDAP.
Implemented and introduced [SVN](http://en.wikipedia.org/wiki/Subversion_(software)) on Delta, setup three repositories : pragyan, delta and dalal, delta for the use of all delta projects.
Implemented and introduced [trac](http://trac.edgewall.org/) on delta, setup three repositories : pragyan, delta and dalal. Customized all of these three. Learned how to customize through .egg files.
Made [svn and trac work through httpd authentication](http://sahilahuja.wordpress.com/2008/05/20/ldap-authentication-through-apache-for-svn-trac-or-anything-else-for-that-matter-p/), which used LDAP to get authentication details. (this was hell)
Revived [delta](http://www.nitt.edu/home/students/clubsnassocs/computing/delta/) as a [student group](http://www.nitt.edu/home/students/clubsnassocs/) - meaning, made sure many meetings were held, made sure everyone knew each other, everyone contributed something to delta and felt a part of the group, made sure many treats were held, and chucked a few inactive members out of delta.
Created [Pragyan CMS V2](http://sourceforge.net/projects/pragyan), from scratch.

_As being [Pragyan'08](http://pragyan.org/08/) Systems head :_
[Implemented mail system through postfix](http://sahilahuja.wordpress.com/2008/05/03/mail-with-postfix-and-ldap/), made its authentication work through ldap. Implemented mailman like features using contact attribute in ldap and aliases in postfix.
Made [dovecot](http://www.dovecot.org/) work through ldap too.
Learned what [SSL](http://en.wikipedia.org/wiki/Secure_Sockets_Layer) certificates are, how they work, created a self signed ssl certificate for pragyan.org, using [tinyCA2](http://tinyca.sm-zone.net/) provided in [Fedora](http://fedoraproject.org/), and made it use it. (basically, allowed the use of https://pragyan.org/...)
[Implemented FDS](http://sahilahuja.wordpress.com/2008/05/05/creating-your-own-schemas-in-fds-ldap-for-use-in-postfix-or-anything-else-for-that-matter-p/) (Fedora Directory Server) as a much better alternative to LDAP on Pragyan Server.