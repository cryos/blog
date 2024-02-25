+++
categories = ["development", "C++", "lego"]
tags = ["development", "general"]
images = ["images/202402-lego-toys.jpg"]
banner = "images/202402-lego-toys.jpg"
date = "2024-02-25T18:45:00-04:00"
title = "Toy Projects and Lego"
menu = ""
description = "A tangent on the importance of toy projects and Lego"
+++

And now for something completely different...a random glimpse into my mind and how I keep things fresh. I am not sure I have ever stated this for the internet at large but I like building Lego and you can see some of my Lego air and space exhibit in the photo. I was thinking about this in the context of programming projects and giving space to explore what is possible along with learning new skills without other pressures.

Working on Vacation
-------------------

I am sure that this would horrify some (many) people but when I was hoping to make a move back into tech I took a week off and dove into build systems. It started out with [GitHub Activity and Single Sign-on][github] where I was contemplating what I might look like to the wider world, and then I worked on [porting Avogadro to Qt 6][avogadro-qt6]. After that I moved on to [Avogadro, VTK Charts and Parenting][avogadro-vtk], [PIMPL, Stability and C++ Libraries][pimpl-stability], then onto some of the bigger issues exploring [Modern CMake and Avogadro][modern-cmake], [Compiler Warnings and Avogadro][compiler-warnings] and ending on [Target Property Based Modern CMake][cmake-target-properties].

Long story short this was a personal exploration of a bunch of things I had been wanting to look at for a while in a project I founded but really hadn't made time to look at in a good while. It was fun to carve out time and decide what I wanted to focus on. It was influenced by a job posting I had looked at in late March/early April and wanting to freshen up my skills but the primary driver was just wanting to get back to some coding/build system work that I used to do all the time. I have friends at the lab who would laugh at my admission of working on vacation as I used to lecture them on unplugging when they take time off, I can be a hypocrite at times...

Pure Toy Project
----------------

I had thought about continuing on in that vein but the Avogadro project has a lot of constraints upon it as an open source project with other contributors. Fast forward I got that [new job][voltron-data-job] in July last year which as many big changes tend to caused some disruption but I recently got back to some exploratory development. I wanted to go a little more extreme than I had in the past in terms of not supporting every platform where it often becomes the lowest common denominator, I also had a laundry list of technologies I wanted to explore including [C++ modules][cpp-modules], [using vcpkg instead of superbuilds][vcpkg-superbuilds] and [DuckDB in a C++ project][duckdb-cpp].

I have no predetermined outcome but going in I wanted to shed the need to make things build anywhere other than my Linux desktop. Really push on things like new C++ language features that don't work everywhere, new ways of adding dependencies and how the whole columnar database interacts with the C++ language. If you have followed my career at all and read some of the posts I am absolutely looking for some of the fast paths and thinking of things like interactive data visualization.

What Next
---------

I am hoping to dive deeper into Arrow and storing/moving binary data around efficiently. I also want some freedom embracing the new startup lifestyle of just throwing everything away and exploring a blank canvas. Avogadro 2 was a from the ground rewrite with all I learned and many years later it still isn't "ready" according to some preconceived list of requirements to equal the original. This is me in some of my own time exploring fresh approaches if I started all over again with C++20 (or above), modern packaging and the new wave of columnar data stores that offer huge amounts of work in exposing them across many languages.

I have not figured out if this would be better ported into an existing project and I don't think I need to figure that out. The same thoughts occur with regards to tomography and multidimensional sensor data: I think that columnar data layouts with native C++ typing that can be efficiently accessed across languages have huge power. Storing raw image data in some columns along with all the different metadata and then thinking about efficient loading, saving and ideally out-of-core processing approaches.


![Lego International Space Station](/images/202402-lego-iss.jpg)

I don't know if having toy projects is right for everyone, I don't know if blogging about them is either. These are just my opinions on what works for me and wanting freedom to really explore more deeply emerging approaches. I have always had a real passion for developing beautiful APIs and building code in a portable fashion which is reflected in my background starting with Gentoo packaging, then KDE/Qt cross-platform development and years at Kitware working to make well-tested cross-platform visualization and analysis software. I think this is a really exciting time in software development when the language is changing in significant ways and we should reassess some of the old ways of doing things.

All About the Data
------------------

One truth that rang true and one that perhaps precipitated my last two moves has been the realization that it is all about the data. It is exciting to see a new generation of open source projects that are turning things on their heads. We have this deluge of data and we need to get a handle on it, and a lot of the work I have done has been addressing that issue. I like to visualize that data and interact with it, but most of the time is spent wrangling databases, file access, data movement and data processing before anything is ready for visualization.

Don't give me too much credit for any kind of master plan at this point, more wanting to revisit a number of things that have limited past projects and get a deeper understanding of new approaches through some experiments. At the core I guess I am still that physicist in the lab but instead of something really cool like space travel (see that Lego exhibit) it is data exploration and analysis. Hopefully others enjoy reading or think about things they might want to explore.

Some of this helps nurture ideas for my day job, or formulating ideas for future work but some of it is like space exploration where I don't know where I end up!

[github]: {{< ref "github-activity-oddness" >}}
[avogadro-qt6]: {{< ref "avogadro-porting-qt6" >}}
[avogadro-vtk]: {{< ref "avogadro-vtk-charts-parenting" >}}
[pimpl-stability]: {{< ref "pimpl-stability-cpp-libs" >}}
[modern-cmake]: {{< ref "modern-cmake-avogadro" >}}
[compiler-warnings]: {{< ref "modern-cmake-avogadro" >}}
[cmake-target-properties]: {{< ref "target-property-cmake" >}}
[voltron-data-job]: {{< ref "startup-voltron-data" >}}
[cpp-modules]: {{< ref "cpp-modules-cmake" >}}
[vcpkg-superbuilds]: {{< ref "cmake-superbuilds-vcpkg" >}}
[duckdb-cpp]: {{< ref "duckdb-and-cpp" >}}
