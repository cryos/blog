---
layout: post
title: Improved Ribbon Rendering
categories:
- FOSS
- KDE
- Linux
permalink: "/archives/163-Improved-Ribbon-Rendering.html"
s9y_link: http://blog.cryos.net/archives/163-Improved-Ribbon-Rendering.html
date: 2007-11-06 20:30:00.000000000 +00:00
---
<span><p>Over the last couple of days I have made a few commits to improve the ribbon support in <a href="http://avogadro.sourceforge.net/">Avogadro</a>. Many thanks to <a href="http://geoffhutchison.net/blog/">Geoff</a> for fixing some bugs we found in <a href="http://openbabel.sourceforge.net/">Open Babel</a> and to <a href="http://thomasmargraf.org/">Thomas Margraf</a> for his helpful suggestions and for letting me take a look at a little of his code that renders ribbons.</p>

<center><img width="169" height="200" src="http://blog.cryos.net/uploads/avo-20071106.serendipityThumb.png" alt="Ribbon rendering in Avogadro" title="Ribbon rendering in Avogadro" /></center>

<p>Right now the ribbon is drawn as a tube between the carbon atoms of the backbone and so isn't really a ribbon at all. Then I looked at the image and it is looking quite a bit like a ribbon. The code is checked in and so feel free to take a look at it. I am using NURBS but am far from an expert on their use. My laptop failure has lost some of the tuning I had done too - this is my first screenshot from Apple Mac OS X Leopard!</p>

<p>Points if you can tell me why the alpha helix looks pretty good despite me having not yet implemented anything to find the correct plane! Still needs some tuning but I hope you will agree that this is looking pretty nice now. It has also led to some optimisation of molecule loading but I am sure that there are lots of biologists who will tell me it still isn't quite right.</p>

<p><strong>Update:</strong> Geoff has now shown me how to do screen capture and so here is a pretty video of Avogadro rendering ribbons in action!</p>
<center><object width="425" height="350"> <param name="movie" value="http://www.youtube.com/v/rSa-Pu0YVhg"> </param> <embed src="http://www.youtube.com/v/rSa-Pu0YVhg" type="application/x-shockwave-flash" width="425" height="350"> </embed> </object></center></span>
