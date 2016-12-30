---
layout: post
title: Getting kinky with Gentoo
categories:
- Gentoo
permalink: "/archives/123-Getting-kinky-with-Gentoo.html"
s9y_link: http://blog.cryos.net/archives/123-Getting-kinky-with-Gentoo.html
date: 2007-01-06 19:26:00.000000000 +00:00
---
I wonder what kind of search results this entry might end up in - I hope jforman doesn't come after me <img src="http://blog.cryos.net/templates/default/img/emoticons/wink.png" alt=";-)" style="display: inline; vertical-align: bottom;" class="emoticon" /> Just spend the last hour or so avoiding my thesis and fixing inklevel monitoring on my system. I have fixed <a kref="http://packages.gentoo.org/search/?sstring=libinklevel">net-print/libinklevel</a> so that it is multilib friendly in the latest 0.6.6 release candidate that is in the tree and then found out that <a href="http://kink.sourceforge.net/">net-print/kink</a> was unhappy.<br />
<br />
So then I spent quite a while figuring out what had changed and patching kink to work with the new API. This fixed <a href="http://bugs.gentoo.org/show_bug.cgi?id=147967">bug 147967</a> but I was a bad dev and forgot to refer to the bug in my commit message... Now I have my new ink cartridge in my printer, I can print out drafts and papers again! So now I really will get back to writing up my thesis but I feel better as I managed to make a little time for Gentoo work <img src="http://blog.cryos.net/templates/default/img/emoticons/smile.png" alt=":-)" style="display: inline; vertical-align: bottom;" class="emoticon" />
