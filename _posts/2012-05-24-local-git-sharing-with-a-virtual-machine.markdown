---
layout: post
title: "Local Git sharing with a virtual machine"
date: 2012-05-24 21:35
comments: true
categories: code
---

My recent projects have involved work between two OSes. I run Windows as my host OS and virtualize Ubuntu, and in order to share work efficiently between the two, I've been using a local bare Git repository in a shared folder.

It's quite simple to set up:

First, make sure that you have a shared folder that is available to both your host and your guest OS. I personally use VirtualBox's Guest Additions and its built-in Shared Folders functionality, so I mount my share using the following command, where "share" is the name of the shared folder I have defined in VirtualBox, and "~/host" is the path to which I am mounting:
```
sudo mount -t vboxsf share ~/host
```

Now, initialize a bare Git repository in the shared folder:
```
cd "~/host"
mkdir myrepo
cd myrepo
git init --bare
```

Almost done. Return to your original repository and add to its remotes:
```
git remote add local "~/host/myrepo"
git push local master
```

Finally, clone that repository from your other OS:
```
git clone "C:\vmshared\myrepo"
```

Now, you can `git push` and `git pull` between your repository on the host OS and your repository on the guest OS to synchronize changes.
