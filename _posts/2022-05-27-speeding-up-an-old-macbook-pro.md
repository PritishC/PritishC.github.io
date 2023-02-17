---
layout: post
title: Speeding up an old Macbook Pro
date: 2022-05-28
permalink: /posts/2022/05/speed-up-macbook-pro/
tags:
  - macbook pro
  - performance
---

This post will be a short one. I own a mid-2012 13-inch Macbook Pro that came with Mavericks pre-installed. I upgraded to Catalina last year before starting grad school. This led to a significant slowdown in all apps on the machine, including the terminal, which made it virtually unusable.

It was so bad that I couldn't run Google Chrome without the machine running into a kernel panic. I switched to Firefox and attempted some optimizations I found on the internet, and while this made the machine usable, the slowness remained. It was particularly bad when on a video call on MS Teams and Meet. Nothing seemed to work. Not even increasing the RAM from 6 gigs to 12 helped.

But I finally made headway a few days ago. I came across this free app by the developers of Titanium Backup, called [OnyX](https://www.titanium-software.fr/en/onyx.html), which among other things fixes corrupt system configuration files and "recalibrates" the system. After a reboot, my machine was back to 80-90% pre-Catalina snappiness. A surprise to be sure, but a welcome one!

So if you're at your wits' end, you might want to give OnyX a try. Keep the OS rollback as a last resort.
