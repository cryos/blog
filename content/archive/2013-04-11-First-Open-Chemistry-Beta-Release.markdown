---
layout: post
title: First Open Chemistry Beta Release
categories:
- Avogadro
- Chemistry
- Gentoo
- GSoC
- KDE
- Kitware
- Linux
permalink: "/archives/265-First-Open-Chemistry-Beta-Release.html"
s9y_link: http://blog.cryos.net/archives/265-First-Open-Chemistry-Beta-Release.html
date: 2013-04-11 18:11:00.000000000 +00:00
---
<span><a href="http://openchemistry.org/"><img style="float: right;" src="http://blog.cryos.net/uploads/OpenChemistry_Logo.png" alt="Open Chemistry" width="200" height="105" /></a>
<p>We are pleased to announce the first beta release of the <a href="http://openchemistry.org/">Open Chemistry</a> suite of cross platform, open-source, BSD-licensed tools and libraries - Avogadro 2, MoleQueue and MongoChem. They are being released in beta, before all planned features are complete, to get feedback from the community following the open-source mantra of <a href="http://en.wikipedia.org/wiki/Release_early,_release_often">&ldquo;release early, release often&rdquo;</a>. We will be making regular releases over the coming months, as well as <a href="http://cdash.openchemistry.org/">automatically generating nightly binaries</a>. A <a href="http://kitware.com/source/home/post/39">Source article from 2011</a> introduced the project, <a href="http://www.slideshare.net/cryos/the-open-chemistry-project">slides from FOSDEM</a> describe it more recently, and the <a href="http://www.openchemistry.org/OpenChemistry/resources/software.html">0.5.0 release binaries can be downloaded here</a>.</p>

<center><img src="http://blog.cryos.net/uploads/openchemistry-workflow.png" alt="Open Chemistry workflow" width="500" height="253" /></center>

<p>These three desktop applications can each be used independently, but also have the capability of working together. Avogadro 2 is a rewrite of <a href="http://avogadro.openmolecules.net/">Avogadro</a> that addresses many of the limitations we saw. This includes things such as the rendering code, scalability, scriptability, and increased flexibility, enabling us to effectively address the current and upcoming challenges in computational chemistry and related fields. MoleQueue provides desktop services for executing standalone programs both locally and on remote batch schedulers, such as <a href="http://en.wikipedia.org/wiki/Sun_Grid_Engine">Sun Grid Engine</a>, <a href="http://en.wikipedia.org/wiki/Portable_Batch_System">PBS</a> and <a href="http://en.wikipedia.org/wiki/Simple_Linux_Utility_for_Resource_Management">SLURM</a>. MongoChem provides chemically-aware search, storage, and informatics visualization using <a href="http://www.mongodb.org/">MongoDB</a> and <a href="http://www.vtk.org/">VTK</a>.</p>

<center><img src="http://blog.cryos.net/uploads/openchemistry-libs.png" alt="Open Chemistry library organization" width="500" height="253" /></center>

<h2>Avogadro 2</h2>

<p>Avogadro 2 is a rewrite of Avogadro; please see the <a href="http://www.jcheminf.com/content/4/1/17">recently-published paper for more details on Avogadro 1</a>. Avogadro has been very successful over the years, and we would like to thank all of our contributors and supporters, including the core development team: Geoff Hutchison, Donald Curtis, David Lonie, Tim Vandermeersch, Benoit Jacob, Carsten Niehaus, and Marcus Hanwell. We also recently obtained permission from almost all authors to relicense the existing code under the 3-clause BSD license, which will make migration of code to the new architecture much easier.</p>

<center><a href="http://blog.cryos.net/uploads/avogadro-mo-66.png" target="_blank"><img src="http://blog.cryos.net/uploads/avogadro-mo-66.png" alt="Avogadro 2 rendering a molecular orbital" width="500" height="394" /></a></center>

<p>Some notable new features of Avogadro 2 include:</p>
<ul>
<li>Scalable data structures capable of addressing the needs of large molecular systems.</li>
<li>A flexible file I/O API supporting seamless addition of formats at runtime.</li>
<li>A <a href="http://doc.openchemistry.org/avogadrolibs/api/class_avogadro_1_1_qt_plugins_1_1_input_generator.html">Python-based input generator API</a>, creating an input for a range of quantum codes.</li>
<li>A specialized scene graph for supporting scalable molecular rendering.</li>
<li>OpenGL 2.1/GLSL based rendering, employing point sprites, VBOs, etc.</li>
<li>Unit tests for core classes, with ongoing work to improve coverage.</li>
<li>Binary <a href="http://packages.kitware.com/packages/application/latest?applicationId=6">installers generated nightly</a>.</li>
<li>Use of MoleQueue to run computational codes such as <a href="http://www.nwchem-sw.org/">NWChem</a>, <a href="http://openmopac.net/">MOPAC</a>, <a href="http://www.msg.ameslab.gov/gamess/">GAMESS</a>, etc.</li>
</ul>

