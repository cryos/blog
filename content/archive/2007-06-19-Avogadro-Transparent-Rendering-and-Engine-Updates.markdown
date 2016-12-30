---
layout: post
title: Avogadro Transparent Rendering and Engine Updates
categories:
- GSoC
- KDE
permalink: "/archives/143-Avogadro-Transparent-Rendering-and-Engine-Updates.html"
s9y_link: http://blog.cryos.net/archives/143-Avogadro-Transparent-Rendering-and-Engine-Updates.html
date: 2007-06-19 13:06:00.000000000 +00:00
---
<span><p>When I initially implemented the transparent VdW engine for Avogadro I had the problem that any rendering of transparent objects must be done after the internal opaque objects have been rendered. So at the time I just implemented a ball and stick engine inside the VdW engine that was basically a copy of the ball and stick engine. I also mentioned that if we could set render order that would allow me to use any other engine if there was a way to ensure this engine was called after the others. The need for this had already been mentioned with respect to label rendering too.</p>

<center><img src="http://blog.cryos.net/uploads/avo20070619a.png" width="666" height="570" alt="Avogadro rendering of a functionalised C60 molecule using a transparent VdW engine with a stick backbone" /></center>

<p>Yesterday we discussed the engine rendering order needs on IRC and hashed out some ideas. Then my IRC connection went crazy (I think it was Freenode or the server I was connected to at least). Donald made some commits late last night (my time at least) and implemented flags for the engines to declare their roles and their transparency depth to order within particular roles. We now have a renderOpaque and renderTransparent function in each engine which should improve transparency rendering when combined with the rendering order enhancements.</p>

<p>The above image shows a rendered functionalised C60 molecule (one I worked with during my PhD research) using the transparent VdW engine with the stick engine rendering its backbone. It has allowed me to simplify the VdW engine whilst making it far more powerful as it can now use the ball and sick, stick or wire frame engine to render the structure inside the VdW surface. As we add more engines they can also be used with no further modification to this engine.</p>

<p>I am really pleased with the result and this particular visualisation shows the structure of the molecule very well. Lots more to do but I thought it would be nice to show how this display engine had progressed. Back to coding now - next challenge is getting to grips with threads!</p></span>
