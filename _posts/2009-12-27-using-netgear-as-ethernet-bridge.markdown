---
layout: post
title: "Dead-Simple Ethernet Bridge/Hub"
date: 2009-12-27 00:00 -0800
comments: true
categories: hardware
---

*Note: This is a revamp of [a post](http://blog.maximzaslavsky.com/2009/12/using-a-netgear-wgt224-as-ethernet-bridge-hub/) from my old blog. It was originally published on December 27, 2009.*

Upon moving into my new office, I hit an instant dilemna: there was only one Ethernet port and I had multiple Ethernet devices.

Crisis.

As it turns out, it's really easy to split an Ethernet connection. All you need is an old router to set up as a bridge. I used a Netgear WGT624:

![Netgear WGT624 diagram](http://i.imgur.com/LTCij.jpg)

1. Connect an Ethernet cable between the Ethernet port and the WAN port of your router.

2. Connect Ethernet cables between your network devices and LAN ports on the router.

3. On a connected device, browse to your router's setup page; in my case, it was `192.168.1.1`. Login.

4. Disable DHCP on your router. On the WGT624, you go to "LAN IP Setup" under "Advanced" in the left navigation frame, then uncheck the checkbox marked "Use Router as DHCP Server" and click Apply.

5. Decide on whether you want the router to be a wireless hub, too, and enable/disable wireless accordingly. To configure this on the WGT624, click "Wireless Settings" under "Advanced" in the left navigation frame, then check or uncheck the checkbox marked "Enable Wireless Router Radio" and hit Apply.

6. Remove the Ethernet cable inserted into the WAN port and insert into into another LAN port, instead.

That did the trick for me. You might encounter a warning notice from your main router (not the bridge) when you first try this setup.