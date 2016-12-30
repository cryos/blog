---
layout: post
title: 'Avogadro: Surface Support'
categories:
- Avogadro
- Chemistry
- FOSS
- GSoC
- KDE
- Linux
permalink: "/archives/172-Avogadro-Surface-Support.html"
s9y_link: http://blog.cryos.net/archives/172-Avogadro-Surface-Support.html
date: 2008-02-11 16:50:00.000000000 +00:00
---
<span><p>I am pleased to announce that we now have working surface support in Avogadro. We originally began working on support for surfaces around November time when <a href="http://geoffhutchison.net/blog/">Geoff</a> improved the support in <a href="http://openbabel.sourceforge.net/">OpenBabel</a> for grids and added some initial code to the <a href="http://avogadro.souceforge.net/">Avogadro</a> repository. Quite quickly it became evident that this algorithm did not deal well with data sets containing discrete objects that you wanted to polygonise.</p>

<p>I began a search of the available algorithms and came across a very nice <a href="http://local.wasp.uwa.edu.au/~pbourke/geometry/polygonise/">guide to the marching cube algorithm</a> with example code. I had a brief look for a C++ implementation and didn't find anything initially, began implementing what was on his page and then came across <a href="http://sourceforge.net/projects/zhu3d/">Zhu3d</a> which is a Qt 4 based program that actually uses an implementation of the algorithms described in the guide and references them. As it is GPL licenced code I imported the relevant class into our repository and began the task of adapting it to fit into our framework.</p>

<center><img src="http://blog.cryos.net/uploads/avo-surface1.png" width="468" height="528" alt="Avogadro surface points" /><img src="http://blog.cryos.net/uploads/avo-surface2.png" width="468" height="528" alt="Avogadro surface lines" /></center>

<p>With some code from Geoff, more pointers from Geoff, some reading and quite a bit of help from Tim (not sure if he has a web page/blog) we got it working. Since then Tim has actually fixed a big bug in OpenBabel that was causing crashes and done more work on the IsoGen class. The screenshots above show the results of our early work where initially we got points and then lines working. I was very pleased at this stage as it adds a feature that had been missing for quite some time to the Avogadro framework.</p>

<center><img src="http://blog.cryos.net/uploads/avo-surface3.png" width="468" height="528" alt="Avogadro surface with filled triangles" /><img src="http://blog.cryos.net/uploads/avo-surface4.png" width="468" height="528" alt="Avogadro surface with filled triangles coloured by electrostatic charge" /></center>

<p>I then got filled triangles added with transparency support, allowing us to visualise the underlying structure of the molecule and map other parameters onto the surface. Tim then added electrostatic charge mapping to the colour of the surface which I hope you agree is already looking very good.</p>

<p>There is still quite a bit left to do. I need to move the class into libavogadro and out of the engines, integrate it into our Painter API, implement caching and am thinking of using the Qt Concurrent framework to do intelligent multithreading once Qt 4.4 is released as surface generation is quite slow for big molecules. I also need to link the mesh size to the global quality level and see what other optimisations might be possible. Another big one is adding support for visualising molecular orbitals. Geoff has already done a lot of work on the back end in OpenBabel for this and so hopefully it will not take me long to get it added in.</p>

<p>Lots to do but some great progress already. I would love to know what you think. Once we have been able to polish this new feature a little I hope we can get a release out of the door so that more people can test out these new features and let us know what they think, point out bugs and shower us with compliments <img src="http://blog.cryos.net/templates/default/img/emoticons/wink.png" alt=";-)" style="display: inline; vertical-align: bottom;" class="emoticon" /> Until then I hope you enjoy the screenshots!</p>

<p><strong>Note:</strong> For some reason the exported graphics shown in this post were not antialiased. They are on screen and I need to look into why they are not when I export graphics in this way.</span>
