+++
images = ["images/avogadro_volume_render.png"]
banner = "images/avogadro_volume_render.png"
menu = ""
description = "It is 2019, where are we at with Avogadro 2, and what are our plans for this year"
categories = ["avogadro, gsoc, chemistry"]
tags = ["open-science", "open-source", "programming"]
date = "2019-03-05T11:15:00-05:00"
title = "Avogadro Plans for 2019"
+++

The [Avogadro][avogadro] project was founded all the way back in 2006, and I participated as a [Google Summer of Code student][gsoc] with KDE in 2007 to bring a molecular editor to Kalzium. The library we were using was libavogadro, this powered Kalzium and the Avogadro application that provided a fuller interface (also using Qt as its base). From the start this was a project founded by a need felt by many of us who got involved in the early days&mdash;to have a solid, cross-platform and open source molecular editor. In addition, we wanted to provide a library that exposed these features.

<!--more-->

### Introduction

Back then I was a Ph.D. student in Physics, working in an experimental group. I started a small project that I never published, and had hesitated for a few years to apply for Google Summer of Code but in 2007 I took a look and found what looked like the perfect project. I already used KDE, C++, and Qt. The group seemed to share many of my goals, and so it seemed like a better idea to work with them. I learned a huge amount from my mentor Benoit Jacob that summer, and we were able to land a slew of new features. Thanks to KDE, GSoC and the Avogadro project my career took on a whole new direction, one that had been a hobby/passion until then&mdash;scientific programming, visualization, and forming communities around open source codes.

![SourceForge downloads statistics for Avogadro](/images/avogadro_downloads_2019.png)

Fast forward through a two year postdoc with Geoff Hutchison (one of Avogadro’s founders), and nearly ten years at Kitware (my current employer) and we arrive here. Avogadro has been downloaded over one million times since our first release, and it has been cited over 2,100 times since we published the paper in 2012! That is absolutely mind blowing to me, and I never dreamt that we would garner so much attention when I sat coding for hours on something that was a passion project. In those years I have learned a huge amount, grown as a developer, mentor, manager, author, proposal writer, presenter and more. We have also been able to grow a community around the project, and found new, related projects.

### Avogadro 2

Since we first developed Avogadro my ambitions grew. Everything we learned from the development of Avogadro 1.x led to an ambitious rewrite of Avogadro. We have been working on Avogadro 2 for quite some time, initially funded by a US Army SBIR (the first SBIR grant I obtained after joining Kitware), lots of our own time, and more recently some DOE funding.

The rewrite was not as easy as I originally hoped, and we hit some dead ends in developing some components. The world also insists on changing around us, which always keeps things interesting! The Avogadro 2 libraries were designed to be far more modular from the start, featuring core libraries that only need C++11, then layering on OpenGL, Qt and other dependencies in other libraries or plugins.

The licensing was also changed from GPLv2 to 3-clause BSD to permit much wider/easier reuse under a [permissive open source license][permissive-license]. This aligns with my employer’s commercialization strategy for open source, and offers reference implementations that can be freely reused by anyone. My thinking in this area has evolved significantly since I entered open source, and considering all of the complications arising from license compatibility, questions of distribution, compliance, whether a work is a derivative I strongly prefer the simpler permissive licensing model. I think copyleft has a place, but I am not convinced it is science, but this is a discussion for another time...

### More Reusable

One of the upshots of this is that the new Avogadro 2 libraries can be used without any rendering/graphical interface dependencies. This has enabled us to wrap the core libraries with PyBind11, and enable `pip install avogadro` to bring in those core modules. We are reusing core functionality in JupyterLab notebooks for file reading, orbital cube generation, and other pieces in web-based workflows. We are also reusing the same Python wrapped API in Python-based server plugins for an open chemistry data server.

{{< youtube mQ6iGz47QC8 >}}

The libraries are far more layered now, enabling us to bring in quite large dependencies such as [VTK][vtk] in libraries depending on the core. This means that we can optionally use VTK’s rendering capabilities to offer advanced volume rendering, flying edges for surfaces, and 2D charts without inflicting that dependency on all users of the library if we had one huge mono-library. This can make some of the development more complex, with core libraries building on C++11 only, but we are doing everything we can to achieve the right balance.

### Faster

Originally we depended upon some very object-oriented code for molecules, atoms, bonds, etc. We were able to rethink most of this from the ground up, and offer data structures that think in terms of allocating large arrays of contiguous memory. This makes reading, writing, and operating on large molecular data sets much faster. The creation of APIs focused on read/write, or editing/manipulation of molecules also offered a separation of concerns.

Moving from immediate mode rendering to a simple scene graph also entirely changed the way in which we rendered. This was mixed in with a move from OpenGL 1.1+ to OpenGL 2.1+ with buffer based APIs primarily. It made us rethink all of our rendering, and instead of instanced spheres we switched to impostor spheres that looked perfectly spherical no matter how much you zoomed in. This coupled with VTK later rewriting its entire rendering backend to take advantage of OpenGL 3.2+ has really changed what we can render.

### Open Chemistry

The [Open Chemistry project][openchem] was founded as an umbrella project for wider efforts related to the development of open source software for chemistry and materials science. We placed the Avogadro 2 development under that organization on GitHub for example, along with web-based projects for chemical data, web visualization widgets, JSON format documentation, Docker containers, and other related efforts.

This has also become an organization in the Google Summer of Code, and I am delighted that we have been accepted for our fourth year. It is amazing to be able to work with GSoC students, meet other mentors, and renew ties with people who supported us all those years ago in our early years. We have in turn been able to meet and work with a number of innovative projects, and [host them under our umbrella organization][gsoc-openchem].

### Final 2.0

When will 2.0 final be "ready"? The answer is I hoped years ago, in some areas it already excels and has for some time. It lacks feature parity in a number of important areas that need to be addressed, such as area selection for atoms/bonds, live "sculpting", etc. I am determined that 2019 is the year we call 2.0 final, and am making every effort to create the necessary time to make this happen. The definition of "ready" is somewhat subjective, and I have always been a fan of the saying that "perfect is the enemy of good". Avogadro remains my passion, and as the world evolves I want to ensure Avogadro evolves too.

We are first and foremost a community project founded and developed by people passionate about both chemistry/materials science and open source. We have been fortunate enough to gain funding for Avogadro development through various sources&mdash;Google Summer of Code for multiple students, DoD, DoE, and more. Ultimately software is sustained by people who wish to see it continue, and those people have finite time. Geoff Hutchison and I have worked for years to find the time and funding to keep pushing Avogadro forward, forging a common vision, and working with our community to support it.

I have some pull requests to finish up, some great new collaborations to make other elements of Avogadro better than they could have ever been before, and some web-based components that I am excited to share when they are ready. We need to move our OpenGL rendering code to 3.2+ core profile so that we don't fight bugs maintaining two very different OpenGL contexts. I would like to offer a richer file format containing more data on visualizations, processing pipelines, etc using optional elements in Chemical JSON.

I hope you will join us in making this the year we make Avogadro 2 shine, help us understand what you need to switch, and let's get ready to celebrate a huge new release! Last year we had our first Avogadro meeting, and we would like to continue to find ways to engage more with our community.

[avogadro]: https://avogadro.cc/
[gsoc]: https://cryos.in/kalzium-3d-molecule-editor-the-start-of-my-gsoc-project/
[permissive-license]: https://en.wikipedia.org/wiki/Permissive_software_licence
[vtk]: https://vtk.org/
[openchem]: https://openchemistry.org/
[gsoc-openchem]: https://openchemistry.org/gsoc/