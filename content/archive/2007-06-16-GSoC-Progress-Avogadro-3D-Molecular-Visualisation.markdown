---
layout: post
title: 'GSoC Progress: Avogadro 3D Molecular Visualisation'
categories:
- GSoC
- KDE
- Linux
permalink: "/archives/142-GSoC-Progress-Avogadro-3D-Molecular-Visualisation.html"
s9y_link: http://blog.cryos.net/archives/142-GSoC-Progress-Avogadro-3D-Molecular-Visualisation.html
date: 2007-06-16 14:39:00.000000000 +00:00
---
<span><p>I have had a really productive week. I have been doing lots of reading to learn the finer points of the Qt plug in system, OpenGL projections and transformations. I have also found and hunted down a few bugs and added some really cool visualisations to Avogadro.<p>

<center><img src="http://blog.cryos.net/uploads/avo20070616.png" width="457" height="429" alt="Avogadro transparent VdW view" /></center>

<p>I am especially pleased with the transparent Van der Waals view with the molecular backbone. I am not sure if I am rendering it in an optimal way right now as it requires three passes - one to render the molecular backbone, one to render totally transparent VdW spheres and a final pass to render the VdW spheres with the specified transparency. I hope you agree that the result is certainly very pleasing visually and I think it gives a good sense of both the molecular structure and how much space it fills.</p>

<p>I have done lots of other things this week. Bond labels have been added as an option for the label engine along with improvements to the rendering engines to actually return a valid bond radius. I added a setAlpha function to the Color class so that the alpha value of a colour can be altered without affecting its colour.</p>

<p>There is a new axes engine that renders the x, y and z axes to the screen. It works reasonably well but still needs several improvements to be implemented. Our text drawing routines don't draw into the current OpenGL projection matrix and so I couldn't label the axes. The vectors I get for the x, y and z axes are also not of uniform length as I wanted - if you have a rectangular view of the molecule the axes are rendered at different lengths. It is certainly helpful having the axes available even in their current form but I need to figure out a few more features before I will be happy with them.</p>

<p>I added a new auto rotation tool this week too. It allows you to rotate the molecule about the views x, y and/or z axes at variable speeds in order to get a complete view of the molecule. I have already tweaked the configuration quite a bit. I did want to make a derived QWidget to have a little more control over the configuration widget, but every time I linked to my derived QWidget class the tool failed to load - still not figured out why and it has been insanely frustrating. If you know why I would love to know! Probably a gap in my Qt skill set - I have a book on the way that promises to teach me the finer points of Qt 4 and am very good friends with the docs bundled with Qt <img src="http://blog.cryos.net/templates/default/img/emoticons/wink.png" alt=";-)" style="display: inline; vertical-align: bottom;" class="emoticon" /></p>

<p>I also added a couple of higher detail levels and have used the highest in the screenshot above. It produces really nice spheres but there is quite a performance hit and I don't think it would perform well with lots of atoms or on unaccelerated graphics cards. Hopefully ATI/AMD will be releasing a nice open source accelerated driver soon. Next week I will be focusing on threads and have already done quite a bit of reading on the subject. Wish me luck.</p></span>