<p>Avogadro is not yet feature complete, but we invite you to try it out along with the suite of applications as we continue to improve it. The new <a href="http://doc.openchemistry.org/avogadrolibs/api/annotated.html">Avogadro libraries feature much finer granularity</a>; whereas before we provided a single library with all API, there is now a layered API in multiple libraries. The Core and IO libraries have minimal dependencies, with the rendering library adding a dependence on OpenGL, and the Qt libraries adding Qt 4 dependencies. This allows us to reuse the code in many more places than was possible before, with rendering possible on a server without Qt/X, and the Core/IO libraries being suitable for command line use or integration into non-graphical applications.</p>

<h2>MoleQueue</h2>

<p>MoleQueue is a new application developed to satisfy the need to execute computational chemistry codes locally and remotely. Rather than adding this functionality directory to Avogadro 2, it has been developed as a standalone system-tray resident application that runs a graphical application and a local server (using local sockets for communication). It supports the configuration of multiple queues (local and remote), each containing one-or-more programs to be executed. Applications communicate with MoleQueue using <a href="http://www.jsonrpc.org/specification">JSON-RPC 2.0</a> over a local socket, and receive updates as the job state changes. A <a href="http://kitware.com/source/home/post/93">recent Source article describes MoleQueue</a> in more detail.</p>

<center><a href="http://blog.cryos.net/uploads/molequeue-queue.png" target="_blank"><img src="http://blog.cryos.net/uploads/molequeue-queue.png" alt="MoleQueue queue configuration" width="500" height="399" /></a></center>

<p>In addition to the system-tray resident application, MoleQueue provides a Qt 4-based client library that can easily be integrated into Qt applications, providing a familiar signal-slot based API for job submission, monitoring, and retrieval. The project has remained general in its approach, containing no chemistry specific API, and has already been used by several other projects at Kitware in different application domains. Communicating with the MoleQueue server from other languages is quite simple, with the client code having minimal requirements for connecting to a named local socket and constructing JSON strings conforming to the JSON-RPC 2.0 specification.</p>

<h2>MongoChem</h2>

<p>MongoChem is another new application developed as part of the Open Chemistry suite of tools, leveraging MongoDB, VTK, and AvogadroLibs to provide chemical informatics on the desktop. It seeks to address the need for researchers and groups to be able to effectively store, index, search and retrieve relevant chemical data. It supports the use of a central database server where all data can be housed, and enables the significant feature set of MongoDB to be leveraged, such as sharding, replication and efficient storage of large data files. We have been able to reuse several powerful cheminformatics libraries such as Open Babel and Chemkit to generate identifiers, molecular fingerprints and other artifacts as well as developing out features in the Avogadro libraries to support approaches to large datasets involving many files.</p>

<center><a href="http://blog.cryos.net/uploads/mongochem-detail.png" target="_blank"><img src="http://blog.cryos.net/uploads/mongochem-detail.png" alt="MongoChem" width="500" height="390" /></a></center>

<p>We have taken advantage of the charts developed in VTK and 2D chemical structure depiction in Open Babel to deliver immersive charts that are capable of displaying multiple dimensions of the data. Linked selection allows for selection in one view, such as parallel coordinate; views of that selection in a scatter plot matrix, and the table view. The detail dialog for a given molecule shows 2D structure depiction, an interactive 3D visualization when geometry is available and support for tagging and/or annotation. We have also developed an early preview of a web interface to the same data using ParaViewWeb, enabling you to share data more widely if desired. This also features a 3D interactive view using the ParaViewWeb image streaming technology which works in almost all modern browsers.</p>

<h2>Putting Them Together</h2>

<p>Each of the applications in the Open Chemistry suite listens for connections on a named local socket, and provides a simple JSON-RPC 2.0 based API. Avogadro 2 is capable of generating input files for several computational chemistry codes, including GAMESS and NWChem, and can use MoleQueue to execute these programs and keep track of the job states. Avogadro 2 can also query MongoChem for similar molecules to the one currently displayed, and see a listing sorted by similarity. MongoChem is capable of searching large collections of molecules, and can use the RPC API to open any selected molecule in the active Avogadro 2 session.</p>

<h2>Acknowledgements</h2>

<p>The development of the Open Chemistry workbench has been funded by a <a href="http://www.kitware.com/news/home/browse/OpenChemistry?2012_01_24&amp;Kitware+Receives+Phase+II+Funding+for+the+Development+of+a+Computational+Chemistry+Workbench">US Army SBIR with the Engineering Research Development Center under contract (W912HZ-12-C-0005)</a> at <a href="http://www.kitware.com/">Kitware, Inc.</a></p>

<p>Originally published on the <a href="http://www.kitware.com/blog/home/post/469">Kitware blog</a></p></span>
