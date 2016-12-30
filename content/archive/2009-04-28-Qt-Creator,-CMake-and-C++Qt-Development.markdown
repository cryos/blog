---
layout: post
title: Qt Creator, CMake and C++/Qt Development
categories:
- Avogadro
- Chemistry
- Gentoo
- KDE
permalink: "/archives/218-Qt-Creator,-CMake-and-C++Qt-Development.html"
s9y_link: http://blog.cryos.net/archives/218-Qt-Creator,-CMake-and-C++Qt-Development.html
date: 2009-04-28 15:13:00.000000000 +00:00
---
<span><p>I have been experimenting with <a href="http://www.qtsoftware.com/products/developer-tools">Qt Creator</a> since the first release. I have always preferred a minimal editor for development work, with my main needs being good syntax highlighting, the ability to switch between different files quickly and something that stays out of my way as much as possible. Previously I had used <a href="http://www.vim.org/">Vim</a>, <a href="http://kate-editor.org/">Kate</a> and several konsole instances the majority of the time.</p>

<p>Recently I have been looking for something with better integration, and so had been slowly keeping an eye out for a lightweight IDE. My main requirements were something lightweight, good C++ support, ideally good <a href="http://www.qtsoftware.com/products">Qt</a> support and <a href="http://www.cmake.org/">CMake</a> integration. Over the weekend I tried the latest <a href="http://labs.trolltech.com/blogs/2009/04/23/11-after-the-release-is-before-the-release/">Qt Creator 1.1 release</a> and was really impressed.</p>

<p>Seb Ruiz <a href="http://www.sebruiz.net/359">made a great post on Qt Creator 1.1</a> that summed up many of my thoughts, and gave a quick walkthrough. It was not immediately obvious how to import a CMake project, I was looking for an import project option. All that is necessary is to go to file and open. You can then open the base CMakeLists.txt file for your project and the CMake plugin will do the rest.</p>

<p>From there on in you get great integration with the build system, version control (<a href="http://git-scm.com/">Git</a> and friends), and your friendly <a href="http://www.gnu.org/software/gdb/">GDB debugger</a>. Under projects you might want to quickly add -j5 (if you are lucky enough to have a quad core machine) to the additional arguments input for make, and select the main executable target for your project if you also have several other executable targets (unit tests etc).</p>

<p>The first time you debug a project you will be prompted to build the Qt debugger helper. Then the integration with GDB really wins over using GDB directly, or using <a href="http://www.gnu.org/software/ddd/">ddd</a> which I had been using more and more recently. I would highly recommend trying Qt Creator if you are looking for a lightweight, cross platform IDE. There are certainly other great IDEs out there, but I think that Qt Creator is a great fit for my development style (and may be yours).</p></span>
