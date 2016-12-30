---
layout: post
title: MADWiFi Working on AMD64 Again
categories:
- FOSS
- Gentoo
- Hardware
- Linux
permalink: "/archives/65-MADWiFi-Working-on-AMD64-Again.html"
s9y_link: http://blog.cryos.net/archives/65-MADWiFi-Working-on-AMD64-Again.html
date: 2006-01-20 18:25:22.000000000 +00:00
---
Well they finally fixed the new MADWiFi driver to work with AMD64 again, after about two months or so of it causes a kernel oops whenever traffic was transmitted over the wireless link. I have been too busy to get a new card and so I am still using this one. Still not happy about the closed source HAL and think the reasoning behind it is flaky. It is little better than a proprietary driver, but the old driver worked and thanks to brix the new driver is in portage already and has been rekeyworded ~amd64.<br />
<br />
Hopefully wireless in Linux will improve soon, I don't think closed source drivers are the answer though. In other news I have also brought the latest version of boinc out of package.mask to receive wider testing. It seems to be working pretty well, but still isn't as smooth as I would like. If anyone has ideas on how to improve it, or better yet patches, I would love to hear from you.
