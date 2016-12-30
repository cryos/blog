---
layout: post
title: 'AMD64 Based PVR: Part 1 - The Adventure Begins'
categories:
- FOSS
- General
- Gentoo
- Hardware
- Linux
permalink: "/archives/69-AMD64-Based-PVR-Part-1-The-Adventure-Begins.html"
s9y_link: http://blog.cryos.net/archives/69-AMD64-Based-PVR-Part-1-The-Adventure-Begins.html
date: 2006-02-05 16:04:13.000000000 +00:00
---
Well I had an old motherboard with an Athlon64 3200+ in it (previous burnt out PSU that wasn't quite as bad as it looked). So I bought 1 GB of RAM, a new PSU, a Hauppage PVR-500, used my old nVidia GeForce FX5900XT and a DVD drive for it. I installed Gentoo amd64 on it of course and then began my first attempt at MythTV.<br />
<br />
I have TV out working and I can play DVDs, although I am using xine instead of mplayer for the DVD menu support. The TV tuners are recognised but all I get is static. I was working with this <a href="http://gentoo-wiki.com/HARDWARE_PVR_500_Setup">wiki article</a>. I also have messages like this in dmesg, <tt>ivtv1: i2c attach to card #1 ok [client=(tuner unset), addr=61]</tt> which I think is my tuner failing to get set up properly.<br />
<br />
It looks like the infrared receiver/IR blaster doesn't work either, it is USB based and came with the package. I get <tt>ID 0609:031d SMK Manufacturing, Inc.</tt> when I plug it in but no lirc devices <img src="http://blog.cryos.net/templates/default/img/emoticons/sad.png" alt=":-(" style="display: inline; vertical-align: bottom;" class="emoticon" /> This means that the remote is also unusable. So far I have had limited success, but I am hopeful I will be able to improve and document the set up in future. I am currently using,<br />
<br />
media-tv/ivtv-0.4.2<br />
media-tv/xmltv-0.5.39  - current stable is unable to parse UK TV listings<br />
media-tv/mythtv-0.18.1-r2<br />
app-misc/lirc-0.8.0_pre3
