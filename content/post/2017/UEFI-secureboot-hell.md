---
title: "UEFI Secureboot Hell"
date: 2017-12-06T23:54:46+05:30
author: Sahil Ahuja
tags: [ "linuxmint" ]
categories: [ "blog" ]
---
Spent a really long time yesterday trying to figure out how to edit UEFI boot options after my old Intel Core 2 Duo desktop refused to boot up on intstalling LinuxMint 18.3.

Had to learn more than I had bargained for about the EFI FAT32 partition at /dev/sda1 to fix it. 
The `efibootmgr` command proved to be a lifesaver. And so did the script provided in [this superuser.com post](https://superuser.com/a/376471). May the person who wrote it [live long and prosper]({{< ref "post/2016/Live-long-and-prosper-Spock.md" >}}).
