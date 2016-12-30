---
layout: post
title: 'CMake External Projects: Building Project Dependencies'
categories:
- Avogadro
- Chemistry
- FOSS
- Gentoo
- KDE
- Kitware
permalink: "/archives/248-CMake-External-Projects-Building-Project-Dependencies.html"
s9y_link: http://blog.cryos.net/archives/248-CMake-External-Projects-Building-Project-Dependencies.html
date: 2011-03-05 21:41:21.000000000 +00:00
---
<span><p>Historically projects have attempted to minimize their dependency list, and often bundle in small third party libraries in an attempt to make things easier for new developers/users to compile their code. In the <a href="http://avogadro.openmolecules.net/">Avogadro project</a> we have bundled a few really small libraries, but on the whole have maintained a dependency list and tried to keep it smaller. As I work on new code, I see opportunities to break off bits of functionality, such as with OpenQube, but don't want to add yet another thing a new user or developer must download, compile and install somewhere.</p>

<p>Linux packagers, myself included, dislike the practice of bundling in libraries. It means that instead of patching one libxml2, we get to patch one plus the three or four in our tree that have been bundled (often with different version, some local patches). The problem is less pronounced on Linux where package managers are ubiquitous and we are able to provide a list of packages to install, but even there we might be developing against versions not yet in the main distribution repository. This is one of the reasons I have always favored rolling release distributions over the periodic.</p>

<p><a href="http://www.kitware.com/products/html/BuildingExternalProjectsWithCMake2.8.html">CMake's external project</a> module helps us to deal with this issue in quite an elegant fashion. Coupled with meta repositories to bring several source trees together, CMake is able to direct the build of several projects, passing locations between projects and expressing dependencies between the projects being built. This means that something like <a href="http://www.openbabel.org/">Open Babel</a> can build zlib and libxml2 before building the main Open Babel library. External projects and CMake allow us to download the source, create the build trees and even direct the build of non-CMake based projects like libxml2.</p>

<p>I have a prototype of this that I just put up to build the core of Avogadro, its working name is <a href="https://github.com/cryos/avogadro-squared">Avogadro Squared</a> as I was feeling geeky that day and had no good names. One thing you should note is that everything in there is an external project, and Avogadro is the last one to be built (it depends on all of the other projects). It requires minimal changes to the projects it contains, it uses git submodules for some of the source, and CMake's download and tar functionality for zlib and libxml2. I will be adding options to simply use system versions of the libraries it can build, but Linux distributions etc can continue using the Avogadro repository directly.</p>

<p>As a new developer or user I can checkout the meta repository, have git download the submodules and CMake download the source tarballs. I can then build the entire project, and then continue to work in the Avogadro subdirectory of the build tree after that. That build tree is almost identical to the one I would have ended up with had I not used the meta repository, except it points to the dependencies I just built. I can then use vim, and IDE or whatever I choose to work on the inner projects. This works across Linux, Mac and Windows to get new users and developers up and running very quickly while only loosely coupling the dependencies to the Avogadro project.</p>

<p>I have worked on other larger projects, such as <a href="http://titan.sandia.gov">Titan</a> and <a href="http://www.paraview.org/">ParaView</a> that are using this approach to a greater or lesser extent. Titan can actually built Qt, Boost, VTK, protobuf, Trilinos and a host of other dependencies before building the Titan libraries and applications. I think Avogadro Squared is an example of just how minimal a meta repository can be, although I will be extending it with more dependencies it really is just a glue repository.</p></span>
