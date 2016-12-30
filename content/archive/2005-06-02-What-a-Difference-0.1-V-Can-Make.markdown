---
layout: post
title: What a Difference 0.1 V Can Make
categories:
- General
- Gentoo
- Hardware
- Linux
permalink: "/archives/32-What-a-Difference-0.1-V-Can-Make.html"
s9y_link: http://blog.cryos.net/archives/32-What-a-Difference-0.1-V-Can-Make.html
date: 2005-06-02 18:00:17.000000000 +00:00
---
I meant to write about this last week. My main amd64 box crashed the other week and managed to clear the BIOS settings along with it. It is a socket 754 Gigabyte board that I have never had too much luck with. They limit the RAM to DDR333 instead of DDR400 as they incorrectly quote AMD specs - I have built other systems using the same two sticks of double sided 512 MB DDR400 Corsair RAM!<br />
<br />
Anyway, reset all the settings I could remember, and it all seemed OK. Then kept getting random crashes and segfaults and thought it was a bad kernel or something. Played with all sorts of settings, and even rebooted into Gentoo on another partition. Ram memtest86+ and it all passed just fine. At the point of pullling my hair out I took a breather and then thought may be upping the RAM voltage would help.<br />
<br />
Did that and I have not had a single crash/segfault since! As I said what a difference 0.1 V can make <img src="http://blog.cryos.net/templates/default/img/emoticons/smile.png" alt=":-)" style="display: inline; vertical-align: bottom;" class="emoticon" /> Lost half a week messing about with it, but got it sorted in the end...
