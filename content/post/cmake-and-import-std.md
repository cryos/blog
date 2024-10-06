+++
categories = ["development", "C++"]
tags = ["development"]
images = ["images/cmake-import-std.png"]
banner = "images/cmake-import-std.png"
date = "2024-10-06T14:15:00-04:00"
title = "CMake and import std"
menu = ""
description = "Exploring recent advances in the import std progress for C++ modules in CMake/C++"
+++

I started exploring this way back in May but other things got in the way. This had to wait and stay in my backlog but it is something I have been thinking about quite a bit along with what mature use of modules in C++ might look like. I would preface this with the fact that even with many months of delays in me writing this up that modules and the import of the standard library in particular are both at a relatively nascent stage...

Are We There Yet?
-----------------

After reading a recent blog post about "[import std in CMake 3.30][std-cmake]" I felt like it was a good time to revisit importing the standard library. The first thing to note is that while C++ modules are a feature of C++20 importing the standard library actually requires C++23. With that in mind my first instinct was to see if my toy project compiles cleanly when C++23 is enabled. That was when I discovered that my previous [DuckDB experiments][duckdb-cpp] exposed issues in the DuckDB API where it triggers compile errors.

So upon seeing that I figured I would just split the module in two, I had been meaning to for a while. This is a small toy project and so it isn't strictly necessary to split them but it is a good idea when you add large dependencies such as DuckDB. This isn't really "core" and so I created a new module called data and moved the DuckDB usage there. I then ported the simple test code over and now I have two modules in my fledgling project (shown in [this commit][data-move-commit])!

Then I was ready to enable the standard module import for my core module, but I hit another issue where `error: GNU extensions was enabled in PCH file but is currently disabled` - this has been reported and at this time you have to enable extensions to use this feature, i.e. `CXX_EXTENSIONS ON` for all targets linking to the module. You also have to be careful to compile everything with the Clang standard library which has not been standardized yet ([open issue here][cmake-std-lib]). I compiled the whole project with the following on Arch Linux:
```
CC=clang CXX=clang++ CXXFLAGS="-stdlib=libc++" cmake --preset default \
  -DBUILD_TESTS=OFF -DDuckDB_DIR=/home/marcus/src/duckdb/clangbuild

cmake --build build
```
Then I get a successful build, but if I turn testing on then I see a failure. I am using clang 18.1.8 right now, and upon searching I see [a reported error that matches][clang-redef-issue]. This is fixed in trunk and likely clang 19 but the packages aren't yet available and this was very much an exploration of what I might get working in Arch Linux with everything updated as of today. You can see the [commit enabling `import std`][import-std-commit] if you are interested in the details.

Progress
--------

Hopefully this post is useful, it is just documenting where I was able to get and some of the pitfalls I hit when building a project with a few dependencies attempting to make use of the C++ module for the standard library. I think for now I will leave it alone and revisit once I have clang 19 available as a package (or I have more time and want to start compiling everything).

It also highlights one of the weaknesses in `vcpkg` I hadn't thought about where it is essential to ensure that dependencies are all compiled with the same compiler and standard library. Without doing that there were issues linking where `spdlog` and the standard library interacted. It makes sense but in the past I hadn't needed to be quite so careful and also hadn't been trying to change the standard library the project linked to, there are hopefully more elegant ways to handle that in future.

Moving Mountains
----------------

If it doesn't come across I am amazed at the progress, people are moving mountains and I am largely an interested observer at this point. Life, work and all the other stuff has been crazy as of late which has offered less time than I had hoped to do fun exploration work like this. The warning from CMake clearly states that this is "meant only for experimentation and feedback to CMake developers". As it turned out the things I came across were already known.

It is an exciting time to see C++ move forward and the potential especially for being able to more efficiently use the standard library. Compile times alone are a huge issue with many workarounds that I spend time in my day job working on to improve them that come back the ancient `#include <blah>` lines you see at the top of so many source files. Compile times are just one aspect of what makes modules useful and I look forward to the day we can start using them in production code.

[std-cmake]: https://www.kitware.com/import-std-in-cmake-3-30/
[cpp-modules]: {{< ref "cpp-modules-cmake" >}}
[vcpkg-superbuilds]: {{< ref "cmake-superbuilds-vcpkg" >}}
[duckdb-cpp]: {{< ref "duckdb-and-cpp" >}}
[data-move-commit]: https://github.com/angohr/angohr/commit/8812d549f75faadea2d58fb63f190f78c63a41c4
[cmake-std-lib]: https://gitlab.kitware.com/cmake/cmake/-/issues/20851
[clang-redef-issue]: https://github.com/llvm/llvm-project/issues/91111
[import-std-commit]: https://github.com/angohr/angohr/commit/7b2452bf1d37f468e4ee247bc83439f62c7e89be
