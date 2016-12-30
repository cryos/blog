---
layout: post
title: Timer Issues Solved With AMD Athlon64 X2 Dual Core Goodness
categories:
- FOSS
- Gentoo
- Hardware
- Linux
permalink: "/archives/56-Timer-Issues-Solved-With-AMD-Athlon64-X2-Dual-Core-Goodness.html"
s9y_link: http://blog.cryos.net/archives/56-Timer-Issues-Solved-With-AMD-Athlon64-X2-Dual-Core-Goodness.html
date: 2005-10-02 19:03:00.000000000 +00:00
---
I have had my newish system up and running for most of the weekend now. I noticed when doing lots of compilation/work on the system that I sometimes ended up with 10 characters where I had only typed one, and gained 10 minutes of time in less than an hour with ntpd running! After some searching around I came across <a href="http://bugzilla.kernel.org/show_bug.cgi?id=5105">this kernel bug entry</a> detailing my exact problem and a solution to it. Just adding the notsc option to the grub entry for my SMP kernel solved this problem immediately. Just thought it might help others who are having similar issues until the patch makes it into gentoo-sources and/or the mainline kernel.
