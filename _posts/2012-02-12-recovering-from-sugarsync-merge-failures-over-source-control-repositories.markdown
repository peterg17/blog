---
layout: post
title: "Recovering from SugarSync merge failures over source control repositories"
date: 2012-02-12 01:11
comments: true
categories: code
---

Intro to SugarSync (SS)
-------

Ever since I started using **[SugarSync](http://sugarsync.com)**, I've loved the app. Until now, it's proven to be easy to use and abnormally straightforward.

However, this weekend, SugarSync Manager decided to start crashing upon each load, making it completely unusable. I ordinarilly would have attempted to find and fix the cause of these crashes, but since the app was due for an update anyway, as I had neglected to run SugarSync (and sync latest changes) for a while, I decided to reinstall the Manager completely.

Problem
-------

That turned out to be a bad decision. For some reason, I wasn't able to explain to SugarSync that the original device that had synced to my account is the same as the current device, so it treats them as different entities with the same device name. Instead, I decided to try SugarSync's *merge* functionality - as the people at SS explain it, it looks for differences between the older (in this case) version synced and the newer (in this case) version available on the current device.

I did not expect this to be a problem, but SugarSync decided to start merging within the `.hg` and `.git` directories of my hg and git repositories. Thus, old dirstates and other key files were transformed to the version they had been at an earlier time.

Solution
-------

My folder structure looked someting like this for "infected" files:

*   `_Handwriting (from Maxim-laptop).i` // this is the newest one
*   `_Handwriting.i` // this is the older one, but takes the place of the latest one.

After countless bouts with HG in order to fix this via the HG tools, I decided to instead **[write a simple program](https://github.com/maximz/sugarsyncfilefix)** that renames files in order to enable this to work.

File changes:

1. `_Handwriting.i` --> `_Handwriting.i.old`
2. `_Handwriting (from Maximlaptop).i` --> `_Handwriting.i`

If you run into this problem and just want a binary, here is the [Windows, .NET 4 binary](https://github.com/maximz/sugarsyncfilefix/raw/master/SugarSyncFileFix/bin/Release/SugarSyncFileFix.exe).
