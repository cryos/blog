---
layout: post
title: Avogadro Featured by Qt Software
categories:
- Avogadro
- Chemistry
permalink: "/archives/210-Avogadro-Featured-by-Qt-Software.html"
s9y_link: http://blog.cryos.net/archives/210-Avogadro-Featured-by-Qt-Software.html
date: 2009-02-08 15:43:16.000000000 +00:00
---
<span><p>I am very pleased to announce that <a href="http://avogadro.openmolecules.net/">Avogadro</a> was recently featured by <a href="http://www.qtsoftware.com/">Qt Software</a> on their <a href="http://www.qtsoftware.com/qt-in-use/">Qt In Use page</a>. I worked with Alexandra Leisse at <a href="http://camp.kde.org/">Camp KDE</a> on getting the page ready and we recently got the rest of the screenshots and videos prepared.</p>

<p>Check out the <a href="http://www.qtsoftware.com/qt-in-use/story/app/avogadro">Avogadro Qt page</a> and some of the features we were able to implement very rapidly thanks to the great API provided in Qt 4. The Avogadro development team is very pleased to be featured by Qt. Many of the features in Avogadro would not have been possible to implement in such short timescales without Qt. As I said on that page, we have made extensive use of the Qt plugin framework to dynamically load almost all functionality at runtime.</p>

<p>There are a few problems with our Windows installer, which was originally a hand crafted NSIS installer. There is a preview of a new <a href="http://www.cmake.org/Wiki/CMake:Packaging_With_CPack">CPack</a> generated installer. You can get it <a href="http://blog.cryos.net/uploads/Avogadro-0.9.0a-win32.exe">here</a> if you are cannot wait to try it on Windows. It lacks <a href="http://www.python.org/">Python</a> support right now as that brings in quite a few extra dependencies I have not had time to compile on my Windows virtual machine yet.</p></span>
