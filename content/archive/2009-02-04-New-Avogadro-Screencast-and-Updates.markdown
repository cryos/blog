---
layout: post
title: New Avogadro Screencast and Updates
categories:
- Avogadro
- Chemistry
- KDE
permalink: "/archives/208-New-Avogadro-Screencast-and-Updates.html"
s9y_link: http://blog.cryos.net/archives/208-New-Avogadro-Screencast-and-Updates.html
date: 2009-02-04 04:04:27.000000000 +00:00
---
<span><p>I made a new <a href="http://avogadro.openmolecules.net/">Avogadro</a> screencast earlier today, trying new formats and preparing a showcase of features in the recent <a href="http://avogadro.openmolecules.net/wiki/Avogadro_0.9.0">0.9.0 release</a>. Unfortunately, due to an API change in <a href="http://eigen.tuxfamily.org/">Eigen</a> this release only builds with eigen-2.0_beta6. The sources in git work with the recently released eigen-2.0, and I will try to make a new release in the near future.</p>

<center><embed src="http://blip.tv/play/AeqzMQA" type="application/x-shockwave-flash" width="800" height="622" allowscriptaccess="always" allowfullscreen="true"></embed></center>

<p>The video shown above, is also available on <a href="http://www.youtube.com/watch?v=pyIDicmphik">YouTube</a>, but the encoding does not look as good as on <a href="http://blip.tv/file/1734564">blip.tv</a>. It shows off several of the features present in the current Avogadro release. There are a few issues with the Windows installer, which is another reason to put a small bug fix release out soon.</p>

<p>I have been putting my newly acquired <a href="http://www.cmake.org/>CMake</a> book to great use by working on improvements to our build system. I found out first hand just how long <a href="http://www.qtsoftware.com/">Qt</a> takes to compile in a Windows virtual machine, I do have a working Windows build environment now. I got <a href="http://www.cdash.org/">CDash</a> working for our project, even without unit tests it is great for flagging build errors/warnings on multiple platforms. I also have CPack generating our NSIS based Windows installer now. There are a few rough edges remaining that I hope to iron out soon, but I think our packaging just got a lot easier - thanks to Bill and <a href="http://www.kitware.com/">Kitware</a>.</p>

<p>Things have been really hectic since I got back from <a href="http://camp.kde.org/">Camp KDE</a>. Had a great time, met lots of really interesting people, did not sleep very much (need to take ear plugs next time) and found my Eee PC with <a href="http://www.kde.org/">KDE 4.2</a> (rc at the time) worked great the whole week, and it is so light.</p>

<p>When I got back I found out that our espresso machine broke, and the electronics shop declared it a lost cause earlier today <img src="http://blog.cryos.net/templates/default/img/emoticons/sad.png" alt=":-(" style="display: inline; vertical-align: bottom;" class="emoticon" /> This has meant a serious espresso shortage since my return! Why do they always concentrate on redundant power systems for the clusters, but not redundant espresso systems for the researchers???</p>

<p>So really busy right now, hopefully good news coming soon on several fronts - keep your fingers crossed! I am loving KDE 4.2, CMake and Qt but in dire need of espresso products <img src="http://blog.cryos.net/templates/default/img/emoticons/wink.png" alt=";-)" style="display: inline; vertical-align: bottom;" class="emoticon" /></p></span>
