---
layout: post
title: Avogadro and OpenBabel Development
categories:
- Avogadro
- Chemistry
- GSoC
- Linux
permalink: "/archives/181-Avogadro-and-OpenBabel-Development.html"
s9y_link: http://blog.cryos.net/archives/181-Avogadro-and-OpenBabel-Development.html
date: 2008-05-29 14:48:01.000000000 +00:00
---
<span><p>I thought I should post a few thoughts on the development of <a href="http://avogadro.sourceforge.net/">Avogadro</a> and <a href="http://openbabel.sourceforge.net/">OpenBabel</a> as there seems to be some confusion in replies to some of my posts. Ever since Avogadro began development it has used OpenBabel as its chemical library. OpenBabel provides Avogadro's internal representation of molecules, atoms, bonds, cube data etc.</p>

<p>Avogadro has driven the development of some new features in OpenBabel. In return we have been able to leverage many of the existing library functions to rapidly implement new features in Avogadro. OpenBabel isn't just a library for loading and saving chemical file formats. It provides information on the atoms, bond typing, <a href="http://en.wikipedia.org/wiki/Force_field_%28chemistry%29">force fields</a> such as UFF to do geometry optimisation and lots of other very useful features. Many of the recent releases of Avogadro (which is still in beta) have been accompanied by a new beta release of OpenBabel due to each project driving the development of the other. I now work on both (but still mainly on Avogadro) as there were bugs I needed to fix in OpenBabel and Geoff got sick of me sending him patches!</p>

<p>As <a href="http://kalzium.kde.org/">Kalzium</a> uses Avogadro to do all of its molecular editing and visualisation this also means that the optional molecular editor depends on new releases of the OpenBabel library. I hope this makes it clearer why Avogadro and Kalzium generally rely upon the latest version of OpenBabel - many times we have implemented new features in OpenBabel for Avogadro but they should also be useful outside of Avogadro. As always I am open to suggestions and feedback on the way we do our development but I would love to hear more feedback on the software I am writing rather than the packaging issues. As a Gentoo developer I do appreciate that packaging is extremely important and so am doing what I can to make packaging as easy as possible too.</p></span>
