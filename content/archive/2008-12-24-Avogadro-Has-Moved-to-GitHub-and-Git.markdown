---
layout: post
title: Avogadro Has Moved to GitHub and Git
categories:
- Avogadro
- Chemistry
- FOSS
- KDE
- Linux
permalink: "/archives/201-Avogadro-Has-Moved-to-GitHub-and-Git.html"
s9y_link: http://blog.cryos.net/archives/201-Avogadro-Has-Moved-to-GitHub-and-Git.html
date: 2008-12-24 05:15:00.000000000 +00:00
---
<span><p>After some discussion on IRC the <a href="http://avogadro.openmolecules.net/">Avogadro Project</a> has moved its version control over to <a href="http://github.com/">GitHub</a>. Our new repository <a href="http://github.com/cryos/avogadro/">can be found here</a>. Most of us are old Subversion users, and a few of us started out with CVS. I think we are still getting our head around the workflow but feel it is worth the effort for all the advantages the move will bring.</p>

<p>There are some great visualisations from GitHub. I have always loved the speed of <a href="http://git.or.cz/">Git</a> when compared to other version control I have used. It is also great for adding in bigger changes and not having to halt development in other areas for fear of merge issues. We shall see over the coming months how positive the move was, but I am confident it will be. I have been using Git locally through git svn for over a year now I think.</p>

<p>For those who might wonder, the conversion was not totally automatic. The branches and tags git-svn leaves you with are not Git branches and tags. It basically required me to manually create the branches and tags. So for our repository I ran the following,</p>
<pre>mkdir avogadro-git
cd avogadro-git
git svn init https://avogadro.svn.sourceforge.net/svnroot/avogadro --stdlayout
git config svn.authorsfile ../avogadro/authors.txt
git svn fetch</pre>
<p>At that point I went and grabbed a coffee, took care of the dog...</p>
<pre>git remote add origin git@github.com:cryos/avogadro.git
git push origin master</pre>
<p>This got us most of the way there but lacked all of our tags and branches. I found that none of the push options worked as the tags and branches needed to be made into full Git entities first.</p>
<pre>git branch -a (show all the branches)
git branch 0.8 0.8
git branch 0.6 0.6
git branch primitive primitive
git tag -f 0.6.0 tags/0.6.0
git tag -f 0.6.1 tags/0.6.1
git push --all origin
git push --tags origin</pre>
<p>After all that we have our tags as Git tags and our branches as Git branches. You can browse them and clone the repository. A few of us have been experimenting and everything looks good. Adding current developers as collaborators enables them to push directly to the repository. There are also some web interfaces that allow for pulling from forks.</p>

<p>So if all goes to plan now, there will be no more commits to our old Subversion repository. We have preserved all of our history and I made sure the author metadata was improved. Hopefully this will make our development process more streamlined. We appreciate any and all tips, <a href="http://github.com/guides/keeping-a-git-fork-in-sync-with-the-forked-repo">this looks like a good guide to keeping a fork in sync</a>, pushing and pulling where necessary.</p>

<p>Now back to coding - we want to get a new release out!</p></span><br />
<br />
