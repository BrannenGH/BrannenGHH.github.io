---
layout: post
title:  "How to repair an APFS formated drive with apfs_fsck"
date:   2017-10-29
categories: APFS fsck Hackintosh MacOS  
permalink: /archive/apfs_fsck
public: no
---

Since APFS is such a new filesystem, when it is being ran on a Hackintosh with a mechanical drive it can become corrupt. I have had this happen most frequently when I try to disable nVidia web drivers. 

# Boot into recovery

To boot into recovery on a hackintosh, when you boot into clover, you will want to select either a "recovery" partition or a "install Mac OS X" partition. This will allow us to unmount the main drive (typically named "Macintosh HD") because a drive must be unmounted for apfs_fsck to repair it.

# Selecting the terminal

Once you have booted into recovery/install, you should see a screen like this [take picture]

You will want to go to utilities/terminal to open up a terminal [picture]

NOTE: If your keyboard or mouse is not working in this environment, you may not have the voodooHDA drivers on the EFI of the drive you booted from. 


