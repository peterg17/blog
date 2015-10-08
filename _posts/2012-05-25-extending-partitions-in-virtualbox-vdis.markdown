---
layout: post
title: "Extending and resizing partitions in VirtualBox VDIs"
date: 2012-05-25 00:37
comments: true
published: true
categories: sysadmin
---

Resizing partitions in VirtualBox virtual disk images can be painful - in some cases, they don't work as expected. For instance, I had a working Ubuntu VM where the partition on which the OS was installed reached its size limit. Here's what I did:

1. If there is not enough unallocated space in the VDI, download the [CloneVDI tool](https://forums.virtualbox.org/viewtopic.php?t=22422) and make a cloned version of your VDI with as much more space as is needed.

2. Download the [GParted live CD](http://gparted.sourceforge.net/) and boot into GParted from your VM.

3. Try to do an in-place resize of the partition you want to extend into the area of unallocated space - if that works, you're done!

4. If that doesn't work, delete your linux-swap partition, and move your extended partition to the left of the available space.

5. Move your main partition to the left, too, and grow it to the desired size to the right.

6. Create new linux-swap logical partition to replace the one you deleted earlier.

The key to this procedure is moving the partitions left. Without doing that, you won't be able to resize the main partition.

An alternative, but more risky procedure is to expand your VDI with CloneVDI so that you can create an entire new parition with the desired size. Then, copy the contents from your original partition to the new old in GParted and set the "boot" mark to the new one. When I tried that, however, I lost my master boot record in the process and had to reinstall my Grub bootloader and configure it to mount Linux, which is an ugly process (I might write up the details in another post).
