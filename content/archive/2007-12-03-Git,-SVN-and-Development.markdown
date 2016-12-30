---
layout: post
title: Git, SVN and Development
categories:
- GSoC
- KDE
- Linux
permalink: "/archives/167-Git,-SVN-and-Development.html"
s9y_link: http://blog.cryos.net/archives/167-Git,-SVN-and-Development.html
date: 2007-12-03 01:42:57.000000000 +00:00
---
<span><p>It seems I have read quite a few posts in the last half a year or so on the virtues on decentralised version control and how good git it. Before my laptop died I had installed git and was using it for development. Unfortunately that was pretty short lived due to the failure of my laptop. Now all of my development is taking place on Apple Mac machines using Leopard (I used Tiger for a while too).</p>

<p>Recently I built git from source on the laptop I am using and checked out the full <a href="http://avogadro.sourceforge.net/">Avogadro</a> subversion repository using the following commands.</p>

<p><tt>git svn init -t tags -b branches -T trunk https://avogadro.svn.sourceforge.net/svnroot/avogadro<br />
git svn fetch</tt></p>

<p>Then I went and grabbed a coffee while it imported over 800 commits which is pretty small compared to many of the other repositories I have heard about being imported. It didn't take too long, but I would happily make my git repository available should anyone want a copy.</p>

<p>I have found git to be very fast which is absolutely great. There are some things which I have found a little confusing while getting to grips with git and its interaction with the subversion repository.</p>

<p>For my day to day work I need very few commands. <tt>git svn rebase</tt> synchronises with the subversion repository. I really like this way of updating too as it displays the diffs for the commits and the log messages. <tt>git commit -a</tt> commits all local changes to the local repository. <tt>git status</tt> shows the current status of the repository, <tt>git show</tt> shows local changes already committed and <tt>git svn dcommit</tt> pushes my local changes to the subversion repository.</p>

<p>It is this last feature I think I like the most. I can queue up multiple change sets which might actually break Avogadro, giving nice bite size commits as I make progress, but only committing them once I am done and everything is working (at least reasonably well). Then there is the potential for doing this when off line which is also great.</p>

<p>One of the most confusing things I found was how to nuke local changes if I didn't want to keep them. Deleting the file and updating doesn't work as it does with subversion. Also revert didn't do what I was after. I finally found <tt>git checkout</tt> which was not what I was expecting. Issuing the command with no arguments resets the repository to the last committed state. Adding filenames as arguments reverts just those files.</p>

<p>Another one I haven't found the answer to is files reappearing that we long since deleted. The avogadro.pro file is the main one left but a set of directories also reappeared. They are not there when checking out using just subversion. If anyone has the answer I would love to know. If I <tt>git rm</tt> the file the commit to subversion does nothing and it loops round.</p>

<p>Other than that I am really happy with git. It can be a little too easy to use the wrong commands and wipe out changes so I am moving quite gingerly at times but I think it is well worth the trade off. A few guides such as <a href="http://utsl.gen.nz/talks/git-svn/intro.html">this one</a>, <a href="http://cheat.errtheblog.com/s/git/">this one</a> and of course <a href="http://www.kernel.org/pub/software/scm/git/docs/">this</a> have helped me along the way.</p>

<p><strong>UPDATE:</strong> Just to note that I was using the git 1.5.3 release compiled from source.</p></span>
