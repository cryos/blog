---
layout: post
title: 'VTK: New 2D API, Canvas and Charting Features'
categories:
- FOSS
- Kitware
permalink: "/archives/236-VTK-New-2D-API,-Canvas-and-Charting-Features.html"
s9y_link: http://blog.cryos.net/archives/236-VTK-New-2D-API,-Canvas-and-Charting-Features.html
date: 2009-12-24 19:13:00.000000000 +00:00
---
<span><p>Since joining <a href="http://www.kitware.com/">Kitware</a> in October, one of the first projects I was tasked with is revamping the 2D charting capabilities in <a href="http://www.vtk.org/">VTK</a> and <a href="http://www.paraview.org/">ParaView</a>. At first I was a little daunted as it meant digging through many of the internals of VTK, and breaking an assumption that is made in many parts of VTK - that everything being rendered is 3D.</p>

<p> A large portion of this work is also being driven by the InfoVis features in VTK, along with <a href="http://www.sandia.gov/Titan/">project Titan</a> that we work on with some really interesting people from <a href="http://www.sandia.gov/">Sandia National Labs</a>. The project grew quite a bit from its original scope, and I have now added some new <a href="http://www.vtk.org/Wiki/VTK/Charts/2DAPI">2D API</a> that uses OpenGL as a backend, with the scope to add further backends in the future. I have been working on optimizing the OpenGL case so that large data sets can be rendered interactively, and small data sets can be rendered with minimal lines of code whilst giving pleasing visual results.</p>

<a class="serendipity_image_link"  href='http://blog.cryos.net/uploads/ParaViewNewCharts.png' onclick="F1 = window.open('/uploads/ParaViewNewCharts.png','Zoom','height=785,width=1075,top=221,left=1401,toolbar=no,menubar=no,location=no,resize=1,resizable=1,scrollbars=yes'); return false;"><img class="serendipity_image_right" width="200" height="146"  src="http://blog.cryos.net/uploads/ParaViewNewCharts.serendipityThumb.png"  alt="ParaView with 2D API canvas based VTK chart" /></a>

<p>Then when considering user interaction with these 2D elements we decided that a higher level API would be useful, that could contain objects and propagate mouse events to items in the scene. So I set about prototyping a new <a href="http://www.vtk.org/Wiki/VTK/Charts/CanvasAPI">canvas based API</a>. At this point I had enough new infrastructure that I felt it was about time I got back to my original task of implementing some efficient, well rendered 2D charts in VTK. Once I had my initial prototype in place it was time to expose this in ParaView and see how everything fitted together. As you can see in the screenshot above, things are shaping up very nicely. The new chart is in the bottom right widget, the chart above is the existing chart widget.</p>

<p>I have really enjoyed my first few months at Kitware, and have found my first project both challenging and rewarding. It is great to be working on real problems that have a broader impact, and as I flesh out these features I will try to maintain cross platform, high performance interactive charts. I think I have also added some useful new 2D focused API that can also be rendered over the top of VTK's existing 3D visualizations, opening the door to some very exciting new views on data.</p>

<p>As a physicist I also feel it is interesting the symmetry - <a href="http://labs.trolltech.com/blogs/2009/11/18/qt3d-brings-qt-style-coding-to-3d/">Qt adds 3D to a 2D toolkit</a>, and at the same time I am adding 2D to a 3D toolkit. Hope you all have a Merry Christmas, and a Happy New Year. I will be <a href="http://www.noradsanta.org/en/index.html">tracking Santa</a> with my son this evening!</p>

<p><tt>Disclaimer: The opinions and musings in this post are mine, and not those of my employer. Any mistakes/inaccuracies are also mine, that said I would love to hear what people think of this new work.</tt></p></span>
