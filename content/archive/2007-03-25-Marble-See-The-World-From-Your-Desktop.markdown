---
layout: post
title: 'Marble: See The World From Your Desktop'
categories:
- Gentoo
- KDE
- Linux
permalink: "/archives/132-Marble-See-The-World-From-Your-Desktop.html"
s9y_link: http://blog.cryos.net/archives/132-Marble-See-The-World-From-Your-Desktop.html
date: 2007-03-25 15:39:00.000000000 +00:00
---
<span><p>Yesterday and today I went along to an <a href="http://www.openstreetmap.org/">Open Street Map</a> event organised in <a href="http://wiki.openstreetmap.org/index.php/Sheffield">Sheffield</a>. When I get time I will talk about that more in another post. As I got back yesterday afternoon I got talking to <a href="http://cniehaus.livejournal.com/">Carsten</a> about it on IRC and he introduced me to <a href="http://www.kdedevelopers.org/blog/551">Torsten Rahn</a> who developed <a href="http://www.kde-apps.org/content/show.php/Marble+-+Desktop+Globe?content=55105">Marble</a>.</p>

<p>I have already been testing out some of the stuff in KDE trunk but had not yet had chance to try out Marble. It is still at an early stage of development but is already very nice to use. I have added <a href="http://packages.gentoo.org/packages/?category=sci-geosciences;name=marble">Marble 0.3</a> to portage as it can be built using just Qt 4. It is a great 3D globe that doesn't use OpenGL and so actually works very well on my laptop that doesn't have 3D accelerated drivers.</p>

<img src="http://blog.cryos.net/uploads/MarbleScreenshot.png" width="789" height="620" alt="Marble in action with Gentoo developers" />

<p>As <a href="http://www.kix.in/">Anant Narayanan</a> had already done a lot of work coordinating the update of Gentoo developer locations I asked him about getting a list in KML format which Marble supports. Above is a screen shot showing most of Europe and the developers located there. You can search for your favourite developer and even measure the distance between them.</p>

<p>It is only keyworded ~amd64 so far. If you are on another architecture you can always test it and ask your friendly architecture team to keyword it if it works well for you. Torsten has lots of stuff on his todo list for Marble. He will also be giving a talk on it at <a href="http://akademy.kde.org/">aKademy</a> this year. One of the things I am particularly interested in is Open Street Map support. I am also looking forward to tile downloading in the next release.</p></span>
