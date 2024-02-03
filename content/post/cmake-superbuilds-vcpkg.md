+++
categories = ["cmake", "C++"]
tags = ["development"]
images = ["images/angohr-fmt.png"]
banner = "images/angohr-fmt.png"
date = "2024-02-03T13:45:00-04:00"
title = "CMake, Dependencies, Superbuilds and Vcpkg"
menu = ""
description = "Some discussion of CMake, dependencies, superbuilds and more modern approaches like vcpkg"
+++

I was a [Gentoo][gentoo] developer before I got serious about C++ software development, and one of the things we hated most about packages was when they copied libraries into their codebase. From the developers point of view they just want to be able to build their codebase, and copying in code so you can just build it all in one go is the easiest way to achieve that if there is no solid packaging story. This was very much the case back then and a lot of patches were to link to system libraries.

Dependencies, APIs and Packaging
--------------------------------

Taking a step back and explaining that most C++ projects reuse some code, and accepting that there has not been a solid cross-platform packaging story for C++. This has meant if you just develop on one distro or OS you can rely on them, so offer instructions to install all dependencies for Ubuntu 22.04 and RHEL 8 for example. Sooner or later you need a newer library than they provide, maybe you copy it into your source. If you are very well behaved you hopefully don't change its API and offer a flag to compile against the system libraries.

I have developed libraries and APIs for many years now, along with packaging libraries on Gentoo, in superbuilds and other places. One day the library changes its API, some libraries do this every release (scream into the bag), others offer amazing guarantees but still make changes over major releases. Qt in my mind is the gold standard in C++ offering both API and ABI stability that they have achieved for decades now. They routinely add features to their API in minor releases while maintaining API and ABI stability.

Even for [Qt][qt] the major releases are a pain, and they often don't make major versions easily co-installable. Gentoo did a lot of work in that area of slotting libraries, and many distros have made Qt and other libraries co-installable to the point where I routinely install Qt 5 and 5, Python 2 and 3, etc. In other cases, such as old work in VTK we would compile in versions of external libraries but mangle their symbols so that users of the API could link against a system version of that same library.

Superbuilds
-----------

You can see a post I wrote in 2017 [CMake Superbuilds and Git Submodules][superbuilds] to see a summary of some of the work I have done in the past with CMake superbuilds. I worked on some of the earliest versions of superbuilds and highlight three major types that I used back then: developer build, packaging build and a dependency build. I worked on a number of complex projects where I wanted to avoid copying code into my project, and strongly favored the use of Git submodules coupled with CMake superbuilds to get new and existing developers up and running quickly on Windows, Mac and Linux.

There was a fair bit of work to standardize superbuilds over the years, but ultimately you could never really copy and reuse build recipes easily. You could use others as a starting point for sure, but each superbuild was a custom island. It did get all developers across all these platforms up and running, but I was never really satisfied with the solution. It also did terribly at caching or reusing builds across different projects or the same project on your machine. The build was also kind of complicated, as you had a two phase top-level versus inner project where you pretty much managed the build order by hand and your "real" project was the last one.

Vcpkg and C++ Packaging
-----------------------

These days we have a growing number of options to easily add external projects as dependencies in your C++ project. A few of the biggest concerns then become how well they integrate with your build system, dependency management and handling static/shared libraries coupled with release/debug builds. A few of the options in this space  are the [CMake Package Manager][cpm], [Conan][conan] and [Vcpkg][vcpkg].

They all have their pros and cons, I don't have a clear favorite. I have used the CMake Package Manager and Vcpkg the most at this point, and took a look at Conan to see how it compared. The one thing they all have in common is that they largely make the superbuild defunct, but there can be a steep learning curve to get to a point where you might fully replace what it does for you in your project.

The Vcpkg project is something developed by Microsoft, I will admit that made me skeptical of the project as a primarily open source developer preferring Linux as my development platform. They have some interesting takes on shared libraries on Linux, and there is a clear preference for the proprietary Windows platform in places but all-in-all it works well. It relies upon some serious git magic for package versions which don't feel so simple.

I will say one of the coolest things they did from an end-user perspective is offering a simple JSON file (`vcpkg.json`) where I can express project dependencies and that is enough to bring them in. [This commit][addvcpkg] adds the baseline and the dependency to my example project, with the below showing you what a simple dependency looks like:
```
{
  "dependencies": [ "fmt" ]
}
```

