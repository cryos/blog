+++
categories = ["general", "avogadro"]
tags = ["development"]
date = "2023-04-14T15:20:00-04:00"
title = "Modern CMake and Avogadro"
menu = ""
description = "Quick update on some minor modernization work in Avogadro's build system"

+++

Not that I am counting, but this is day six. I thought that there was a good chance I wouldn't make it today as I had a few other commitments but here we are. When I first designed Avogadro's build system I made it as modern as I could at the time, and then reluctantly wasn't as aggressive as I might have liked in pushing the minimum version higher for modern CMake features. Today I had a chance to take the first step in addressing some of that by adding target include directories to the Avogadro libraries.

Project Add Library Command
---------------------------

Like many projects the Avogadro build system adds a project specific add library function, imaginatively named `avogadro_add_library` shocking as it might be. This function will first call `add_library` from core CMake, then a little regex to turn `AUTOMOC` on if it is a Qt-based library, before setting the version of the library. It also takes care of generating an export header, and tweaking include directories.

Until I made a PR this morning it had not used the new (to Avogadro's build system) `target_include_directories` capability. Instead as each `add_subdirectory` call was made the include directories were globally added to for each library. This was a compromise at the time to make things as modern as we could without all the fancy target properties.

Build and Install Interfaces
----------------------------

One of the other things we have always done well in projects I have developed is let you build against a build tree or an install tree. Now if you want to use `target_include_directories` and continue supporting that than generator expressions are needed. They let us specify our include directories for both the build and install tree, and the expression will be evaluated later when something wants to consume the target we are creating.
```
  target_include_directories(${name}
                             PUBLIC
                               "$<BUILD_INTERFACE:${CMAKE_CURRENT_BINARY_DIR}>"
                               "$<INSTALL_INTERFACE:${INSTALL_INCLUDE_DIR}>")
```

Simplifying Our Build System
----------------------------

Adding the above means that within our build system as we build, or as the Avogadro application builds against our build tree, or as someone builds against the installed Avogadro libraries we can just add the target to our `target_link_libraries` call and avoid changing the global using `include_directories`. This allowed me to remove a bunch of `include_directories` calls, and carry that information with the target only to the things that state that they want that target.

This obviously broke a few things as it is much more granular and over the years a few things snook in. Normally you would get an error about missing symbols, but Avogadro has a number of templated or inline classes, especially in core that will just be built straight into the calling code. I found a number of those instances and now the build system is more robust as it will fail much earlier if it attempts to include headers for libraries there is no dependency specified for.

So I put this together into a new [pull request][pr]. It also highlighted that I should probably pull a lot of the header only code into a header only library that is much easier to express these days. I pulled apart a header that was trying to be a little too helpful, and then added a few dependencies that are needed. I think as a follow up I would like to separate out an enum into a separate header, and consider properly separating the header only part from the core.

More To Do
----------

There is more to do here, this is just the first step. Another aspect I want to tackle next is moving the libraries into a namespace as that is now generally expected as well as offering more protection in CMake - it will always be interpreted as a target (and not a string as most things fall back to in the end). There are also a few things to look at in terms of packaging, policy changes since bumping the CMake minimum version.

It has been fun getting back into some of this and seeing real impacts modern approaches can have on a not only the build system but immediate feedback if implicit dependencies are creeping in.

[pr]: https://github.com/OpenChemistry/avogadrolibs/pull/1246
