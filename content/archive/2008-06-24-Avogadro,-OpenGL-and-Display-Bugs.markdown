---
layout: post
title: Avogadro, OpenGL and Display Bugs
categories:
- Avogadro
- Chemistry
- GSoC
- Linux
permalink: "/archives/184-Avogadro,-OpenGL-and-Display-Bugs.html"
s9y_link: http://blog.cryos.net/archives/184-Avogadro,-OpenGL-and-Display-Bugs.html
date: 2008-06-24 02:53:26.000000000 +00:00
---
<span><p>Before last summer I had never really done any OpenGL programming. Now I feel like I know a reasonable amount but certainly still have a lot to learn. I have an Acer Ferrari laptop with an ATI Radeon X700 discrete graphics card in it. I was using the proprietary driver for a while but it was so unstable it just wasn't worth using. I was hopeful after reading about AMD opening up the specs so that good 3D support can be added to the open source driver.</p>

<center><img src="http://blog.cryos.net/uploads/avo_surface_fill.png" width="368" height="420" alt="Avogadro showing a filled surface with incorrect colouring on ATI open source driver" /><img src="http://blog.cryos.net/uploads/avo_surface_lines.png" width="368" height="420" alt="Avogadro showing a surface with correct colouring on ATI open source driver" /></center>

<p>I have to say on the whole the 3D support has been getting better and better for the r300 chipset. I cannot enable the desktop effects in KDE 4.1 trunk without losing my OpenGL apps though. As you can see in the above screen shots filled surfaces also do not work. For some reason the colouring of the surface is incorrect, i.e. the colour is never changed. I am running the latest git sources of xorg, the ati drivers, x11-drm, mesa etc, thanks to Donald Berkholz. Avogadro seems hit <tt>File r300_render.c function r300Fallback line 360, Software fallback:ctx->RenderMode != GL_RENDER</tt> every time too.</p>

<p>There is <a href="https://bugs.freedesktop.org/show_bug.cgi?id=8273">an open bug report</a> that appears to be describing the same situation. I do wonder if it is possible that our OpenGL code could be improved to avoid this bug. I would love any tips on ensuring our OpenGL code is as compatible as possible. The surface rendering works correctly on all other platforms (Linux, Mac, Windows) and with other drivers as far as I know.</p>

<p>We also have an open bug report <a href="http://sourceforge.net/tracker/index.php?func=detail&aid=1905737&group_id=165310&atid=835077">where Avogadro segfaults on Linux systems using the savage driver</a>. This seems to be a consistent problem. I am afraid I do not have the hardware to test further, I have added further debug output to our initialisation routines - Avogadro crashes very early on. Again, any ideas on how I might fix this bug or at least exit gracefully would be great. Backtraces may help to at least see what functions are called before the crash but this might just be a driver bug.</p></span>