The oddest limitation, at least for me, is that I can only specify a `>=` version dependency, I cannot pin to a major version, or pin greater and less than. You have a few options such as creating your own registry with your own recipes, and custom versions, or specifying what they call `overrides` where you can only specify the exact version (no looser pinning for less than). So hardly a lost cause, and still far easier than doing everything by hand. You can also specify the baseline version of the upstream ports, your custom repositories etc and so explicitly pin everything.

Another thing to realize is that all that complication above with superbuilds being two phase is still true, it just got shifted. Effectively in order to satisfy your dependencies in your project they are invoked during the configure phase, which can now take hours as everything builds! I can't help but think we need a new phase in addition to configure and generate but that is how it is. There is output to let you know what is happening, but it can be a little startling at first.

CMake Presets
-------------

The Vcpkg stuff works OK, but if you look at some of the suggested command lines from Conan or Vcpkg they are pretty clunky to say the least! One thing you can do to make them easier to use in your project is to add a [`CMakePresets.json`][presets] file that specifies a few things. Due to the way CMake is written you have to provide the toolchain file on the command line, and this is the mechanism both projects use to add themselves to your project.

In a presets file you can specify a number of things that traditionally needed to be on the command-line. This means that a single named preset can offer a default generator, toolchain, build directory and many other components.
```
{
  "version": 8,
  "configurePresets": [
    {
      "name": "default",
      "binaryDir": "${sourceDir}/build",
      "generator": "Ninja",
      "cacheVariables": {
        "CMAKE_TOOLCHAIN_FILE": {
          "type": "PATH",
          "value": "$env{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake"
        },
        "VCPKG_INSTALLED_DIR": {
          "type": "PATH",
          "value": "${sourceDir}/vcpkg-installed"
        },
        "VCPKG_TARGET_TRIPLET": {
          "type": "STRING",
          "value": "x64-linux-dynamic"
        }
      }
    }
  ]
}
```

Now I can just type in `cmake --preset default` and all of the above are set in the build tree created! This includes the injection of Vcpkg into the project and fetching, compiling and installing `fmt` to use in the project. This [commit][addfmt] shows an update to the presets, along with adding the CMake and C++ changes to make use of the library. CMake doesn't know or care if this is a system library or a Vcpkg library and so either way it would work. Just the way in which you configure the project determines whether Vcpkg is added or not.

Presets and IDEs
----------------

Another side benefit of the presets file is that IDEs such as [vscode][vscode] know about it. This means that they will read the presets JSON file and can offer the different presets, configuring and building your project. This offers a lot of freedom to offer nice defaults for your project our of the bag with a user preset that can override what you offered.

This can offer one of the best onboarding experiences if you get it right as more IDEs/editors expand to supprt this simple standard they can invoke CMake. A project should aim to have sane defaults with no preset or options supplied, but you often want some concept of "everything", "as little as possible", along with "release" and "debug".

I am not sure of the best way to achieve some of the combinatorics I already want. Ideally something like Linux, everything, release and debug variants, Linux minimal, same as before, Windows everything, etc. You might consider auto-generating the JSON to avoid hand-editing, maybe there are some mechanisms I am missing. I would welcome suggestions on that, but worst case it seems like I could specify matrix and mix-ins and have code fill in all the combinations.

Final Thoughts
--------------

Hopefully an interesting read, it definitely feels like time to move on for new projects and time to consider upgrading for existing projects. From what the different C++ package managers have to offer the CMake Package Manager feels best suited to small dependency sets whereas Conan and Vcpkg seem ready to deal with bigger and more complex dependencies. I think one of the big hurdles with all of them is building all the combinations wanted and caching binaries for CI, developers and others to make build times tractable.

[gentoo]: https://gentoo.org/
[superbuilds]: https://www.kitware.com/cmake-superbuilds-git-submodules/
[cpm]: https://github.com/cpm-cmake/CPM.cmake
[conan]: https://conan.io/
[vcpkg]: https://vcpkg.io/
[addfmt]: https://github.com/angohr/angohr/commit/73e5043994b8a0bd7a0d2d887e63ad080a712fd3
[addvcpkg]: https://github.com/angohr/angohr/commit/8549636e563ac0ac7c5a392d0697c49d2356454e
[vscode]: https://code.visualstudio.com/
[presets]: https://cmake.org/cmake/help/latest/manual/cmake-presets.7.html
[qt]: https://www.qt.io/
[angohr]: https://github.com/angohr/angohr
