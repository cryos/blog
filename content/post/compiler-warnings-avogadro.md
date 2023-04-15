+++
categories = ["general", "avogadro"]
tags = ["development"]
date = "2023-04-15T17:35:00-04:00"
title = "Compiler Warnings and Avogadro"
menu = ""
description = "Thoughts on keeping compiler warnings under control or just turn them off"

+++

When we started the Avogadro project we were quite deliberate in what compiler warnings we added, and in keeping them to zero wherever possible. These last few years I have not been as involved, CDash has gone away and the warnings no longer show up on a dashboard with the same visibility. Today I started off wanting to look at some other things but realized that there are too many compiler warnings to notice new ones I might introduce.

I started out porting another plugin over to the new charts dialog I added, created a [pull request][prcharts], and then moved on to figuring out the Open Babel plugin. That one uses `QRegExp` in quite a few places, so after initially looking at moving it over wholesale to the Qt 6 classes I decided to use the `Core5Compat` library for now. As you can see in the [pull request][propenbabel] it still needed a fair bit of porting. I got it working locally, and confirmed it was good with Qt 5.15 and Qt 6.5 before pushing it.

I went down the rabbit hole, I didn't get them all, but I am at 20 commits in a branch at this point to get rid of many of the compiler warnings that have crept in over the last couple of years! Only changing 55 files, so not so bad, some warnings pointed to a few potential bugs along with simple housekeeping that should be taken care of. In the end once I pushed the [pull request][prwarnings] some of the automated analysis picked up other things that had been lurking due to only looking at changes.

This was instead of yard work, I swear I was going to go and do it and then it just started raining! Check the weather forecast or flip a coin - they got it wrong today...

[prcharts]: https://github.com/OpenChemistry/avogadrolibs/pull/1247
[propenbabel]: https://github.com/OpenChemistry/avogadrolibs/pull/1248
[prwarnings]: https://github.com/OpenChemistry/avogadrolibs/pull/1249
