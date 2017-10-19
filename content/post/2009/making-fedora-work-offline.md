---
title: Making Fedora rpms/yum work - Offline
author: Sahil Ahuja
categories: [blog]
tags:
  - fedora
  - offline
  - update
  - yum
date: 2009-10-22 01:00:44
---

This is guide relevant to those who wish to spread fedora to friends and loved ones who don't necessarily always have an internet connection (or a good one atleast). The problem faced in such situations, almost always (talking from my experience), is that there are a huge number of rpms that need to be downloaded to make fedora capable of playing media, and fill it with good stuff like k3b, amarok etc.

This isn't always possible with the skimpy internet connections that our not-so-tech-savvy aunts have. (We'll assume that it is our aunt on whose system we need to install fedora for the sake of this guide.)

So, I devised a way of spreading fedora to our aunt's system, without getting embarrassed  by that fact that we weren't able to run mp3 on their system.

The way to do this, is to **install a fresh copy of fedora** on our system, and then bring it to perfect shape by **installing many more rpms**, and while doing this, **keeping a copy of the rpms** required, and then copying this repository of rpms (which we are sure don't require any more rpms as dependencies as we install them on our own system in offline mode) on a pen drive and taking it along with the fedora installation media to our aunt's home. And after installing fedora on her system, we simply **install all the rpms on her system**.

**Steps:**
**On our system:**
Download all rpms required for the extra packages (the package rpms + dependencies)
`yumdownloader --destdir=rpmsForAunt --resolve rpmName(s)`

OR

create a service pack of all pending updates or certain rpms using gpk-service-pack
`yum install gnome-packagekit-extra`

OR

Edit /etc/yum.conf and change the value of keepcache to 1\. After the update is done, the downloaded rpm files then can be found in (and copied from) subfolders named "packages" in /var/cache/yum. When you're done with them you can get rid of them to save disk space with yum clean packages.
**On our aunt's system:**

1.  Install fedora.
2.  Install the extra downloaded rpms:

    1.  You need to disable all repositories before yum localinstall will work without net access. To do so,
go to System &gt; Administration &gt; Add/Remove Software and go the System &gt; Software Sources and **uncheck **all sources.
    2.  Installing the rpms:(1 : see footnote)
`cd rpmsForAunt; yumlocalinstall --nogpgcheck *`
The above command is to be run for every category of rpms below after copying the resultant directories on our Aunt's system.
**For getting all updates:**
I wrote a script for downloading all updates (after a fresh install) to a directory:
```
for i in `yum list updates | grep fc11 | cut -d ' ' -f 1`
do
echo Now downloading rpms for package $i
yumdownloader --destdir=localUpdate --resolve $i
done
```
**For getting all media rpms:**
```
rpm -ivh http://rpm.livna.org/livna-release.rpm
rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-livna
rpm -ivh http://linuxdownload.adobe.com/adobe-release/adobe-release-i386-1.0-1.noarch.rpm
rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-adobe-linux
```
(the above is required only so that _you (and not your aunt) _can download the rpms)

`yumdownloader --destdir=localRpmsForMedia --resolve libdvdcss vlc flash-plugin xine xine-lib-extras xine-lib-extras-freeworld mplayer mplayer-gui gecko-mediaplayer mencoder amarok rhythmbox gstreamer-plugins-ugly gstreamer-plugins-bad gstreamer-ffmpeg audacious audacious-plugins-freeworld* k3b`

**A few more rpms that I use:**

`yumdownloader --destdir=localRpmsOther system-config-lvm gparted digikam m17n-db-*`
> (1)I faced an issue while bash was updated using this method. It said transaction failed.
> 
> To resolve this, I ran
> 
> ```yum-complete-transaction --clean
> rpm -e bash
> ```
> 
> The above command listed two bash versions (I don't remember the version numbers), on saying rpm -e bash.version1, it said there are many dependencies, then I tried rpm -e bash.version and it worked. Then, I went back to the yumlocalinstall step and then that worked.