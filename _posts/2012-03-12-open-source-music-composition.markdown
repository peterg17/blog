---
layout: post
title: "Open source music composition"
date: 2012-03-12
comments: true
published: false
categories: music
---

*Note: This is a revamp of [a post](http://blog.maximzaslavsky.com/2010/03/open-sourcing-music/) from my old blog. It was originally published on March 10, 2010.*

The open source movement has infiltrated many fields: software, hardware, writing. But a major one has been overlooked.

We haven't changed what currently goes on in the music industry... yet.

The open source paradigm, or at least Free As In Beer, certainly has had an effect on music, which is why many artists opt to release their music for free online. The extent is fully public-domain recordings and sound libraries.

Yet composition, the root of all music, remains unchanged. Arguably, composition is impossible to open up, since it is an embodiment of a single composer's feelings and ideas.

# Current problem

Tthe problem we're facing is two-fold:

* **Music composition is very private**: the current form of music composition limits music to being written by one or a few people.
* **Publishing is also private**: only one publishing route exists, and that is for composers who are famous and good enough to have contracts with big publishers. No Creative Commons-type alternative exists.

But what if people could work together to write music? 

Then the previous paradigm of private composition would break. Ideas would be generated together and combined, for higher creative potential. The repetive and time-consuming notation tasks of composition would be streamlined, for a faster process, which will make composition much more available and entertaining to potential composers. The final product would be published openly, for freedom of sharing and for the potential of remixing, arranging, adaptation, and external improvement.

What if there were a team like Code52, starting and working on a new open source composition project each week?

# Finding an open source solution

Such a model would be very different from the technology we have today. Ideally, we could have a Github-esque environment. A composer creates a repository for their new project and starts notating a composition. They push the repository online and other users fork it, make their own changes, and submit pull requests that the original composer then merges into the main repository. Pretty similar to an open source code workflow with Git.

In terms of licensing, porting a Creative Commons license to the music field would fulfill these needs.

But what format would you store music notation in? 

Open format: MusicXML is proprietary, maybe create something very open called MML or MusicML (Music Markup Language)? There should then be converters from other proprietary formats (e.g. Sibelius files, Finale files, the aforementioned MusicXML, etc.)


# Issues

There are more fundamental technicalities to be resolved. Assuming we build a suitable open format for music notation, we need to find a way to manage idea and style differentiation. As the purpose of individual components of music is impossible to explain objectively to someone else, group collaboration will be difficult. But small groups of writers have managed to solve that problem, so maybe larger groups will, too.

# Taking this further

* A Q&A site where composers can share portions of their notations and receive feedback and potential improvements
* An online Creative-Commons-licensed library of user-submitted motifs that composers can use
