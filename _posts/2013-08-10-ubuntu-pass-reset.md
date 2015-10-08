---
layout: post
title: "Ubuntu password reset"
date: 2013-08-10 00:00
comments: true
published: true
categories: sysadmin
---

Having forgotten the root passwords to several of my Ubuntu virtual machines, I searched for ways to crack or reset the passwords. Here's my solution.

First, you want to get access to a root shell so you can change passwords and other settings. The easiest way to do this is to boot into Ubuntu recovery mode from the GRUB bootloader screen. Select "root" from the options menu that appears. This drops you into a root shell!
Ubuntu now mounts the filesystem as read-only by default, so execute `mount -o rw,remount /` to remount it with read-write permissions.

If you don't have a recovery mode option in your bootloader menu, boot up from a Linux live CD. Open a terminal window, then execute the following:

```
sudo su # Authenticate as root within your live-CD environment
fdisk -l # List the hard drives available on your system, and identify which one holds your Linux setup. In this example, /dev/sda1 is my Linux partition.
mkdir /mnt/internalhdd # Create a mounting point
mount /dev/sda1 /mnt/internalhdd # Mount your Linux partition
chroot /mnt/internalhdd # Change root into your Linux partition. Now you have root access!
```

Now that you have a root shell, run `passwd root` and `passwd [your-username-here]` to reset passwords for your accounts.

If you used the Linux live CD method, here are the commands you should execute to safely unmount your Linux partition:

```
exit # Exit to one level up, i.e. from /mnt/internalhdd root to root on your Linux live CD
umount /mnt/internalhdd # Unmount your Linux partition
mount # List mounted devices. Confirm that /dev/sda1 is not mounted anywhere else.
exit # Exit to one level up, i.e. from root on your Linux live CD to the default user account on your Linux live CD
exit # Exit to one level up, i.e. close the terminal window.
```
