---
title: Playing Around
author: Sahil Ahuja
categories: [pcbo]
date: 2006-06-06 12:56:00
---

We realised the transfer of data through php and JavaScript made the process of plotting too slow, giving a plotting rate of only <span style="font-weight:bold;">1 frame/s</span>. We had to take a different path, so we decided to use a Java Servlet. The applet was allowed to interact with the servlet through the sandbox. The servlet interacted with the MySQL databse. The implication of this was that we could achieve frame rates of upto <span style="font-weight:bold;">20 frames/s</span> as the Tomcat server was fast. We decided this today and made a Java applet accept a string variable parameter from the servlet.