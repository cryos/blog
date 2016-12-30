---
layout: post
title: Manifest Hell...The New DLL Hell?
categories:
- Avogadro
- FOSS
permalink: "/archives/209-Manifest-Hell...The-New-DLL-Hell.html"
s9y_link: http://blog.cryos.net/archives/209-Manifest-Hell...The-New-DLL-Hell.html
date: 2009-02-07 20:30:00.000000000 +00:00
---
<span><p>I am going to shock you all and admit that I am not a Windows programmer! I do however know quite a bit about cross-platform development and have now learnt the joy that is the manifest in Windows development. It seems that DLL hell is now a thing of the past, all hail manifest hell. A week ago I was not aware of these wonderful little files and this post is an attempt to document what I learned while packaging <a href="http://avogadro.openmolecules.net/">Avogadro</a> for Windows.</p>

<p>After listening to Bill's talk at <a href="http://camp.kde.org/">Camp KDE</a> I was convinced that it really was a good idea to use <a href="http://www.cmake.org/Wiki/CMake:Packaging_With_CPack">CPack</a> to package Avogadro. So when I got back home I spent a day or two getting a Windows development environment set up for Avogadro. We have several dependencies such as <a href="http://www.qtsoftware.com/">Qt</a> and <a href="http://www.openbabel.org/'>OpenBabel</a> so it took a while to get everything installed and compiled.</p>

<p>Once done I got some new packages made up and initially it all looked pretty good. I used InstallRequiredSystemLibraries to install the MS DLLs we needed and then tried it on a fresh Windows install. I got some very cryptic message telling me to reinstall my application. After some searching I came across <a href="http://www.mail-archive.com/cmake@cmake.org/msg17941.html">this post</a> documenting a bug in the Visual Studio 9 service pack. So I edited the manifest and lied about the version of the DLLs - it believed me.</p>

<p>Next I found that none of our plugins would load. They are Qt plugins that implement most of the functionality in Avogadro. I found a <a href="http://lists.trolltech.com/qt-interest/2007-02/thread00449-0.html">very long thread</a> on this subject, the crux of which is that the embedded manifests are causing Windows to look for the runtime libraries in the plugin directory. Copying them did indeed work but was not optimal. I found that by adding <tt>set(CMAKE_MODULE_LINKER_FLAGS "${CMAKE_MODULE_LINKER_FLAGS} /MANIFEST:NO")</tt> to our CMakeLists.txt manifests were no longer made for our plugins (which are loadable modules).</p>

<p>So all is quite well with our Windows build now I think. If you would like to try out a new Windows installer, then please <a href="http://blog.cryos.net/uploads/Avogadro-0.9.0a-win32.exe">download it from here</a> and let me know if it works for you. I have tested it on Windows 2000 and XP virtual machines. This is not the final installer, I need to add some extra data files for OpenBabel and ensure I got the other dependencies right.</p>

<p>If anyone with more Windows experience knows of better solutions please let me know. CPack is absolutely awesome, it seems a shame that the deployment of applications is made so difficult. I know that plugins are not as widely used and so hopefully this post will add to the collective knowledge indexed by <a href="http://www.google.com/">Google</a>.</p></span>
