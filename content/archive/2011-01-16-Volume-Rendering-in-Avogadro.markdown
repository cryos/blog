---
layout: post
title: Volume Rendering in Avogadro
categories:
- Avogadro
- Chemistry
- GSoC
- KDE
- Kitware
permalink: "/archives/247-Volume-Rendering-in-Avogadro.html"
s9y_link: http://blog.cryos.net/archives/247-Volume-Rendering-in-Avogadro.html
date: 2011-01-16 03:23:43.000000000 +00:00
---
<span><p>Since joining <a href="http://www.kitware.com/">Kitware</a> I have had limited spare time to work on <a href="http://avogadro.openmolecules.net/">Avogadro</a>, and for various reasons my spare time has been more limited than usual too. Since the new year I have been able to start spending more time working on Avogadro, and open source chemistry in general, thanks to an SBIR phase I proposal that was funded last year with the <a href="http://www.usace.army.mil/">US Army Corps of Engineers</a>. This is exciting for a number of reasons, including the fact that I have the opportunity to prototype exciting new features for chemistry visualization, workflow and data management.</p>

<center><a class="serendipity_image_link"  href='http://blog.cryos.net/uploads/avogadro-benzene-volume.png' onclick="F1 = window.open('/uploads/avogadro-benzene-volume.png','Zoom','height=1059,width=1437,top=-117,left=-66,toolbar=no,menubar=no,location=no,resize=1,resizable=1,scrollbars=yes'); return false;"><img class="serendipity_image_center" width="199" height="146"  src="http://blog.cryos.net/uploads/avogadro-benzene-volume.serendipityThumb.png"  alt="" /></a></center>

<p>One of the new bits of work I have been doing is to use some of the advanced visualization techniques in <a href="http://www.vtk.org/">VTK</a> such as GPU accelerated volume rendering. Now the code is still pretty rough, and is more a proof of concept. I wrote a simple external Avogadro extension that links to and uses VTK to render the first volume found in the current Avogadro molecule. All of the parameters are currently fixed, I am hoping to get the time to add in more options along with some integration of the Avogadro rendered molecule in the VTK render window. You can view the code <a href="https://github.com/cryos/AvogadroVTK">here</a>, please bear in mind it is at a very early stage.</p>

<p>I have also been working on several other things such as splitting out the quantum calculation code from the Avogadro plugins, and putting it in a small library. I have called the library <a href="http://gitorious.org/avogadro/openqube">OpenQube</a>, right now it only has the base functionality that was in Avogadro but I will be extending it with more features, regression tests and I am hoping due to the decoupled nature and liberal BSD license it will encourage wider collaboration in this field.</p>

<p>There is also <a href="http://quixote.wikispot.org/">the Quixote project</a> which I am very excited about. Meaningfully storing the results of quantum calculations, annotating them and retrieving them within an open framework. This is a growing problem in todays world, and I am working on extensions to Avogadro to allow it to fully exploit the semantic chemical web. This includes some of the previous work to access the PDB and other public resources as well as private databases within groups and organizations.</p>

<p>I think this is going to be a very exciting year for Avogadro, and open source chemistry in general.</p></span>
