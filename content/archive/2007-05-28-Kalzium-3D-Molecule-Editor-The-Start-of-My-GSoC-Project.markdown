---
layout: post
title: 'Kalzium 3D Molecule Editor: The Start of My GSoC Project'
categories:
- Gentoo
- GSoC
- KDE
- Linux
permalink: "/archives/141-Kalzium-3D-Molecule-Editor-The-Start-of-My-GSoC-Project.html"
s9y_link: http://blog.cryos.net/archives/141-Kalzium-3D-Molecule-Editor-The-Start-of-My-GSoC-Project.html
date: 2007-05-28 12:49:00.000000000 +00:00
---
<span><p>My blog is aggregated on three planets now, <a href="http://planet.gentoo.org/universe">Gentoo</a>, <a href="http://planetkde.org/">KDE</a> and <a href="http://planet-soc.com/">SoC</a>. So I guess my readership will be at its peak. There have been some hurdles leading up to my <a href="http://code.google.com/soc/kde/appinfo.html?csaid=3EBDFAAF85EFFA00">Google Summer of Code (TM) project</a> but I am very pleased to have made it and intend to make the very best of this amazing opportunity to work on what is a really exciting project for me.</p>

<p>I will be working on the 3D molecular editor project which was an idea proposed by <a href="http://cniehaus.livejournal.com/">Carten Niehaus</a> on the <a href="http://techbase.kde.org/Projects/Summer_of_Code/2007/Ideas#A_3D_Molecular_Editor">KDE GSoC 2007 ideas page</a>. I have to admit that when I read it I was very excited. I had read some stuff on the <a href="http://planetkde.org/">Planet KDE</a> (which I have read for ages and am really proud to be added to now) about the new 3D molecular viewer for <a href="http://edu.kde.org/kalzium/">Kalzium</a>.</p>

<center><img src="http://blog.cryos.net/uploads/avo20070528a.png" width="800" height="501" alt="Avogadro snapshot of a HMDS molecule" /></center>

<p>I was hoping to be able to find an area I could help out with that when I discovered the idea that looked like it had been written for me! I then discovered the <a href="http://avogadro.sourceforge.net/">Avogadro</a> project and met some of the project's developers. As I was putting my application together I helped with a few small patches and ported the molecule navigation code across to Avogadro from Kalzium. I also provided a patch for a Van der Waals sphere view of the molecule as I have always liked that particular method of visualising molecules.</p>

<p>Some of my patches were accepted and integrated. Eventually I heard back about my GSoC application - I was very pleased to learn it had been accepted. Unfortunately for personal reasons I spent the next few weeks offline (after letting my new mentor know) and didn't get to celebrate straight away.</p>

<p>Once I was back online I got commit access for the KDE subversion repository, my commit name is "hanwell" as they don't like you to use nicks. I also got commit access to the Avogadro repository where my commit name is "cryosuk" due to my usual "cryos" already being taken on <a href="http://www.sourceforge.net/">SourceForge</a>. So now I am committing under multiple aliases in different projects <img src="http://blog.cryos.net/templates/default/img/emoticons/wink.png" alt=";-)" style="display: inline; vertical-align: bottom;" class="emoticon" /></p>

<center><img src="http://blog.cryos.net/uploads/kalziummol20070528.png" width="575" height="369" alt="Kalzium 3D molecule viewer snapshot of a methylbenzenethiol molecule" /></center>

<p><a href="http://bjacob.livejournal.com/">Benoit Jacob</a> is my mentor along with <a href="http://cniehaus.livejournal.com/">Carten Niehaus</a>, Donald E. Curtis and <a href="http://geoffhutchison.net/">Geoff Hutchison</a> who have all been very welcoming. They already contributed so much to the project I am just getting involved in. <a href="http://openbabel.sourceforge.net/">Open Babel</a> and the Avogadro library underpin much of the 3D molecular editor and I have already made quite a few commits to the  Avogadro and Kalzium subversion repositories.</p>

<p>There was an application freeze planned at the start of June for KDE 4.0, so I started my project early in order to get some of the great new features of Avogadro into <a href="http://techbase.kde.org/Schedules/KDE4/4.0_Release_Schedule">KDE 4.0</a>. Some of the highlights of this work were porting the navigate tool, adding the manipulate tool, various improvements to the label engine as well as some small enhancements to the engine API. We had the goal of ensuring all kalzium 3D viewer code was ported to the Avogadro library before we began porting Kalzium to use the Avogadro library to display molecules.</p>

<p>We accomplished that a few weeks ago and then began porting Kalzium to use the Avogadro library as its 3D visualisation backend. Along the way the Avogadro project made its 0.1 release, I added an ebuild for <a href="http://www.gentoo.org/">Gentoo</a> and also made a few posts about the initial work. The feature freeze has been delayed but we got everything we wanted to done before the original deadline which I am pleased about.</p>

<p>Today marks the first official day of my project. I have already implemented several features I had planned including the port to the Avogadro library and ensuring all 3D Kalzium code was ported to the Avogadro library. I am really looking forward to working on this project over the summer and creating an awesome 3D molecular visualisation application. I am lucky to be working with such a friendly and motivated team of developers and will be sure to make regular posts about what I am up to. I welcome feedback on my work and have placed a screen shot of Avogadro (first picture) and the 3D molecular viewer in Kalzium (second picture).</p></span>
