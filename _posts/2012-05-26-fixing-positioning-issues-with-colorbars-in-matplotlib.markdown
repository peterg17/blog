---
layout: post
title: "Positioning issues with Colorbars in Matplotlib"
date: 2012-05-26 01:36
comments: true
published: true
categories: code
---

I ran into a problem with some Matplotlib code the other day: clearing a figure that previously held a Colorbar would still keep empty space in the location of the now-removed Colorbar.

In other words, after removing the Colorbar from a figure, the figure would not shift back to its full width. And adding a colorbar afterwards would decrease the width of the figure even further, so the problem would compound.

Thankfully, I happened across [a Stack Overflow answer](http://stackoverflow.com/a/5265614/130164) that addresses this problem with the following code:
```
self.figure.delaxes(self.figure.axes[1])
self.figure.subplots_adjust(right=0.90)  #default right padding
```

This solution is inherently hacky, but does its job well. If you execute that code after clearing a figure (`self.figure.clf()`), the figure will shift to the right, returning to its original width before the creation of the Colorbar.

Also, if you are plotting multiple graphs in the same figure, I recommend keeping global handles to the figure, to the current axes, to the current Colorbar (if it exists), and to other graph elements. With that design, updating the figure requires only modification of those handles and a call to `draw()`, and you can fix the Colorbar positioning problem by checking to see if its handle is defined before you plot a new graph and correspondingly executing the removal code.

