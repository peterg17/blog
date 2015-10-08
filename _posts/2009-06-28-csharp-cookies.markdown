---
layout: post
title: "C#: handling cookies in a series of HttpWebRequest and HttpWebResponse sessions"
date: 2009-06-28
comments: true
categories: code
---

*Note: This is a revamp of [a post](http://blog.maximzaslavsky.com/2009/06/c-handling-cookies-in-a-series-of-httpwebrequest-and-httpwebresponse-sessions/) from my old blog.  It was originally published on June 28, 2009.*

A while back, I was working on "wrapping" and extracting data from an online database UI. In order to retrieve data, a user would submit a series of HTML forms, view the resulting map, and then see a popup with a malformed-HTML table of all the points displayed on the map. My goal was to write some C# that would submit these painful forms in various desired combinations and retrieve and parse the points.

To add insult to injury, a Fiddler run revealed that whoever wrote the UI decided to not just maintain session state, but also *transfer raw data* between the different UI pages using cookies and HTTP referrers with querystrings ... naturally. :'(

Thankfully, C# makes this really easy to solve - you just create a cookie "jar" that carries over from HTTP session to another:

```
var cookieJar = new CookieContainer(); // initialize cookieJar
var request=(HttpWebRequest) WebRequest.Create("http://google.com"); // create your HttpWebRequests
request.CookieContainer = cookieJar; // for each HttpWebRequest you make, add cookieJar
```

Use the last line to apply `cookieJar` to each request and you're set!
