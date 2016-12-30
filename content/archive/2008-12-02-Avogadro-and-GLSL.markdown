---
layout: post
title: Avogadro and GLSL
categories:
- Avogadro
- Chemistry
- KDE
- Linux
permalink: "/archives/197-Avogadro-and-GLSL.html"
s9y_link: http://blog.cryos.net/archives/197-Avogadro-and-GLSL.html
date: 2008-12-02 18:23:00.000000000 +00:00
---
<span><p>Last night I finally found a little time to look at <a href="http://en.wikipedia.org/wiki/GLSL">GLSL shaders</a> and how best to integrate some into <a href="http://avogadro.sourceforge.net/">Avogadro</a>. I had been meaning to do this for quite some time but there is always so much to do and so little time! First problem I had was actually accessing the functions to use GLSL shaders. In the end I found a great little library called <a href="http://glew.sourceforge.net/">GLEW</a> that lets me test for OpenGL 2.0 and then ensures all the functions are available.</p>

<center><img src="http://blog.cryos.net/uploads/avo-benzene-gl.png" width="200" height="200" alt="Avogadro rendered atoms without any special shaders" /><img src="http://blog.cryos.net/uploads/avo-benzene-glsl.png" width="200" height="200" alt="Avogadro rendered atoms with an OpenGL 2.0 phong shader" /></center>

<p>Both of the images were rendered using medium quality. The one on the left is not using any GLSL shaders and the one on the right is using a phong style GLSL shader. I am not sure it is very optimised, and right now the code needs cleaning up a little before I can commit it. I think it is another great option to use on higher end systems while maintaining compatibility with older systems.</p>

<p>Hopefully I will have more time to play with shaders soon. I wrote a flattening shader that looks pretty cool too. I think that shaders introduce a level of flexibility to our rendering pipeline but I have so much to learn. Being able to effectively ray trace on the GPU is great!</p></span>
