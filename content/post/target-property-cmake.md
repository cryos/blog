+++
categories = ["general", "avogadro"]
tags = ["development"]
date = "2023-04-18T19:25:00-04:00"
title = "Target Property Based Modern CMake"
menu = ""
description = "Updating the Avogadro build system to use more modern target properties over variables."

+++

Something an old mentor told me to never do is call a thing "Modern ..." as you can guarantee someone will be chuckling in 10-20 years. I can neither confirm nor deny that I found myself sitting at my desk at gone 1am immersing myself in what "Modern CMake" was exactly, and what I wanted to apply to the Avogadro build system. It seems to have its nucleation in about 2017 where I find a number of posts, talks, etc.

Modern?
-------

I designed Avogadro 2's build system to be "modern CMake" as I had debated with many at Kitware and in the KDE community. I even had compliments on how self contained things were, along with critiques of whether it was really right to call `find_package` for the same package more than once in a project. I was proud of what we had back then, but it is indeed showing its age. I was also involved in discussions of Boost's CMake-based Ryppl project.

Superbuilds
-----------

I wrote some of the first superbuilds for a project called Titan with Sandia National Labs, I added superbuilds for the Open Chemistry projects and Tomviz too. These were primarily to aid in getting developers up and running, and to avoid adding third party libraries/dependencies to my project itself. Being a former maintainer I felt the disappointment when half my packages had internal copies of stuff I was packaging, and now I had to try and untangle it!

Namespaces in CMake
-------------------

One of the things you get to learn about CMake is that everything is a string! It causes lots of issues when developing complex build systems (or even simple ones) depending on quoting, even something you `unset` is just an empty string. With namespaces the use of `::` guarantees to CMake that what it is looking at cannot be a valid file name, and so it must be a target where traditionally you would get right to the end of the build and see the linker fail to link to some string that was clearly supposed to be a target but "bad things happened".

The counter-intuitive thing, at least to me, is that you cannot use namespaces with `add_library` to add a library target, but you can use `add_library` to add an alias to your library target. Why would you do that you ask? Mainly, and this is just my opinion, to enable dependent targets to reference the namespaced target in your project the same way an external consumer of your project would. You cannot do much else with the alias and must work with the "real" target. So this became core to my redesign.

Target Source Properties
------------------------

"Old CMake" was all about variables, and for me in my more modern take accumulating lists with `list(APPEND ...`. In new CMake I can add a library that contains nothing, I am pretty sure I couldn't do that before. What this offers is the ability to define a bare target, and then to accumulate source files and other properties on the target directly. This is less error prone and the data model for targets is richer these days. This is far closer to what I wanted when I first started using CMake, and I am glad to see so many features get added to CMake to support building, installing and reusing C++ libraries.

One of the bigger features that was only added in CMake 3.23 was the `FILE_SETS` property where I can add public headers for the targets, specify their base directories and install them all from the target. This also sets the build time include directories automatically for that target so that users of the library automatically see it in my build tree. This offers a reduction in the complexity of the build system even if it requires reversing the order of commands. It used to be that I would accumulate all of the variables for various things and only then add the library, now I want to add the bare library upfront and then accumulate properties on it.

Changing Dependent Code
-----------------------

The changes required in the Avogadro application were very minimal in the end. You can see the [pull request][prlibs] for the libraries is quite lengthy, where as the [pull request][prapp] for the application was just adding the double colons for the namespace in. I chose to use the common prefix of `Avogadro::` and then shortened the library target names to things like `Core`, but in order to avoid file collisions I set the `OUTPUT_NAME` to retain the `Avogadro` prefix it has had for years. This results in the target going from `AvogadroCore` to `Core`, but the exported/alias target being `Avogadro::Core` and the output name of the library being prefixed, so on Linux it remains `libAvogadroCore.so`.

It seems a shame that the prefix isn't automatically incorporated, but it isn't hard to do as you can see in the diffs. I think that I likely want to rename the `avogadro_add_library` command to something more descriptive, but left it for now. Whilst it is always a shame to cause churn in how people reusing the libraries refer to the libraries I think in this case it is worth the short-term pain. The patch is very simple and other users can address it rapidly, it will result in more robust build system code. The automated builds are all a little broken due to the change in target names.

Fixing Dependencies
-------------------

The thing I need to look at next is improving how the dependencies are brought in, they need to use namespaces, set their include directories on the imported targets. That will let me simplify the code both within the libraries repository and the application repository as they will expose things like the Eigen include directories as Eigen is part of the `Avogadro::Core` interface. I think this is likely enough for one set of pull requests and I would like to avoid changing too much in one go so that I can see what other impacts there might be.

[prlibs]: https://github.com/OpenChemistry/avogadrolibs/pull/1264
[prapp]: https://github.com/OpenChemistry/avogadroapp/pull/364
