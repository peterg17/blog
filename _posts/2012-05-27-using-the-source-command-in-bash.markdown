---
layout: post
title: "Using the source command in bash"
date: 2012-05-27 00:51
comments: true
published: true
categories: code
---

A handy command for bash scripts is `source`:
> [When a script is run using `source' it runs within the existing shell, any variables created or modified by the script will remain available after the script completes.](http://ss64.com/bash/period.html)

So if you want to execute code that affects your current shell, rather than having it run in its separate subshell, run `source ./mycode` or `. ./mycode`.
