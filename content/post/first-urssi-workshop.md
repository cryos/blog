+++
description = ""
categories = ["academia"]
tags = ["open-science"]
images = ["images/201804-urssi-careers.jpg"]
banner = "images/201804-urssi-careers.jpg"
date = "2018-04-15T10:56:13-04:00"
title = "First URSSI Workshop"
menu = ""

+++

Earlier this week I attended the first [URSSI][urssi] workshop, held at UC Berkeley. URSSI stands for the US Research Software Sustainability Institute, and right now is in the formation phase. Much of the week was spent discussing what this institute could be, and how such an institute might operate. For me this speaks to a core gap I observed in the importance, and career opportunities for researchers that engage in the development of software that is primarily used in research.

<!--more-->

The institute formation is already off to a fantastic start in my eyes, using a [git repository][urssi-repo] to discuss ideas, and coordinate the first workshop. The main website for the project is also using [Hugo][hugo] (I use it for my blog too), and you can fork [this repo][urssi-web], suggest changes and submit a pull request. There is a thread of openness and transparency to the way things are being conducted that I hope to see continue on into the final institute.

### Growing Importance of Software

There was a time when software was not a big thing in most mainstream science, nor in most people's lives. Lab notebooks were physical notebooks, with recorded values written down by hand, and even plotted on graph paper. This is no longer the case, the tools available to us in everyday life as well as science are becoming more sophisticated, capable of recording more, and requiring software to drive their operation. Even the experimental fields are now feeling this as sensors, data acquisition boards, and control equipment evolve the software must too.

### Common Roots

Another thing that strikes me, and it is something that I remember being drilled into me as an open source developer, is that science is built upon shared facts, knowledge, and peer review. Many of the founders of open source referenced the founding principles of modern science as indications that open source was indeed the right way to do things. Indeed the [Royal Society's][royal-society] motto was "nullius in verba", which roughly translated means to take nobody's word for it - trust, but verify. Another key feature of science is that people don't own/control facts, with new science building upon that which came before it.

### Open Principles

I think one of the core needs in science right now is to wrangle with the new reality that computer software is quickly becoming (if it has not already become) more important than mathematics in science. I spent many hours on derivations of important theorems, and on how to make new derivations. This skill is important in science, but in modern studies I posit the equivalent is the development of code to further research. Another issue is in bringing the field forward, and avoiding constant reinvention.

I did not study for many years to use a blackbox code, and be told by a group, company, entity, whatever that I should trust them, they know this stuff really well. The heart of scientific research is in learning new things, going places no one has gone before. That means that as software's importance increases we need to ensure that everyone has access to it with minimal restrictions. That means that software needs to be available to all, with the ability to modify it, and redistribute/publish those changes.

### Licenses, Process, Nurture

I would go further, and say publicly funded research should be using permissive, open source licenses that encourage reuse, further development, and shared ownership of community codes. One point that became clear to me recently is that researchers need to be educated on licensing too, and realize that you should avoid modifying existing licenses at all costs. Adding new clauses, or changing the language means that what you have is no longer an open source license, unless the [OSI][osi] approves your license. We already have a lot of licenses, inform any lawyers that get involved that we likely don't need more, and if we do they should go to the effort of working with with OSI to get it approved as an open source license.

Assuming code gets this far, and too often it does not, and you have a real, OSI-approved open source license there is still much to be done. What version control system are you going to use, where are you going to host it, what continuous integration methods will you employ, code review, automated builds, packaging, issue tracking, mailing list, forum. How will you bring on board new developers, encourage community contributions, ideally grow the project beyond a single grant, group, and institution. How will you structure the repository, will you tag releases, etc? These are all things that the URSSI might help with.

### Final Thoughts

From my undergraduate, postgraduate, postdoctoral and now professional career I have always been looking at how we can foster an ecosystem of open source code for scientific research. I still fully believe that if you publish papers without code and/or data used to arrive at those results you are basically just [advertising possible results, not disseminating scientific research][advertising]. This is one of the core issues that has led to the reproducibility crisis. There is a lot of powerful open source software developed by the wider community that can help once you have decided to follow this path, but even if everyone is on board this is tough right now.

The [Blue Obelisk][blue-obelisk] advocated for open source in chemistry, the [SSI][ssi] has been working in this area for a number of years in the UK, and have developed a new role in British academia - the research software engineer (RSE) role. There is also [WSSSPE][wssspe] that has organized a number of workshops to discuss making software more sustainable for science. If RSEs had existed when I was figuring out what I should do it is a path I might have followed, and one I am very pleased to see opening up.

[urssi]: http://urssi.us/
[urssi-repo]: https://github.com/si2-urssi/berkeley_workshop
[hugo]: https://gohugo.io/
[urssi-web]: https://github.com/si2-urssi/website
[royal-society]: https://royalsociety.org/about-us/history/
[osi]: https://opensource.org/
[advertising]: https://blog.okfn.org/2013/09/03/publishing-research-without-data-is-simply-advertising-not-science/
[blue-obelisk]: https://en.wikipedia.org/wiki/Blue_Obelisk
[ssi]: https://www.software.ac.uk/
[wssspe]: http://wssspe.researchcomputing.org.uk/
