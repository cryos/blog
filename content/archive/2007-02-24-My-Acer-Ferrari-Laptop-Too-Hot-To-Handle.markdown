---
layout: post
title: My Acer Ferrari Laptop - Too Hot To Handle
categories:
- Gentoo
- Hardware
- Linux
permalink: "/archives/127-My-Acer-Ferrari-Laptop-Too-Hot-To-Handle.html"
s9y_link: http://blog.cryos.net/archives/127-My-Acer-Ferrari-Laptop-Too-Hot-To-Handle.html
date: 2007-02-24 21:16:00.000000000 +00:00
---
<span><p>In the last few months the CPU temperature of my Acer Ferrari 4005 laptop has been getting higher and higher when idle or under load. I suspected it was just some dust reducing cooling efficiency but hadn't had chance to check it out. I was also putting it off as laptops generally aren't that easy to get into. Last week I was compiling a few applications as I was testing them for keywording bugs and the laptop shut itself down.</p>

<p>I rebooted and then resumed the emerge. I spotted the CPU temperature was up at 95 C and shortly after the laptop shut itself down again. Since then I had just left it turned off until I got a chance to look at it today. I found a very helpful article <a href=" http://gentoo-wiki.com/HARDWARE_Gentoo_Acer_Ferrari_4005WLMi_Manual">on Gentoo and the Acer Ferrari laptop</a> which linked to a very helpful service manual as well as documenting how to get most of the hardware to work.</p>

<p>Twenty four screws later and I unclipped the keyboard to realise I didn't even need to undo any of the screws in order to clean the CPU heat sink and fan! I used the trusty blower that was intended for cleaning my SLR lenses to blow all the dust out of the fan and put the keyboard back. Booting back up and emerging something taxing showed a 25 C drop in temperature both idle and under load - and no sign of any more shutdowns.</p>

<p>I also spotted there is now a <a href="http://tifmxx.berlios.de/">project to get the integrated memory card reader working under Linux</a>. Apparently SD cards are already working (don't use them yet, but might if I manage to get hold of a Nikon D80) and xD support is planned which I would love to see as that it what my Fuji F10 uses. Looks like people have had success getting suspend to ram working too - I will have to see about getting that working when I get chance too.</p></span>
