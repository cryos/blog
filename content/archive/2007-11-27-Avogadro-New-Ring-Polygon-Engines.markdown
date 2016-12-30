---
layout: post
title: 'Avogadro: New Ring & Polygon Engines'
categories:
- FOSS
- GSoC
- KDE
- Linux
permalink: "/archives/165-Avogadro-New-Ring-Polygon-Engines.html"
s9y_link: http://blog.cryos.net/archives/165-Avogadro-New-Ring-Polygon-Engines.html
date: 2007-11-27 03:58:52.000000000 +00:00
---
<span><p>I recently added a couple of new engines to <a href="http://avogadro.sourceforge.net/">Avogadro</a> and the screen shot below shows them both. The ring engine finds all the rings of the molecule and draws a transparent plane through the ring. The polygon engine finds atomic centres with three or more atoms bonded and draws a polygon around that atom. This is only done for atoms that are not the common organic types.</p>

<center><img src="http://blog.cryos.net/uploads/avogadro_rings_polygons.png" width="426" height="434" alt="Avogadro using the ring and polygon engines" title="Avogadro using the ring and polygon engine" /></center>

<p>I think these are useful engines that have been prompted by user requests. May be not as exciting as the ribbon engine or the surface support we are working on but useful to display certain structures. The ring engine has not been without its problems though as you can probably spot in the image below showing the ring engine rendering a carbon nanotube.</p>

<center><img src="http://blog.cryos.net/uploads/avogadro_nanotube_rings.png" width="426" height="434" alt="Avogadro using the ring engine to render a nanotube" title="Avogadro using the ring engine to render a nanotube" /></center>

<p>The lighting just flips at certain points - the same happens as you rotate molecules that are using the ring or polygon engine. I guess the lighting is flicking on at certain angles. I would be interested if anyone with more OpenGL knowledge than I might know how I can improve the rendering. Some rings are near white and some of the back rings don't seem to be drawn - that could actually be drawing order though which is always tough to get right.</p>

<p>Comments and tips are always welcome. The big challenge right now is getting surface support added in. This is something I think we really need and I would use in my daily work as I am sure many others would. I have been reading up on marching cubes and stuff but would welcome tips in that area too!</p></span>
