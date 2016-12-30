---
layout: post
title: My New Acer Ferrari 4005WLMi and Gentoo
categories:
- FOSS
- General
- Gentoo
- Hardware
- Linux
permalink: "/archives/44-My-New-Acer-Ferrari-4005WLMi-and-Gentoo.html"
s9y_link: http://blog.cryos.net/archives/44-My-New-Acer-Ferrari-4005WLMi-and-Gentoo.html
date: 2005-09-13 00:10:00.000000000 +00:00
---
I got a few new toys delivered to me last week. On Thursday I got a Fuji F10 6.3 MP digital camera which is a really great camera - take a look <a href="http://www.fujifilm.co.uk/digital/cameras/f10/?lpage=/digital/cameras/range.php">here</a> for more details. It was recognised as a USB mass storage device without any trouble in Gentoo and I have been doing everyone's head in taking pictures of everything. It is a replacement for my old Sony Cybershot which met its ultimate end on the last night of my stag week in Tenerife... I got a 1 GB xD memory card and a spare battery for it too!<br />
<br />
The biggest new toy arrived on Friday though, which is my new Acer Ferrari 4005WLMi laptop, specs are <a href="http://www.acer.co.uk/acereuro/page4.do?dau22.oid=10477&UserCtxParam=0&GroupCtxParam=0&dctx1=17&CountryISOCtxParam=UK&LanguageISOCtxParam=en&crc=3887355547">here</a>. This is a great laptop, and I read loads of reviews before purchasing it. As soon as I got it on Friday morning I repartitiioned and starting installing Gentoo on it of course <img src="http://blog.cryos.net/templates/default/img/emoticons/smile.png" alt=":-)" style="display: inline; vertical-align: bottom;" class="emoticon" /> The initial install went fairly well, and I got it to boot without too many problems. Unfortunately it comes with a broken ACPI DSDT so the battery readout was broken - I wish manufacturers would try getting stuff like this right. Fortunately those before me had already fixed this.<br />
<br />
I am afraid that laptops don't seem to have gotten much easier to get working... I installed straight from 2005.1 amd64 stages, and built a multilib system. During my research I found a few useful pages scattered across the web with installation details. An <a href="http://www.fwconsult.com/laptop-install.html">Acer 5021NWLCi</a> installation of Gentoo, as well as a user on the Gentoo wiki who installed it on the same model I have <a href="http://gentoo-wiki.com/HARDWARE_Gentoo_Acer_Ferrari_4005WLMi_Manual">here</a> which has been useful in providing quite a few pointers and fixes.<br />
<br />
I installed using gentoo-sources-2.6.13 and upgraded to -r1 over the weekend. I had to apply one patch to the kernel - <a href="http://forums.gentoo.org/viewtopic.php?t=122145">to load the updated DSDT file from an initrd during boot</a>. I am using ndiswrapper to use my broadcom wireless network card, and I have finally managed to get WEP encryption working. I got the Windows XP 64 bit driver from <ahref="ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit">Acer FTP</a>. Unfortunately I have not been able to get wpa_supplicant working so far - any tips greatfully received <img src="http://blog.cryos.net/templates/default/img/emoticons/wink.png" alt=";-)" style="display: inline; vertical-align: bottom;" class="emoticon" /> I also got a new Linksys WRT54GC wireless router to power my new wireless network too.<br />
<br />
The integrated memory card reader doesn't work, and it doesn't look like there is much chance of getting it working which is a shame as that functionality would be nice to have. I am getting APIC errors on the CPU which is a little worrying too, but doesn't seem to be causing issues. The touchpad is working great, but I still can't get the bluetooth mouse working reliably either - I think I am missing something here but I need to get back to some real work!<br />
<br />
Productivity has been terrible on my PhD work, Gentoo and consultancy stuff whilst getting this laptop working! Hopefully now I will get back to being even more productive.
