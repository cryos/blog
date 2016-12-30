---
layout: post
title: Git and Automatic ChangeLog Generation
categories:
- Avogadro
- FOSS
- Linux
permalink: "/archives/202-Git-and-Automatic-ChangeLog-Generation.html"
s9y_link: http://blog.cryos.net/archives/202-Git-and-Automatic-ChangeLog-Generation.html
date: 2008-12-29 17:10:58.000000000 +00:00
---
<span><p>After our move to use <a href="http://git.or.cz/">Git</a> and <a href="http://github.com/cryos/avogadro/">GitHub</a> to host our repository I got thinking about ChangeLogs. Having a version controlled file, where you manually add details about what the version control system should be recording seems like it should not be necessary. I searched and couldn't find a solution that generates ChangeLogs in the style we prefer, which is a variant of the GNU ChangeLog.</p>

<p>So I wrote a quick <a href="http://www.python.org/">Python</a> script to try and accomplish this task. It may not be the prettiest Python code as I have never written more than five or six lines of Python before. ChangeLogs always seemed to be the biggest source of merge conflicts whenever we would work in branches, or just all be working at the same time. This is why I think it is necessary to automatically generate something like this that can be generated with source tarballs.</p>

<p>I called it <a href="http://github.com/cryos/avogadro/tree/master/scripts/gitlog2changelog.py">gitlog2changelog.py</a> and it has all of the basics down already. It may not be the most general script but works pretty well for us. I need to add some extra parsing for file creation/deletion so that we can add the + or - in front of the file names. Is there a general need for this? Are there better scripts out there that I dd not spot?</p>

<code><pre>2008-12-29  Tim Vandermeersch &lt;email@protected&gt;

  &lowast; libavogadro/src/pluginmanager.cpp: replace getenv(...) with
  QProcess::systemEnvironment()

  &lowast; libavogadro/src/elementtranslate.h: Replace "A_DECL_EXPORT extern ..." with
  "A_EXPORT extern ..."

  &lowast; CMakeLists.txt: use /MD compiler flag for MSVC

2008-12-28  Marcus D. Hanwell &lt;email@protected&gt;

  &lowast; libavogadro/src/molecule.cpp, libavogadro/src/molecule.h,
  libavogadro/src/python/molecule.cpp: Lots of documentation updates,
  reorganised the functions and grouped in Doxygen tags. Some minor changes
  too, more are needed for const correctness.

  &lowast; testfiles/multicubes.cube.gz: Removed from our source as it is the same
  size as all the other files put together. May be we should provide a more
  extensive sample of files in a separate distribution.

  &lowast; libavogadro/src/engines/bsdyengine.cpp: Ported to use the new bond position
  functions.

  &lowast; libavogadro/src/bond.cpp, libavogadro/src/bond.h: Added functions to
  retrieve bond positions, still need to implement the mid-point function.

  &lowast; libavogadro/src/bond.h: Documentation updates.

  &lowast; libavogadro/src/python/bond.cpp: Added missing Atom include.

  &lowast; libavogadro/src/atom.cpp, libavogadro/src/atom.h: Documentation updates,
  added member function groupings and a destructor.

  &lowast; libavogadro/src/atom.cpp, libavogadro/src/bond.cpp, libavogadro/src/bond.h:
  Added some atom accessor functions to the Bond class. This should make using
  bonds easier. Fixed assignment order in Atom constructor.</pre></code></span>
