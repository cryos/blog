---
layout: post
title: Avogadro and POV-Ray Export
categories:
- GSoC
- KDE
- Linux
permalink: "/archives/154-Avogadro-and-POV-Ray-Export.html"
s9y_link: http://blog.cryos.net/archives/154-Avogadro-and-POV-Ray-Export.html
date: 2007-08-18 15:02:42.000000000 +00:00
---
<span><p>I have made some more progress with Avogadro and exporting to POV-Ray. Currently the export is working quite well, but is a more manual process than it will be once I have finished all aspects of its implementation. You can export to POV-Ray, but then need to run POV-Ray yourself on the .pov file created to actually get an image. It is not too much work to add the dialog to call POV-Ray, pass it a few options and display the rendered image.</p>

<p>Right now I have the issue that I cannot properly translate between the OpenGL camera matrix and the POV-Ray camera system. If anyone has any experience of doing this I would love to hear about it. I have tried using the direction, up and right keywords but POV-Ray claims my coordinates are not orthogonal, and they are - Benoit double checked they were too. I am probably missing something simple. So right now I can export to POV-Ray but only get one view of the atom which does not follow the view in Avogadro - not ideal but certainly usable.</p>

<center><img src="http://blog.cryos.net/uploads/1d66.png" width="400" height="388" alt="1d66 rendered in POV-Ray with shadows" title="1d66 rendered in POV-Ray with shadows" /><img src="http://blog.cryos.net/uploads/1d66-ns.png" width="400" height="388" alt="1d66 rendered in POV-Ray without shadows" title="1d66 rendered in POV-Ray without shadows" /></center>

<p>The images above show a rendering of 1d66 from the protein data bank thing (I sometimes grab interesting and large example structures from there to test Avogadro and Carsten liked this one). The first image shows it rendered with shadows and the second shows it rendered without shadows. Carsten pointed out that effects such as shadows can serve to confuse students but this can be made a configurable option as shadows also help the mind to visualise the three dimensional structure in my opinion (if used right).</p>

<p>There are lots of things that can be tweaked about the way the files are exported as well as the rendered image look and feel. A lot of work has actually gone into getting this working as I have made the painter independent of the paint device being used. This means that the engines can paint to any device where a painter implements the primitives in the virtual base class and I think this will allow Avogadro to scale very well as more features are added.</p></span>
