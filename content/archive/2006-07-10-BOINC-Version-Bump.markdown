---
layout: post
title: BOINC Version Bump
categories:
- Gentoo
permalink: "/archives/97-BOINC-Version-Bump.html"
s9y_link: http://blog.cryos.net/archives/97-BOINC-Version-Bump.html
date: 2006-07-10 16:58:00.000000000 +00:00
---
I have finally bumped BOINC to version 5.5.6 today. There was some messing that had to be done, but it seems to be working better and I have already had reports of it fixing at least one build issue. I would appreciate testing on it and any feedback. I am thinking about removing the server USE flag as there is virtually no-one who is going to use that functionality and it only seems to cause issues. Furthermore I cannot test whether it even works properly and if you are running your own project you can probably add a line to the ebuild without any trouble.<br />
<br />
The problem I have now is in updating the SETI@Home client. It fails to build for me here on my amd64 systems. Haven't had chance to test it on one of my x86 systems yet. I have been trying the 5.17 sources from today's snapshot of the enhanced client. Their CVS seems broken as when I check it out from their files are missing. The file vector/analyzeFuncs_x86_64.cpp is throwing errors on check_suspend_flag not declared in this scope... If anyone has any ideas on this I would love to hear them. I am using GCC 4.1.1 and it could well be an issue with that but I don't want to add new stuff that doesn't work with it. I got an assembler warning too.<br />
<br />
I am pretty busy so I am not sure if I will get the time to revisit this any time soon. I built the enhanced snapshot from today against the 5.5.6 boinc sources in the tree. So any ideas please comment on this post, comment on a boinc bug in bugzie or send me an email. Hopefully this weekend I will get chance to poke around and see what other distros are doing too.
