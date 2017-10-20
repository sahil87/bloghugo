---
title: "{{ replace .TranslationBaseName "-" " " | title }}"
date: {{ .Date }}
draft: true
author: Sahil Ahuja
tags: [ "test", "git" ]
categories: [ "blog", "guide" ]
featuredpath: "date"
featured: "image-name.png"
featuredalt: "Image Name Alt"
description: Optional description
---
{{< load-photoswipe >}} <!-- needed only once -->

Summary Line used if description not given above
{{< figure src="/images/2008/snapshot2.png" title="KDE 4 Preview" width="300px">}}

<!--more-->

More content for the body
{{< figure src="/images/2008/screenshot.png" title="Gnome Preview" width="300px">}}

### Gallery
{{< gallery >}}
{{< figure link="/images/2008/pcbo/canteen-pic.jpg" caption="IITB Canteen" >}}
{{< figure link="/images/2008/pcbo/103_0169.jpg" caption="Our Circuit connected to the power supply" >}}
{{< figure link="/images/2008/pcbo/103_0166.jpg" caption="Our Circuit" >}}
{{< /gallery >}}

### Youtube Embed
{{< youtube n2_BVgWMa1c >}}

#### Code highlight
{{< highlight toml "linenos=table,linenostart=50,hl_lines=2 4-5" >}}
server_host = 10.0.0.126
search_base = ou=Groups,ou=Pragyan,dc=delta,dc=nitt.edu
query_filter = (&amp;(objectClass=*)(listName=%u))
result_attribute = mail
special_result_attribute = contact
bind = yes
bind_dn = cn=dovecot,ou=Pragyan,dc=delta,dc=nitt.edu
bind_pw = ******
{{< /highlight >}}
