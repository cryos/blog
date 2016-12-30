---
layout: post
title: 'Avogadro Gets More Eye Candy: Improved Ray Tracing'
categories:
- Avogadro
- Chemistry
- KDE
- Linux
permalink: "/archives/198-Avogadro-Gets-More-Eye-Candy-Improved-Ray-Tracing.html"
s9y_link: http://blog.cryos.net/archives/198-Avogadro-Gets-More-Eye-Candy-Improved-Ray-Tracing.html
date: 2008-12-02 19:00:00.000000000 +00:00
---
<span>
<a class='serendipity_image_link' href='http://blog.cryos.net/uploads/benzene-homo.png' onclick="F1 = window.open('/uploads/benzene-homo.png','Zoom','height=620,width=820,top=300,left=560,toolbar=no,menubar=no,location=no,resize=1,resizable=1,scrollbars=yes'); return false;"><img class="serendipity_image_left" width="200" height="150" style="float: left; border: 0px; padding-left: 5px; padding-right: 5px;" src="http://blog.cryos.net/uploads/benzene-homo.serendipityThumb.png" alt="Benzene rendered using POV-Ray and Avogadro" /></a>

<p>I seem to have made quite a few breakthroughs in the last week or so, and have hardly had the time to talk about them. May be it is due to a bout of insomnia and feeling inspired. I was talking to Geoff about some of the ray tracing work I have been doing. After revisiting a few of the early decisions I made and reading some of the <a href="http://www.povray.org/">POV-Ray</a> documentation I have managed to make several improvements to the POV-Ray output. The rendering of the highest occupied molecular orbital for benzene looks a lot better (left). I have also been looking at the actual POV-Ray scene descriptions Avogadro outputs and making them as easy to modify as possible.</p>

<p>Geoff recently added a new atom colouring method, colour by atom index, which can give some really nice rainbow like effects. To the left is a large bucky ball rendered by Geoff on a Mac using <a href="http://megapov.inetart.net/">MegaPOV</a>, and to the right is a nanotube I rendered using the latest beta of <a href="http://www.povray.org/">POV-Ray</a> which actually split the rendering across all four cores here. Hopefully we will be able to make a new release containing some of these new features in the near future, along with integrating some of this new functionality into the Kalzium molecular editor.</p>

<a class='serendipity_image_link' href='http://blog.cryos.net/uploads/c540.png' onclick="F1 = window.open('/uploads/c540.png','Zoom','height=620,width=820,top=300,left=560,toolbar=no,menubar=no,location=no,resize=1,resizable=1,scrollbars=yes'); return false;"><!-- s9ymdb:104 --><img class="serendipity_image_left" width="200" height="150" style="float: left; border: 0px; padding-left: 5px; padding-right: 5px;" src="http://blog.cryos.net/uploads/c540.serendipityThumb.png" alt="Large bucky ball rendered using MegaPOV" /></a>

<a class='serendipity_image_link' href='http://blog.cryos.net/uploads/nanotube.png' onclick="F1 = window.open('/uploads/nanotube.png','Zoom','height=620,width=820,top=300,left=560,toolbar=no,menubar=no,location=no,resize=1,resizable=1,scrollbars=yes'); return false;"><!-- s9ymdb:106 --><img class="serendipity_image_right" width="200" height="150" style="float: right; border: 0px; padding-left: 5px; padding-right: 5px;" src="http://blog.cryos.net/uploads/nanotube.serendipityThumb.png" alt="Nanotube rendered using new Avogadro/POV-Ray code" /></a>

<p>Hope you are not too bored of all the visuals, I am working on plenty of other stuff in the backend and quantum sides, along with some really good work Tim is doing on wrapping our functionality for Python scripting. I even added our first unit tests over the weekend and hope to get at least our core classes covered over the coming weeks.</p></span>
