---
layout: post
title: Avogadro Gets Some Sweet POV-Ray Goodness
categories:
- GSoC
- KDE
- Linux
permalink: "/archives/148-Avogadro-Gets-Some-Sweet-POV-Ray-Goodness.html"
s9y_link: http://blog.cryos.net/archives/148-Avogadro-Gets-Some-Sweet-POV-Ray-Goodness.html
date: 2007-07-18 14:08:00.000000000 +00:00
---
<span><p>It has been a while since I last posted about progress with Avogadro. I have been doing a lot of under the hood improvements which has been really frustrating at times and hard to blog about. Hey I just spent all day refactoring the Painter base class and everything still works the same as it did before! At last I have some real output and have just committed the code to the repository.</p>

<center><img src="http://blog.cryos.net/uploads/avogadropovray.png" width="317" height="508" alt="Ray traced molecule exported by Avogadro and ray traced by POV-Ray" /></center>

<p>The above image is one of the first I have produced and ray traced in POV-Ray. The abstracted painter stuff seems to be working really well and the engines no longer care whether they are painting onto an OpenGL context or to a file with POV-Ray objects in it. I think this is one of the most exciting aspects of the work I have been doing - the painting code has been somewhat abstracted away from the engines allowing for multiple painter devices.</p>

<p>I haven't just been coding though. I had a lot to think about after aKademy and have been reading a great deal about Qt and API design. I have also been reading the book that Google sent me about producing open source software. One suggestion I really like and I think most projects should be using is of code review, where each commit is reviewed by other members of the project. At times I think I would find it tough to review the code of other project members but I can see how it can really improve the quality of the code and help us see what other people are doing in the project.</p>

<p>I need to run as it is my nephews birthday today and I am expected. Hope you like the image. The POV-Ray export is extremely rough right now and needs a lot of things to be done before I would consider it ready for prime time. The philosophy of maintaining minimal local revisions also appeals to me though and so I am trying to stick to that too. I hope to be making much nicer images soon.</p></span>
