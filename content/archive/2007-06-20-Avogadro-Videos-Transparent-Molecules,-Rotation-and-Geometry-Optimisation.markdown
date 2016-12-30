---
layout: post
title: 'Avogadro Videos: Transparent Molecules, Rotation and Geometry Optimisation'
categories:
- GSoC
- KDE
permalink: "/archives/144-Avogadro-Videos-Transparent-Molecules,-Rotation-and-Geometry-Optimisation.html"
s9y_link: http://blog.cryos.net/archives/144-Avogadro-Videos-Transparent-Molecules,-Rotation-and-Geometry-Optimisation.html
date: 2007-06-20 18:36:00.000000000 +00:00
---
<span><p>I already wrote this post once, but the bit bucket ate it when my browser crashed... <a href="http://cniehaus.livejournal.com/">Carsten</a> and I were talking on IRC yesterday about the last post I made and progress with my project in general. He asked if I would try making a few videos demonstrating new features as his system has trouble capturing videos without dropping frames. I am new to the whole video capture scene and have always found screen shots to be enough in the past. He told me about <a href="http://xvidcap.sourceforge.net/">xvidcap</a> and so I emerged it. What else do people use for this kind of thing?</p>

<center><object width="425" height="350"><param name="movie" value="http://www.youtube.com/v/UYy95pBmGr0" /><param name="wmode" value="transparent" /><embed width="425" height="350" src="http://www.youtube.com/v/UYy95pBmGr0" type="application/x-shockwave-flash" wmode="transparent"></embed></object></center>

<p>After some trial and error (I found xdamage prevented the OpenGL window from being recorded properly) I recorded a video. The <a href="http://www.youtube.com/watch?v=UYy95pBmGr0">above video</a> is my first successful one, as uploaded to <a href="http://www.youtube.com/">YouTube</a> by Carsten. I don't know about you but I find flash very unreliable on my 64 bit system in my 64 bit browser as there is still no decent 64 bit flash plugin. You can get the <a href="http://cryos.net/avo20070619.mpeg">original video here</a> (~17MB) and my second attempt <a href="http://cryos.net/avogadro-transparency-rotation.mpeg">here</a> (~14MB) which I think is a little better personally.</p>

<center><object width="425" height="350"><param name="movie" value="http://www.youtube.com/v/azoFt01PTHU" /><param name="wmode" value="transparent" /><embed width="425" height="350" src="http://www.youtube.com/v/azoFt01PTHU" type="application/x-shockwave-flash" wmode="transparent"></embed></object></center>

<p>I made a new video this morning that is <a href="http://www.youtube.com/watch?v=azoFt01PTHU">shown above</a> and also available for <a href="http://cryos.net/avogadro-geometry-optimisation.mpeg">download here</a> (~5MB) showing some recent changes in Avogadro implemented by Donald - geometry optimisation now takes place in a separate thread. This was on my list of features to implement and I had done some reading and initial code (nothing that worked right). It is a great feature to have implemented as geometry optimisation can take quite some time. My research, reading and coding haven't been in vain either - I learned a lot about how Avogadro, OpenBabel and Qt interact as well as learning quite a bit about threads (never used them before). There are other things that will benefit from threading too, so I hope I will be able to do some coding with threads soon <img src="http://blog.cryos.net/templates/default/img/emoticons/smile.png" alt=":-)" style="display: inline; vertical-align: bottom;" class="emoticon" /></p>

<p>I would love to hear what you think about the videos, if they are useful demonstrations of new features in Avogadro. Most of this stuff is actually in libavogadro which is used by Avogadro. Kalzium uses a snapshot of libavogadro right now, in KDE 4.1 it should be possible to switch to the system copy of libavogadro. It is a great demonstration of how easy it is to add molecular visualisation capabilities to a program by using libavogadro. I am still learning lots of new stuff and thankfully the development team don't mind me asking questions, even when some of the questions are really stupid... I am still having a great time working on the code pushing the boundaries of what we can accomplish and hope that you find these posts informative.</p></span>
