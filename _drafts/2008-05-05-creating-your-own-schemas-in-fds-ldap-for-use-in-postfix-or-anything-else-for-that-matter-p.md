---
title: >-
  Creating your own schemas in FDS Ldap for use in postfix (or anything else for
  that matter) :P
author: Sahil Ahuja
categories: blog
tags:
  - fedora
  - ldap
  - postfix
id: 32
date: 2008-05-05 15:58:25
---

What I needed for mailman like functioning while making postfix work with ldap was an attribute that stores content of type DN (Distinguished Name) i.e. a node address, or holding a data type that stores nothing but data of type that can hold address of the data type itself.

In openldap, I used a schemas called evolutionPerson and evolutionPersonList (available with my fedora openldap distribution by moving evolutionperson.schema in /usr/share/evolution-data-server-1.12/ to /etc/opanldap/schemas/). evolutionPerson is very similar to inetOrgPerson class, which stores basically everything that could ever be used to describe a person. The reason I chose evolutionPerson over inetOrgPerson was the availablity of the evolutionPersonList class. Its attributes are : mail, contact and listnName, where both mail and contact can contain more than one values. mail and listName attribute type is text, and contact attribute type is DN. contact's were used to create groups, and mail's were used to forward the email to a third party server. Here is a screenshot of the same in action :

[![](http://sahilahuja.files.wordpress.com/2008/05/openldap.jpg?w=300)](http://sahilahuja.files.wordpress.com/2008/05/openldap.jpg)

The contact attribute worked like charm. If any contact attribute turns out to be another evolutionPersonList, it repeats the whole process again for it, collecting new mails from it, and if it turns out to be evolutionPerson, it takes its mail attribute. The whole process repeats itself, taking care that infinite loops do not get created. In the end, what we get a list of mail ids to which the mail has to be sent.

Now, I haven't yet figured out how to add _evolutionperson.schema_ to schema. So, what did I do for delta?? I simply created my own schema. For a user, I already had whatever I needed in inetOrgPerson. All I need was some sort of an inetOrgPersonList. So, here are the steps :

*   I am assuming you have already setup fedora directory server through the [wonderful install scripts](http://sahilahuja.wordpress.com/2008/04/04/fedora-directory-server-rocks/) provided. (/usr/sbin/setup-ds-admin.pl and then /usr/sbin/setup-ds.pl)
*   Open Fedora Directory Server admin console : /usr/bin/fedora-idm-console

[![Me, showing off my workspace](http://sahilahuja.files.wordpress.com/2008/05/myworkspace.jpg?w=300)](http://sahilahuja.files.wordpress.com/2008/05/myworkspace.jpg)
*   Under the server groups entry in the default view tree, select your directory server and open it, using the DN and password you provided earlier during the directory server setup.
*   Under the to configuration tab, select schema. Select Attributes in the right hand pane.
*   Create a new attribute by clicking on the new attribute button at the bottom of the right pane.

[![](http://sahilahuja.files.wordpress.com/2008/05/dsconsoleattributes.jpg?w=300)](http://sahilahuja.files.wordpress.com/2008/05/dsconsoleattributes.jpg)
*   I needed two new attributes for my purpose :

    1.  contact : of type DN, multi valued.
    2.  listName : of type String, single valued.
    3.  The third multivalued attribute I needed, mail, already exists.

*   Now, under the Object Classes pane, create any number of Objects you nees, using the attributes you just now created, or the preexisting ones.

[![](http://sahilahuja.files.wordpress.com/2008/05/dsconsoleobjectclass.jpg?w=300)](http://sahilahuja.files.wordpress.com/2008/05/dsconsoleobjectclass.jpg)
*   The one created was inetorgpersonlist having Required Attributes listName and objectClass, and Allowed Attributes contact and mail.
That's it!!