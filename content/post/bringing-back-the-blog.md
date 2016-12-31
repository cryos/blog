+++
date = "2016-12-30T17:19:58-05:00"
title = "Bringing Back the Blog"
description = "Bringing the blog back after a long break, most of the old posts are in the archives, but I am starting fresh with Hugo and Markdown"
draft = false
categories = ["general"]
banner = "images/snow-trees-winter-2016.jpg"
images = ["images/snow-trees-winter-2016.jpg"]
+++


So I got distracted with life, and continued writing in several other places, including my [company blog][kwblog], [opensource.com][osdc], and a few other spots. I also got tired of maintaining my blog on virtual machines with the typical LAMP stack, but I did get interested in using static site generators. I am giving [HUGO][hugo] a try, and I made an attempt to migrate my old posts over from [Serendipity][s9y] via [Jekyll][jekyll] in case they are still of interest. The world has changed a lot since I started blogging in 2004, and quite a bit since I last posted to a personal blog!

I always hated having to log on to a web site, and edit my post there, and when it was ready post it. As I use Git and Markdown in so much of my other work this feels far more natural. I am hoping to use this for more of the unfiltered me, with random thoughts, and no editor to fix up my grammar/spelling. As I develop my workflow I hope that it reduces the time to prepare a post, and enables me to post more often on my schedule. If any of you have tips you would like to share, or thoughts on how things look then please do get in touch.

I surveyed quite a few different generators before settling on this one, but I liked the templating, speed, and the opportunity to possibly learn a little Go if I need to propose any changes. The migration of my old posts still seems a little lame, so I am going to see if I can improve that a little. I also want to find a better theme at some point, but I think the minimalistic one will work for now. At least I know I can try out different things offline, and see the same thing reflected once I push it.

I will probably just try to get a post out most weeks with stuff I am working on, open source, open science, rants, programming, chemistry, visualization, and whatever else comes to mind. I might even sneak in a few posts on my new motorcycle, or hopefully some photos as I am traveling around. Here is a little code to take the syntax highlighting for a spin...

{{< highlight cpp >}}
    auto x = 5;
    for (auto i = 0; i < 5; ++i)
      cout << "Iteration : " << i << " of " << x << endl;
{{< /highlight >}}

Now to see if I can publish this somewhere publicly, make SSL work, and all that other good stuff.

[kwblog]: https://blog.kitware.com/
[osdc]: https://opensource.com/users/mhanwell
[hugo]: https://gohugo.io/
[s9y]: https://s9y.org
[jekyll]: http://jekyllrb.com/
