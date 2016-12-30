---
layout: post
title: CMake Performance with Open Babel
categories:
- Chemistry
- General
- Gentoo
- Linux
permalink: "/archives/217-CMake-Performance-with-Open-Babel.html"
s9y_link: http://blog.cryos.net/archives/217-CMake-Performance-with-Open-Babel.html
date: 2009-04-11 15:17:00.000000000 +00:00
---
<span><p>Recently, Luca made a post <a href="http://blogs.gentoo.org/lu_zero/2009/03/24/cmake-vs-autotools-a-benchmark">comparing the speed of CMake and autotools</a> in which some timings were posted. I have to say that I am not sure I agreed with the conclusion and have had a very different experience with the projects I am involved in. As with anything your mileage may vary, and I have not looked at <a href="http://www.wesnoth.org/">Wesnoth</a>.</p>

<p>I think it is questionable at best to include the time it takes to build CMake, but not autotools. Seems like this is a one time cost and the build time is not that high for either. All tests were performed on my quad core Gentoo box at work. Each step is for the first cold run as would normally be the case when compiling <a href="http://www.openbabel.org/">Open Babel</a> from source. The make step used `time make -j5` and I have listed the real time in each case.</p>

<p>The timings are shown in the table below. They seem somewhat similar to the <a href="http://blog.qgis.org/node/16">experiences of the QGIS developers</a> who made this move quite some time ago. All times shown are in seconds and are the real time reported by the time command.</p>

<center>
<table>
  <tr>
    <th>&#160;</th>
    <th><a href="http://sources.redhat.com/autobook/">Autotools</a></th>
    <th><a href="http://www.cmake.org/">CMake</a></th>
  </tr>
  <tr>
    <td>Configure time</td>
    <td>20.39</td>
    <td>4.79</td>
  </tr>
  <tr>
    <td>Compile time</td>
    <td>116.45</td>
    <td>102.23</td>
  </tr>
  <tr>
    <td>Install time</td>
    <td>28.39</td>
    <td>4.19</td>
  </tr>
  <tr>
    <td>Total time</td>
    <td>165.23</td>
    <td>111.21</td>
  </tr>
</table>
</center>

<p>For those interested, on this system the total CMake compilation/installation time (cmake-gui disabled) was 1 minute and 54 seconds. The compilation/installation time for automake, autoconf, libtool, m4 was 2 minute and 14 seconds. I am not sure how relevant either of those times are, other than to show neither of them take that long to compile and install. <a href="http://www.gentoo.org/">Gentoo</a> users/developers may or may not have CMake installed, most other developers will install the binary packages for either one and are likely to be much more interested in how well it integrates with their development environment, compile and install times.</p>

<p>As a developer I prefer CMake, and have been using/maintaining the CMake based build system for Open Babel for over a year now. It was originally contributed by the KDE Windows porting team, but I found that I spent less time waiting for it to do things when I was working on code too. Add to that the extras CMake comes with, such as <a href="http://vtk.org/Wiki/CMake_Testing_With_CTest">CTest</a>, <a href="http://www.cdash.org/">CDash</a> and <a href="http://www.vtk.org/Wiki/CMake:Packaging_With_CPack">CPack</a> I think it makes a very attractive option for many projects. I am also hoping that it will allow Open Babel to drop maintaining a totally separate build system for MSVC.</p>

<p>I am sure the Open Babel autotools build system could be optimized (I never tried), but when you add in the additional benefits mentioned above, support for multiple targets such as makefiles, XCode, MSVC, Eclipse etc, one shared language/syntax for all build files and an increasingly polished competitor to autotools, I honestly think it is a sensible choice for projects to move to CMake. There are a few less well known features such as Fortran module dependency parsing that I think are fairly unique and valuable, in scientific coding at least (and I have used the Fortran module dependency parsing at least once and was pleasantly surprised).</p>

<p>Full disclosure: I recently accepted a job offer with <a href="http://www.kitware.com/">Kitware</a>, and will start in the Fall assuming all the visa paperwork falls into place. The opinions expressed here are my own. I think it is great to discuss issues like this objectively, and hope to be a part of making CMake a better build system. As with most software - there are areas that need improving.</p></span>
