---
layout: post
title: 'Avogadro: New Orbital Support and Gaussian Cube Format'
categories:
- Avogadro
- Chemistry
- FOSS
- GSoC
- KDE
- Linux
permalink: "/archives/173-Avogadro-New-Orbital-Support-and-Gaussian-Cube-Format.html"
s9y_link: http://blog.cryos.net/archives/173-Avogadro-New-Orbital-Support-and-Gaussian-Cube-Format.html
date: 2008-02-20 02:00:00.000000000 +00:00
---
<span><p>So over the weekend I spent quite a lot of time hacking away at <a href="http://openbabel.sourceforge.net/">OpenBabel</a> working on the Gaussian cube format support I needed to get working in order to be able to visualise electronic orbitals. The initial support was taken from <a href="http://www.cscs.ch/molekel/">Molekel</a> but contained no error checking and it was not reading in the example cube file I had.</p>

<p>Thankfully a colleague pointed out a page with details on the <a href="http://local.wasp.uwa.edu.au/~pbourke/dataformats/cube/">Gaussian cube format</a> and I used this as a basis to get it working in OpenBabel with better error checking and a more resilient tokenisation of the cube points. I made my first few commits to OpenBabel over the weekend and got at least simple Gaussian cube files loading that only contain one cube. More will follow I am sure.</p>

<center><img src="http://blog.cryos.net/uploads/avogadro_benzene_homo.png" width="480" height="458" alt="Benzene HOMO orbitals visualised in Avogadro" /></center>

<p>After I got the file loading sorted a few more changes to <a href="http://avogadro.sourceforge.net/">Avogadro</a> got me my first ever orbitals in Avogadro - the benzene HOMO! I believe the cube file came from the <a href="http://jmol.sourceforge.net/">JMol</a> test files. Geoff informed me that chemists for some reason see positive as blue and negative as red. That seemed very strange to me and I had initially put it the other way around. Growing up playing with electronics it seemed to me that positive should be red just as the wires in a circuit have a red positive... Other than that orbitals seemed to be working well and I was very pleased.</p>

<center><img src="http://blog.cryos.net/uploads/avogadro_ch3cl_esp.png" width="480" height="458" alt="CH3Cl electrostatic potential visualised in Avogadro" /></center>

<p>Next I started to load up some other cube files I had been given as examples. I thought the above image of the electrostatic potential of CH<sub>3</sub>Cl looked very nice. When I showed Geoff he also liked it and we wondered if it had been visualised in this way before. I know normally the cube would be mapped onto the Van der Waals surface of a molecule.</p>

<p>Anyway I was pleased and also felt more productive as I now have my laptop back up and running and am developing on <a href="http://www.gentoo.org/">Gentoo</a> again. It would be great to hear what other people think of this new support. I am already working on various improvements to the code and getting ready for another release of Avogadro!</p></span>
