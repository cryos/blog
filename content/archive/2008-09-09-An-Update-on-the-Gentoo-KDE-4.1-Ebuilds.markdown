---
layout: post
title: An Update on the Gentoo KDE 4.1 Ebuilds
categories:
- Gentoo
- KDE
permalink: "/archives/190-An-Update-on-the-Gentoo-KDE-4.1-Ebuilds.html"
s9y_link: http://blog.cryos.net/archives/190-An-Update-on-the-Gentoo-KDE-4.1-Ebuilds.html
date: 2008-09-09 03:20:00.000000000 +00:00
---
<span><p>My <a href="http://blog.cryos.net/archives/189-KDE-4.1-Gentoo-Ebuilds.html">previous post</a> sparked off quite a few comments. I can see from some of the comments that the post was too long, some people really don't understand the <a href="http://www.pathname.com/fhs/pub/fhs-2.3.html">FHS</a> where it clearly states, "Large software packages <strong>must not</strong> use a direct subdirectory under the /usr hierarchy." We currently do, the FHS KDE install really is FHS compliant. Please not that is <strong>not</strong> the primary reason we would like to do this. It is however one of several benefits.</p>

<p>I thought I had made it quite clear that slotting of minor versions was not going to be removed. Jorge and I have been working hard on getting the KDE 4.1 ebuilds into shape, and after Jorge worked with Zac on a few ideas it appears that new portage behaviours to do with blocking effectively allows us to use the original multislot idea I implemented using a different implementation (avoids variable slots). Some of the changes could do with EAPI 2 but it looks like we can implement much of what we need now and impove things when EAPI 2 is available.</p>

<p>Thanks to those who commented on my post in a constructive fashion. Not sure how to respond to a few of you who just don't seem to have read my post (or the FHS). Just to say that we are working on it. Jorge, myself and several interested users have been doing what we can with the time we have available to get the ebuilds into shape. If you would like to take a look at what we are doing you can check out the kde-testing overlay using layman, otherwise we will be working on getting KDE 4.1 into the tree as soon as we can.</p></span>
