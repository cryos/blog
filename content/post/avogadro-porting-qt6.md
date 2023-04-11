+++
categories = ["general"]
tags = ["development"]
images = ["images/avogadro-ethane-qt6.png"]
banner = "images/avogadro-ethane-qt6.png"
date = "2023-04-11T15:46:00-04:00"
title = "Avogadro Development and Porting to Qt 6"
menu = ""
description = "Some updates on getting Avogadro working with Qt 6"

+++

I don't post anything in years and then get on a three day streak!?! Don't expect this all the time, but I have been missing having an outlet, especially for more technical stuff as I work on it. Today I woke up and wanted to make a start on getting Avogadro ported over to Qt 6, while ideally continuing to support Qt 5.15 for at least a while. Qt 5 is end of life and it is something that has been bugging me wanting to take a pass at updating the code base. There haven't been meaningful updates to Qt 5 in years. Spoiler the screenshot above is of Avogadro running with Qt 6 on Linux.

![Avogadro built against Qt 5.15](/images/avogadro-ethane-qt5.png)

If you look above this text you should be able to see Avogadro build against Qt 5.15 using the same branch as below built against Qt 6.4 on Arch Linux. For now I have added options to the superbuild and both projects to set the major Qt version they will build against and it defaults to 5 right now. If you want to see the gory details there is a fairly big [Avogadro libaries pull request][avolibspr] and a much smaller [Avogadro application pull request][avoapppr]. At a high level before and after they are merged not a lot will change if you just build the projects as normal. Once they are merged I will also create a superbuild pull request to coordinate building.

![Avogadro build against Qt 6.4](/images/avogadro-ethane-qt6.png)

Build System Changes
--------------------

I started off with some build sytem changes to offer the option of building against Qt 5 or 6. As we will only support two major versions I opted for the enum like approach, and issue a failure if you get creative and inject other values in at configure time. In the CMake GUI you will be presented with a combobox offering the two supported values, and if you configure it on the command line you will be greeted with a hopefully intuitive error if you choose a value we do not support.
```
set(QT_VERSION "5" CACHE STRING "What major version of Qt")
set(QT_VERSIONS_SUPPORTED 5 6)
set_property(CACHE QT_VERSION PROPERTY STRINGS 5 6)
if(NOT QT_VERSION IN_LIST QT_VERSIONS_SUPPORTED)
  message(FATAL_ERROR "Qt version must be one of ${QT_VERSIONS_SUPPORTED}")
endif()
```

The next thing I had to do was port the other CMake code where a lot of things are versioned using the major version. I expected quite a bit of work but I was pleasantly surprised by some additions made in Qt 5.15 and 6 to support simpler migrations. Most of us only build with one major version within a single build because we like to keep things simple, and avoid spending time on things that don't really help us. I use out of source builds and can build against 5 and 6 there, but do not want a single build with both. To that end unversioned CMake commands and link targets are provided! This means that a lot of boilerplate I might have written, or conditional code I might have littered the build system with could be avoided.

Qt Code Changes
---------------

Once I had something that would configure it built straight away and I was done! I kid, I kid... I obviously spent most of the day working through various porting issues, spotting some patterns and cursing my former self. When we started developing the new code base I wanted to be more precise about what classes we used, and which modules they came from. At the time there was much debate in the Qt world about which style was better, but I really preferred being cognizant of adding new dependencies and being deliberate. I see the error of my ways and the build system is a much better place for us to express that when the include doesn't work along with the linker telling us.

So I got reacquainted with an old friend sed after doing the same thing two or five times. I would like to do this to the entire code base soon for consistency, but for now took a minimal approach with the classes that had moved and removed the module prefix from the includes that were causing issues. Something along these lines was run and then tested:
```
sed -i 's|QtWidgets/QAction|QAction|g' */*.cpp
```

There were also a number of things that had just changed, so I worked through a number of issues initializing the window flag defaults, realizing some things didn't need initializing as they were constructed with the expected initial values and then moving from qSort to std::sort (which I remember saying years ago we really should do). This got me through most of the libraries in the Avogadro libraries, but the plugins were a different story. In the libraries I made use of the Qt 6 Core5Compat library, mainly to support QRegExp which we use a lot but only in one library. A job for a willing volunteer or future me is to get rid of that, but I really appreciate it being offered to let me get this done in a day.

Disabling Some Plugins
----------------------

This is where I make up with past me, maybe even give him a pat on the back and say good thinking. The plugin code is focused, and written by a number of people with specific goals in mind. That code lives in a directory and it links to the relevant libraries to do things like rendering, opening dialogs etc. I worked through all of the easier cases and then disabled a number of plugins if the major Qt version is not 5. This lets us port the remaining plugins as and when we have time, if you want to use them now you can build with Qt 5 and even build them with 6 and get things working, and make a pull request.

Fast forward to this afternoon, I may not have done many of the other jobs I was asked to take care of on my day off but I have a working Avogadro! The main application code was much simpler to port, and required only quite minimal changes. It mirrors the same CMake code to offer the major version option, and built with relatively little effort. I will need to check that I am building as much of the code base as possible later, and probably make a follow up migrating the QRegExp code.

Vacation and Diving Back In
---------------------------

My kids are off school this week, and my wife is working hard doing people's taxes as the submission deadline gets closer. I decided to take the week off, get my taxes ready with her, and have been indulging myself. These last few years have been a lot and I have neglected a lot of the open source work I am passionate about and enjoy. When I architected Avogadro I thought really hard about how I could modernize both the C++ and CMake, now I see both have moved on and have new capabilities. I am hoping to take another pass to bring them both up to date.

Will I keep posting every day? Maybe this week, who knows? My son is learning to code and I am trying to help him with that. Alas there is yard work, DIY, taxes and other stuff that needs my attention so no promises.

[avolibspr]: https://github.com/OpenChemistry/avogadrolibs/pull/1241
[avoapppr]: https://github.com/OpenChemistry/avogadroapp/pull/361
