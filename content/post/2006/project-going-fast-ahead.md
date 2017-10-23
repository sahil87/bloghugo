---
title: Project going fast ahead!!
author: Sahil Ahuja
categories: [pcbo]
date: 2006-05-25 04:30:00
---

Today...
For the first time we saw values change in the monitor with us changing a knob in our hands!!! (instantaneously)
We plotted the graph of the actual and observed readings.. IT WAS BEAUTIFUL!!!

We made a prog for querying C with MySQL and integrated it with PARAPIN.

Mr. Pandit told us to ponder more on the diode circuit problem he gave us.

Then..
I decided..
The following approaches are available for giving the data to the JAVA-APPLET:

1.  To digitally sign the java applet to allow it make connections to other hosts.
2.  To use the tomcat server to make the MySql queries for the applet and ask the applet to connect to tomcat server on port no 80\. (The applet is allowed to make connection only to port it was called from.)
3.  The 3rd approach.. (My original approach :)
To use AJAX to update the data on the client!!
The APPLET tag on the webpage has a parameter named PARAM.
My theory is -Sahil