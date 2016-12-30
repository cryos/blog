---
layout: post
title: Got My New System Working
categories:
- General
- Gentoo
- Hardware
- Linux
permalink: "/archives/54-Got-My-New-System-Working.html"
s9y_link: http://blog.cryos.net/archives/54-Got-My-New-System-Working.html
date: 2005-10-01 17:01:45.000000000 +00:00
---
Got my new system up and running yesterday. I would like to thank Mastercard and NatWest for helping my to purchase a new PSU, motherboard, graphics card and AMD Althlon64 X2 3800+! I haven't worked out all the fine details of how I will pay them back just yet, but I do have a beautiful new system up and running!<br />
<br />
Thanks to Gentoo it took virtually no effort at all. Flashed the BIOS to the latest version, plugged in my old hard drive. Everything booted but a few things weren't working so I just recompiled the kernel with SMP support, PCI express support and the forcedeth module for the different network interdace. Rebooted and it was all working great. I do have this really weird issue where it seems to reboot on a cold boot after entering run level 3, then on a second boot everything boots fine.<br />
<br />
The system has clock issues too - it gains time at quite an incredible rate. I have even found ntpd having trouble keeping up when it is under load! Hopefully I will get some time to do a little work during the rest of the weekend. I am really hoping for some better luck when it comes to computer hardware too - I can't afford to replace anything else! The dual core processors seem pretty responsive so far too running on the gentoo-sources-2.6.13-r2. There is just the clock issue and the random reboot on cold start.
