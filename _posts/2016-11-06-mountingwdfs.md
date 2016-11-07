---
layout: post
title:  "How to Set Up WDFS  on openSUSE"
date:   2016-11-06 19:16:00
categories: openSUSE linux how_to nextcloud webdav wdfs
permalink: /archive/configure_wdfs
---

# How to mount a webdav partition on openSUSE and configure openSUSE to mount it at boot

Webdav, a system used by owncloud and nextcloud for mounting cloud partitions, can be easily added to openSUSE. This tutorial was written for [openSUSE Leap 42.1](https://software.opensuse.org/421/en) and with wdfs version 1.4.2-154.2.

## How to install

Root access will be required for installing wdfs.

### How to install by terminal

Open konsole then type:
   sudo zypper install wdfs

### How to install with YaST

First, open YaST2 (which is labled as YaST in the application menu in the bottom left), then type in your password. Next, click on "Software Management" then, after it loads, type in wdfs into the box and then hit the search button. Finally, click the check button to the left of "wdfs" then hit install.

## How to mount a partition

For this process, a terminal emulator like konsole has to be used.

First type:
    sudo wdfs -o allow_others http://yourcloud.com/webdavdirectory /mountpoint
Where http://yourcloud.com/webdavdirectory is the location of the webdav server you want to mount, and /mountpoint is the local mountpoint on your system — can be anything, if you need to set up a mountpoint, you can run:
    mkdir ~/webdavserver
And after that run:
    sudo wdfs -o allow_others http://yourcloud.com/webdavdirectory ~/webdavserver
Then type in your computer password (if asked), then your webdav username, then your webdav password.


## How to set up automatic mounting as a part of fstab

To mount the directory without root permissions, the fstab file has to be configured

#TODO

    
