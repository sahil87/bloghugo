---
title: Fedora Directory Server Rocks!!!
author: Sahil Ahuja
categories: [nitt]
tags:
  - fds
  - fedora
  - ldap
date: 2008-04-04 01:18:08
---

Having gone through the hell of installing  an LDAP server once, I thought I could I could install the openldap server on the old server that we had to shift to.

Anshu had already broken his head on it and was at the verge of losing his sanity. And so i stepped in.

First I checked /etc/openldap/slapd.conf, line by line. Everything was fine.
`ldapadd -W -x -D "cn=Manager,dc=pragyan,dc=org" -f base.ldif`
`**invalid credentials (49)**`

`slappasswd`
`Enter password:`
**`{SHA}xyxzsdf;alskjdf;lasjdf;lajd`**
I put the password in slapd.conf

tried again.
`**invalid credentials (49)**`

Changed the rootdn in slapd.conf
`**invalid credentials (49)**`

Removed evolutionperson.schema
`**invalid credentials (49)**`

Uninstalled openldap-server, openldap-client, db4utils
`rpm -e --nodeps openldap-server openldap-client db4utils etc...`
Reinstalled all of these from yum
`yum install openldap-server openldap-client db4utils etc...`
Reconfigured slapd.conf
`**invalid credentials (49)**`

I started making strange sounds, started laughing without reason.

Opened a website listing down installation steps, followed them **line by line**
`**invalid credentials (49)**`

Thats when I remembered Fedora Directory Server. (It wasn't fully developed when I was implementing LDAP in Fedora 7, so didn't use it then).

To my pleasant surprise they have the concept of "install scripts". I felt like a king when the script asked me, "What would you like your domain root to be? Usually, you should keep it the same as your fully qualified domain name". A smile appeared on my face. I knew the meaning of true happiness then.

[http://directory.fedoraproject.org/](http://directory.fedoraproject.org/)