+++
categories = ["general"]
tags = ["personal"]
images = ["images/vckg-cmake-presets.png"]
banner = "images/vckg-cmake-presets.png"
date = "2024-03-02T19:33:00-04:00"
title = "Vcpkg, Conan or Spack for C++ Dependencies in a CMake Project"
menu = ""
description = "After a recent post on Vcpkg a few people asked about Conan and Spack so I decided to explore them a little more deeply"

+++

I have been [using Vcpkg a little][vcpkg-superbuilds] and getting to know it better. I also took a look at [Conan][conan] but haven't really dove into [Spack][spack] recently. I am interested in them all through the lens of a developer who wants to improve the handling of third-party dependencies. This isn't intended to be exhaustive but more to examine a specific use case that interests me most: handling the dependencies for my project in the most elegant was possible where some dependencies are large needing some caching.

Conan
-----

Out of the gate one thing that put me off of it was the Python requirement meaning that I have a pretty big dependency to build all of my dependencies. With that said the installation is pretty simple:
```
mkvirtualenv conan
pip install conan --upgrade
```

There is also a package in AUR on Arch Linux. Once you have that then you will need to create a `conanfile.txt` that contains your dependencies along with a Conan profile using `conan profile detect --force`. The profile contains things like the C++ standard to use and the build mode. So you would need to create a profile for debug, release, etc.

One thing I like about the default way of specifying dependencies is the use of versions in the spec. So the following is what I added to my `angohr` repository to satisfy the same vcpkg dependencies:
```
[requires]
fmt/10.2.1
gtest/1.14.0
spdlog/1.13.0

[generators]
CMakeDeps
CMakeToolchain
```
Then to install these dependencies using the profile:
```
conan install . --output-folder=build-release --build=missing
```
Once you have done that then the command adds `CMakeUserPresets.json` to include files from that directory automatically, this meant that my existing presets were not easily reused. For the purposes of testing I went with the following:
```
CC=clang CXX=clang++ cmake -G Ninja --preset conan-release -DDuckDB_DIR=/home/marcus/src/duckdb/build
```

Once that was done and I fixed a bug in the CMake code I was able to compile the project and run the tests successfully. This [commit][conan-commit] shows the addition of the dependencies file along with a fix to actually find and use `spdlog` that it uncovered.

Spack
-----

Spack has a similar dependency that put me off of Conan in that it is Python-based, meaning my dependency build has a fairly large dependency. I get that we usually have Python available, so not a deal breaker by any stretch. It also offers cloning or an AUR package for Arch Linux. I tried using the package but every time I ran it I was asked for elevated privileges which I don't want in this context! So cloning it is:
```
git clone -c feature.manyFiles=true https://github.com/spack/spack.git
. spack/share/spack/setup-env.sh
```

This offered an install that wasn't trying to get more privileges, next how to specify my project dependencies. The documentation is extensive, reading through it looks like environments are probably what I want in this context.
```
spack env create angohr
spack env activate angohr
```
Then there is a little oddness that you add specs to environments
```
spack add fmt
spack add googletest
spack add spdlog
spack install
```
This led to the biggest set of installs out of the three package managers with things like autotools, gcc, cmake and perl flashing across my screen. It may be the most self-contained but that is not something I particularly need. Installing those three packages resulted in:
```
$ spack find
==> In environment angohr
==> Root specs
fmt   googletest   spdlog

==> Installed packages
-- linux-archrolling-zen4 / gcc@13.2.1 --------------------------
berkeley-db@18.1.40                 diffutils@3.9       googletest@1.14.0  perl@5.38.0
bzip2@1.0.8                         fmt@10.2.1          libiconv@1.17      pkgconf@1.9.5
ca-certificates-mozilla@2023-05-30  gcc-runtime@13.2.1  ncurses@6.4        readline@8.2
cmake@3.27.9                        gdbm@1.23           nghttp2@1.57.0     spdlog@1.12.0
curl@8.6.0                          gmake@4.4.1         openssl@3.2.1      zlib-ng@2.1.5
==> 20 installed packages
```
This feels like a lot for a relatively small set of lightweight libraries.
```
CC=clang CXX=clang++ cmake -B build -S . -G Ninja -DDuckDB_DIR=/home/marcus/src/duckdb/build
cmake --build build
```
This configured, but it failed to compile as it looked like the `spdlog` was using a built-in copy of `fmt`. I am sure it is something that could be fixed but a disappointing out of the box experience. All in all the most `conda` like experience in creating an environment, you can create a YAML file in the code directory to specify dependencies which was a little further down in the environments section.

