---
layout: post
title: New Webcam and Linux
categories:
- General
- Gentoo
- Linux
permalink: "/archives/183-New-Webcam-and-Linux.html"
s9y_link: http://blog.cryos.net/archives/183-New-Webcam-and-Linux.html
date: 2008-06-17 03:29:08.000000000 +00:00
---
<span><p>As my regular readers will know I moved over to Pittsburgh, PA in the USA at the end of September last year. Before I left I got some of mine and Louise's family webcams so that we could stay in touch. Then it took ages to sell our house and the shipping nightmare began (which I will try and bring myself to talk about one of these days). Eventually I actually got my desktop computer back (a little worse for wear after the shippers "carefully packaged it").</p>

<center><img src="http://blog.cryos.net/uploads/logitech_quickcam_9000.jpg" width="500" height="335" alt="Logitech Quickcam Pro 9000" /></center>

<p>Going back to my original point, I had been putting off buying a webcam as I wanted it to work well in Linux, and every time I looked into which webcams might be my best bet it seemed that even individual models had multiple chipsets, which may or may not be supported. On Saturday I bit the bullet as Louise had been asking about getting <a href="http://www.skype.com/">Skype</a> working.</p>

<p>I chose the Logitech Quickcam Pro 9000 (photo above) as it seemed to be part of the new USB video class standard I had been reading about and saw there was a healthy <a href="http://linux-uvc.berlios.de/">Linux UVC project</a> already. I still anticipated having trouble getting it working on <a href="http://www.gentoo.org/">Gentoo</a> but thought I should be able to get it working eventually.</p>

<p>Imagine my surprise when I just typed <tt>emerge -av media-video/linux-uvc media-video/luvcview</tt>, modprobed the new kernel module, ran luvcview and I could see me staring at the camera! Sometimes I worry this Linux thing might be getting a little too easy <img src="http://blog.cryos.net/templates/default/img/emoticons/wink.png" alt=";-)" style="display: inline; vertical-align: bottom;" class="emoticon" /> Another five minutes and I had the microphone working (just usb audio) and was testing it out in Skype. On Sunday we had our first intercontinental video chat with my Mum and two nephews. Skype also integrates into my KDE 4 desktop without any trouble.</p>

<p>I am pretty new to the webcam thing and had resisted it for a while but it was great to be able to chat and see family and friends back home. I would rather use an open source, cross platform video conferencing application but have yet to find a viable one. <a href="http://www.openwengo.org/">Open Wengo</a> looks like it might be that application one day but I couldn't get it to work reliably last time I tried (although I did like the look of it). I also don't seem to be able to find a nice application that will let me capture video messages easily.</p>

<p>I was very pleasantly surprised by my experience and am very happy with the performance of the Linux drivers for the webcam as well as the camera itself. Any Linux webcam tips would of course be gratefully received!</p>

<p>UPDATE: Forgot to mention this <a href="http://blog.gnist.org/article.php?story=Linux_and_LogitechQuickCamPro9000">great blog post I spotted</a> that helped me decide this webcam was probably a good bet...</p></span>
