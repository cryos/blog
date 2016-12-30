---
layout: post
title: System Freezes Caused by the Proprietary Nvidia Driver
categories:
- FOSS
- Gentoo
- Hardware
- Linux
permalink: "/archives/42-System-Freezes-Caused-by-the-Proprietary-Nvidia-Driver.html"
s9y_link: http://blog.cryos.net/archives/42-System-Freezes-Caused-by-the-Proprietary-Nvidia-Driver.html
date: 2005-09-04 18:12:00.000000000 +00:00
---
Today my system locked up yet again, and as far as I can tell this is due to the proprietary Nvidia driver I use and has been present for many driver versions. I keep meaning to look into this problem further and then it gets better and I forget again. I can use the nv driver to get rid of the problem, but lose all 3D acceleration too. How many others have this problem?<br />
<br />
After googling it appears that it could be a problem with something in the OpenGL part of the driver, and so I have turned off the OpenGL screensaver I was using as a test. It also seems to be more common when the system is under heavy load too. I have wondered if it might be a problem with TwinView, which I use with my two 17" TFT screens. It is certainly an irritating bug - it is usually necessary to ssh into the system and kill -9 the X process to fix it.<br />
<br />
The normal error message accompanying these crashes in /var/log/messages is,<br />
<tt>Aug 27 04:48:02 cryos NVRM: Xid: 25,  L1 -> L0<br />
Aug 27 04:48:02 cryos NVRM: Xid: 13, 0000 02003900 00000039 00000328 00000000 00000800</tt><br />
<br />
After searching on this I found a couple of posts <a href="http://www.nvnews.net/vbulletin/showthread.php?t=49117&highlight=Xid">here</a> and <a href="http://www.nvnews.net/vbulletin/showthread.php?t=55261">here</a>. Also another here suggesting it could be an X86_64 issue <a href="http://www.nvnews.net/vbulletin/showthread.php?t=55476">here</a>. A post <a href="http://lists.debian.org/debian-user/2005/05/msg00925.html">here</a> also indicates very similar issues with Debian. This <a href="http://bugs.gentoo.org/show_bug.cgi?id=86353">bug</a> seems to be a similar issue.<br />
<br />
I haven't been able to get any more information than the log messages above, and the fact that X gets stuck in a loop consuming 100% of the CPU cycles until it is killed. Not even the keyboard/mouse respond so you need a second system to log in with... I guess this is the problem with a black box binary linked into my kernel - there is no way to debug it. Submitted a bug report to nVidia about a year ago and never received a reply from them.<br />
<br />
I have tried enabling and disabling all sorts but nothing seems to change it, and the crashes only happen every day to every few weeks over different xorg-x11 versions and nvidia-kernel versions. It also doesn't affect my work system which is very similar, but only has one TFT screen and a lower end nvidia graphics card...