Vcpkg
-----

I would say that Vcpkg has the steepest learning curve in many ways having to learn about triples (specifying build parameters), git magic for creating ports that use git trees, and specifying the presets. Once you have done that it also offers a build environment with the least number of dependencies and the tightest integration with CMake. The following will build a project:
```
cmake --preset default -DDuckDB_DIR=/home/marcus/src/duckdb/build
cmake --build build
```

The specification of the dependencies is among the simplest with a `vcpkg.json` you add to your source tree:
```
{
  "dependencies": [ "fmt", "gtest", "spdlog" ]
}
```

The thing I disliked also becomes a huge advantage, it is deeply integrated with git and I can specify the base SHA for the registry I wish to use. This locks all dependencies in place until that SHA is updated:
```
{
  "default-registry": {
    "kind": "git",
    "repository": "https://github.com/microsoft/vcpkg",
    "baseline": "80403036a665cb8fcc1a1b3e17593d20b03b2489"
  }
}
```

The thing I am not as keen on, but I have grown to accept is the use of the configure step to make all of this work using the presets makes it simple, adding the following entry will make a preset use vcpkg:
```
"CMAKE_TOOLCHAIN_FILE": {
  "type": "PATH",
  "value": "$env{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake"
},
"VCPKG_TARGET_TRIPLET": {
  "type": "STRING",
  "value": "x64-linux-dynamic"
}
```
The upstream clearly doesn't think we should use dynamic libraries on Linux, I strongly disagree but they also provide several mechanisms to make use of it too. Another disadvantage in my mind is defaulting to building debug and release versions of every package which takes twice as long and is often not needed. There are tricks you can employ to avoid this, but it is irritating that is the default position.

CMake Package Manager
---------------------

I mention the CMake package manager, I would put in in a different category to the above three as it offers no dependency resolution or caching of binaries. It is extremely convenient to pull in small dependencies, you can grab them from git repositories and configure/build them with minimal effort. I would recommend layering this on top of whichever approach you choose above for those small dependencies that use CMake.

It is a pure CMake implementation, minimal additional dependencies (just some CMake code) and there are a number of good examples to be found. The other package managers all offer ways to add your own package but none can match the simplicity. It is also very well integrated with CMake and your project can use it quite seamlessly but for anything that takes more than 20-30 seconds to configure and build I would probably pull in one of the above three.

Conclusions
-----------

All three variants used an externally build DuckDB for comparison. All three supplied three dependencies that they had existing packages for with minimal effort on my part. They vary mildly in how you specify what your dependencies are employing an INI style file, YAML or JSON but it is easy to translate between them. The bigger difference is in how they make these dependencies available and the level to which they integrate with CMake.

I have honestly just spent a half hour or more looking through the documentation for all three (plus the bonus one). I have made more extensive use of Vcpkg and the CMake Package Manager so it is possibly what is reported above is tinted by more time being spent on them. I have also looked at this pretty heavily through the lens of the easiest possible developer experience I might offer.

Another thing I was considering was the improved integration of CMake presets with IDEs such as VS Code. I only see Vcpkg and CMake Package Manager as offering a great "out of the box" experience for developers where they can choose a preset that would bring in the package manager and build all dependencies before building the project. When maintaining code Vcpkg will also update dependencies upon rebuilds of newer source which is quite an advantage. Conan and Spack seem to suffer from the detached build tree issue, which you can use Vcpkg in too, if I am missing a mode where they can both operate like that I would be interested.

I find the version specification for Vcpkg to be disappointing where I can only ask for `>=`, but they offer an overrides capability to exactly specify too. The deeper use of git in Vcpkg fills me with more confidence that I can choose when to update dependencies and do so in an atomic fashion in my repository. All four options discussed feel superior to the "superbuilds" I used to author, and satisfy package reuse we wanted back then.

[vcpkg-superbuilds]: {{< ref "cmake-superbuilds-vcpkg" >}}
[conan]: https://conan.io/
[spack]: https://spack.io/
[conan-commit]: https://github.com/angohr/angohr/commit/e5774a61a4b68963a987423f61b5671cc9e41445
