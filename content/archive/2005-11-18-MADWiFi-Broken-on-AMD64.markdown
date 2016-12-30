---
layout: post
title: MADWiFi Broken on AMD64
categories:
- Gentoo
- Hardware
- Linux
permalink: "/archives/60-MADWiFi-Broken-on-AMD64.html"
s9y_link: http://blog.cryos.net/archives/60-MADWiFi-Broken-on-AMD64.html
date: 2005-11-18 21:02:00.000000000 +00:00
---
I had to mark net-wireless/madwifi-driver-0.1_pre20051111 -amd64 as it just causes kernel panics. Until today I have not been able to bring up their web site (database errors or timeouts). Downgrading doesn't seem to work either, and I have been really busy so I have just been using my wired network. I actually bought this Atheros based miniPCI wireless card as I was led to believe it worked better than the Broadcom card I had under Linux! They seem to know about the <a href="http://www.madwifi.org/ticket/74">issue</a>, but it has not been solved yet.<br />
<br />
Now I am thinking that may be I need to look at buying another wireless card <img src="http://blog.cryos.net/templates/default/img/emoticons/sad.png" alt=":-(" style="display: inline; vertical-align: bottom;" class="emoticon" /> I think a closed source HAL is just about as bad as a closed source driver... Preferably one that might even make it into the kernel with a fully open source driver such as Ralink 2500 chipsets possibly. There have been some attempts at making an open source HAL for the Atheros chip but they do not seem to have come to much as far as I can tell.
