---
layout: post
title: Open Chemistry, VTK and ParaViewWeb
categories:
- Avogadro
- Chemistry
permalink: "/archives/260-Open-Chemistry,-VTK-and-ParaViewWeb.html"
s9y_link: http://blog.cryos.net/archives/260-Open-Chemistry,-VTK-and-ParaViewWeb.html
date: 2012-06-22 19:04:46.000000000 +00:00
---
<span><p>Last year <a href="http://www.kitware.com/company/team/lonie.html">David Lonie</a>, now a new <a href="http://www.kitware.com/">Kitware</a> employee, worked on a <a href="http://www.kitware.com/blog/home/post/141">Google Summer of Code project</a> to add better support for <a href="http://www.kitware.com/source/home/post/44">chemical structure visualization to VTK</a>. More recently, <a href="http://www.kitware.com/company/team/lutz.html">Kyle Lutz</a> added representations to <a href="http://www.paraview.org/">ParaView</a> to expose some of this new functionality for ParaView users. Once that was in place we were able to work with&#160;<a href="http://www.kitware.com/company/team/jourdain.html">S&eacute;bastien Jourdain</a> to expose this functionality in <a href="http://paraview.org/Wiki/ParaViewWeb">ParaViewWeb</a>&#160;and expose parts of the MongoDB database we have been working on as part of the <a href="http://www.openchemistry.org/">Open Chemistry project</a>. You can checkout the live&#160;<a href="http://paraviewweb.kitware.com/OpenChemistry/">demo here</a>, or take a look at the screen shot below.</p>

<a href="http://paraviewweb.kitware.com/OpenChemistry/"><img src="http://blog.cryos.net/uploads/openchemistryparaviewweb.png" width="776" height="727" alt="ParaVIewWeb and Open Chemistry live demo" /></a>

<p>It was up and running within a day, and in another day we had a query page and summaries exposed in ParaViewWeb with some simple queries. <a href="http://wiki.openchemistry.org/ChemData">ChemData</a>&#160;exposes more complex searches and 2D visualizations of the data contained. The 2D images are created using <a href="http://www.openbabel.org/">Open Babel's</a> SVG rendering, and saved to the database as PNGs for speed and the 3D structure is rendered using ParaViewWeb and image based delivery right now. You can interact with the 3D geometry both inline, or full screen. We will be extending this to show electronic structure and adding other features in the near future too.</p></span>
