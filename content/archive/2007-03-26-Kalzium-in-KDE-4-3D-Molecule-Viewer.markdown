---
layout: post
title: 'Kalzium in KDE 4: 3D Molecule Viewer'
categories:
- KDE
- Linux
- PhD
permalink: "/archives/133-Kalzium-in-KDE-4-3D-Molecule-Viewer.html"
s9y_link: http://blog.cryos.net/archives/133-Kalzium-in-KDE-4-3D-Molecule-Viewer.html
date: 2007-03-26 12:10:00.000000000 +00:00
---
<span><p>Some of you may remember a post I made <a href="http://blog.cryos.net/archives/52-New-Kalzium-With-KDE-3.5-Beta-1.html">about Kalzium</a> quite some time ago. In KDE 4 trunk it now has a 3D molecule viewer which is already looking pretty fantastic. I have been playing with it quit a bit, and the library where all the 3D molecular visualisation is destined to be kept so that other applications can use it.</p>

<center><img src="http://blog.cryos.net/uploads/kalzium3dmolecule.png" width="600" height="437" alt="Kalzium displaying a 3D rendering of methylbenzenethiol" /></center>

<p>I have been using <a href="http://www.uku.fi/~thassine/projects/ghemical/">ghemical</a> to draw my 3D molecules and am rendering them in <a href="http://jmol.sourceforge.net/">Jmol</a> using the <a href="http://www.povray.org/">POVRay</a> rendering stuff. This is a reasonable solution but I have to say I have found myself wishing for something a little more integrated and intuitive. Above you can see how Kalzium rendered my 4-methylbenzenethiol molecule which encapsulates the gold nanoparticles I spend so much time writing about right now in my thesis.</p>

<p>There is code in subversion that already does some basic molecular editing, geometry optimisation and rendering to screen. Thanks to <a href="http://openbabel.sourceforge.net/">OpenBabel</a> it can load and save pretty much any chemical data file format too. As you may know this is the last time I am ever likely to be a student and I have put in an application to work on this over the summer with <a href="http://code.google.com/soc/">Google Summer of Code (TM)</a>. So with me luck <img src="http://blog.cryos.net/templates/default/img/emoticons/smile.png" alt=":-)" style="display: inline; vertical-align: bottom;" class="emoticon" /></p>

<p>I have been wanting to get involved in upstream <a href="http://www.kde.org/">KDE</a> development for quite some time now and this seemed like an amazing way to start. The timing is pretty great too (although right now I am insanely busy finishing up my thesis and so the application period was hard to fit in) as I will complete my thesis before the summer starts and can delay getting full time work until after the summer. Don't worry - I have no plans to leave Gentoo and once I have more free time I will be spending more time on Gentoo again too!</p></span>
