---
title: Mail with postfix and ldap
author: Sahil Ahuja
categories: [nitt]
tags:
  - dovecot
  - fedora
  - ldap
  - mail
  - postfix
id: 27
date: 2008-05-03 08:39:43
---

Yes, it's possible. I did it for the [pragyan.org](http://pragyan.org) server.

The setup we used was :

* `/var/mail/virtual/%u`: the inboxes of different users,
* `/var/mail/virtual/PragyanMail/%u/%f`: the different folders in mailboxes of different users.

It's much easily setup than one thinks initially.

HOW?? Here's how:

_But_, as with anything else, basics first

*   [<acronym title="Simple Mail Transfer Protocol">SMTP</acronym>](http://en.wikipedia.org/wiki/SMTP) server : Simple Mail Transfer Protocol : The server which sends and receives mails. **Postfix (or smtp)**.

*   [<acronym title="Internet Message Access Protocol">IMAP</acronym>](http://en.wikipedia.org/wiki/IMAP) server : Internet Message Access Protocol : The service which interacts with the <acronym title="Simple Mail Transfer Protocol">SMTP</acronym> server to access mail and send mail. **Dovecot**

*   These come preinstalled in most linux distributions.

Apart from these, other tricks that can be used by people to confuse simple minded, bread earning people like us are :

*   [MTA](http://en.wikipedia.org/wiki/Mail_transfer_agent) : Mail transfer agent : A [computer program](http://en.wikipedia.org/wiki/Computer_program "Computer program") or [software agent](http://en.wikipedia.org/wiki/Software_agent "Software agent") that transfers [electronic mail](http://en.wikipedia.org/wiki/Electronic_mail "Electronic mail") messages from one computer to another. (Eg: [Postfix](http://www.postfix.org/), [Sendmail](http://www.sendmail.org/))
*   [MDA](http://en.wikipedia.org/wiki/Mail_delivery_agent) : Mail delivery agent : A **Mail Delivery Agent** (**MDA**) is [software](http://en.wikipedia.org/wiki/Software "Software") that delivers [e-mail](http://en.wikipedia.org/wiki/E-mail "E-mail") messages right after they've been accepted on a server, distributing them to recipients' individual [mailboxes](http://en.wikipedia.org/wiki/Email_Mailbox "Email Mailbox"). (Eg: [dovecot](http://www.dovecot.org/))
*   [MUA](http://en.wikipedia.org/wiki/Mail_user_agent) : Mail user agent : An **e-mail client**, aka **Mail User Agent** (MUA), aka **email reader** is a frontend [computer program](http://en.wikipedia.org/wiki/Computer_program "Computer program") used to manage [email](http://en.wikipedia.org/wiki/Email "Email"). (Eg: [gmail](http://gmail.com), [evolution](http://gnome.org/projects/evolution/), [horde](http://www.horde.org/), [squirrelmail](http://squirrelmail.org/), Outlook Express.)
Now that thats out of the way, lets get our hands dirty.

But again, not so fast. As with anything in linux, when you set off to configure something, you end up knowing much more than you bargained for. ;)


### <a id="aliases" name="aliases">Aliases</a>

Aliases are mappings between one source name and one or many destination name (in mail).

Aliases can be found out from flat files in the form of mapping, from sql queries or from ldap (`man ldap_table`). The source itself can be in the destination.

Link to alias files is given in `/etc/postfix/main.cf` at line
`alias_maps = hash:/etc/aliases, ldap:/etc/postfix/ldap-aliases.cf`

Type `/usr/sbin/postmap -q core@pragyan.org ldap:/etc/postfix/ldap-aliases.cf` to see its effects.


### <a id="local_transport" name="local_transport">local_transport</a>

The *local_transport* parameter corresponds to the mail delivery agent used.

1.  The default with postfix is _local_. The problem with local is that is requires local users and hence, a posixAccount schema to be an objectClass of every mail account. Rejected. Btw local also has to ability of mail forwarding to a user. i.e. if mailbox of **_user_** user1 is user1@gmail.com (user forwarding), then local will also forward to user1@gmail.com. By default, it assumes the uid of the user it is delivering mail to while delvering mail.

1.  Next is _virtual_. This is the one used. Virtual accepts users who are _system_ users. But virtual (for security purposes) does not forward to hosts other than the localhost. So how do we forward to external hosts? virtual forwards in case the mails are aliases. So we simply put the gmail address as the entry of one of the aliases of the mail. If virtual MDA is used then whose uid does it use? (because the uid of the user himself doesn’t exist on the system). Another parameter value has to be used :
```
virtual_minimum_uid = 100 (security feature)
virtual_uid_maps = static:700
virtual_gid_maps = static:700
```

1.  Other mail delivery agents : _procmail_ doesn’t understand LDAP, and _maildrop_ has too much overhead.

### <a id="group_expansion" name="group_expansion">Group expansion</a>

Excellent notes are available in /usr/share/doc/postfix-2.4.3/README_FILES/LDAP_README.

Any “map” parameter value, like alias_maps, can be either given a flat mapping file name, or a .cf file, with tells it what to do to get the mapping, in this format : **protocol:filename**. Eg.

`virtual_mailbox_maps = ldap:/etc/postfix/accountsmap.cf`

### <a id="mail_boxes" name="mail_boxes">Mail boxes</a>

**mbox** is a format for storing mails. It is the default format used in postfix and dovecot. This is a line from dovecot conf :
`mail_location = mbox:/var/spool/mail/virtual/PragyanMail/%u:INBOX=/var/spool/mail/virtual/%u`

The first part (mbox:**/var/spool/mail/virtual/PragyanMail/**%u:INBOX=/var/spool/mail/virtual/%u) refers to the user’s mail folder, which contains all his mail folders (Trash, drafts, sent mail.. ) (_the user’s mail folders are files in mbox format_)

The second part (mbox:/var/spool/mail/virtual/PragyanMail/%u:INBOX=**/var/spool/mail/virtual/%u**) refers to the one specific user folder (i.e. server file) which postfix writes to, that is his INBOX. (All other folders are written to and handled by the <acronym title="Internet Message Access Protocol">IMAP</acronym> client - dovecot.) Other variables which could have been used for specifying this are : %u - username, %n - user part in user@domain, same as %u if there’s no domain, %d - domain part in user@domain, %h - home directory etc.

A virtual user can specify his mail folder to be anywhere. So, the following is a security config for postfix INBOX files :

`virtual_mailbox_base = /var/spool/mail/virtual`

Also `chmod g+s /usr/bin/procmail` for it to be able to create mail directories

### <a id="maps_specified_in_postfix" name="maps_specified_in_postfix">Maps specified in postfix</a>

Maps are specified in `/etc/postfix/main.cf`. Important maps to be specified are :

1.  User aliases **virtual_alias_maps** - mapping between group@domain.org and user1@pragyan.org, user2@pragyan.org, ...
2.  User mailboxes **virtual_mailbox_maps** - mapping between mailaddress (user1@pragyan.org) and mailbox location (`/var/spool/mail/virtual/user1`). A confirmation that the mail address corresponds to a real virtual user. For mail to be delivered, this entry needs to be there, which contains the mailbox address. This is but only a one to one mapping. (Ignores all following values)
`local_recipient_maps = $virtual_mailbox_maps`
This line is required whenever the **local_transport** is changed to something else. (in this case to virtual)

### <a id="schemas_the_real_working" name="schemas_the_real_working">Schemas (The Real Working):</a>

* Ldap Entry **evolutionPersonList**<pre>
contact (multiple) : links to others ldap entries : uid=sahil,ou=P... , uid=cyber, ou=.. , ...
mail (multiple) : mails : sahilahuja@gmail.com, core@pragyan.org, ...
listName (single) : list name : coding
</pre>
*  main.cf entry : `virtual_alias_maps = ldap:/etc/postfix/ldap-aliases.cf`. Contents of ldap-aliases.cf :
```toml
server_host = 10.0.0.126
search_base = ou=Groups,ou=Pragyan,dc=delta,dc=nitt.edu
query_filter = (&amp;(objectClass=*)(listName=%u))
result_attribute = mail
special_result_attribute = contact
bind = yes
bind_dn = cn=dovecot,ou=Pragyan,dc=delta,dc=nitt.edu
bind_pw = ******
```
  * The field matched is **listName**.
  * The query runs recursively runs on field “contact”.
  * All mails of form alias@pragyan.org again go through the same process.

* Ldap entry **evolutionPerson** . Important thing in it is the mapping between uid and mail. It’s a proof to postfix the user is a real virtual user.
* main.cf entry `virtual_mailbox_maps = ldap:/etc/postfix/accountsmap.cf`. Contents of accountsmap.cf :
```toml
server_host = 10.0.0.126
search_base = ou=People,ou=Pragyan,dc=delta,dc=nitt.edu
query_filter = (&amp;(objectClass=*)(mail=%s))
result_attribute = uid
bind = yes
bind_dn = cn=dovecot,ou=Pragyan,dc=delta,dc=nitt.edu
[gallery]bind_pw = ******
```

* The final main.cf entry that fits it all : virtual_mailbox_base = /var/spool/mail/virtual . A file with the name that is a result of the previous query (**uid**), gets created in this directory as the inbox of the user.
Workflow is mailid → getaliases → Use alias result to get mail ids → deliver. That is, first alaises get processed, then accountsmap.

Here are the files I used finally :

* Postfix : <span class="wikilink1">main.cf</span>, <span class="wikilink1">accountsmap.cf</span>, <span class="wikilink1">ldap-alias.conf</span>
* Dovecot : <span class="wikilink1">dovecot.conf</span>, <span class="wikilink1">dovecot-ldap.conf</span>
* [Here](https://gist.github.com/sahil87/fe2569f472cccaa1c277aefc2c2ff245) is a compilation of the final content of these files.

[Here](http://wanderingbarque.com/howtos/mailserver/mailserver.html) is the link of the guide I used as my own reference.
