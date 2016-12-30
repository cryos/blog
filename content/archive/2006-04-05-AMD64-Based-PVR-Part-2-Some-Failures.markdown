---
layout: post
title: 'AMD64 Based PVR: Part 2 - Some Failures'
categories:
- FOSS
- Gentoo
- Hardware
- Linux
permalink: "/archives/79-AMD64-Based-PVR-Part-2-Some-Failures.html"
s9y_link: http://blog.cryos.net/archives/79-AMD64-Based-PVR-Part-2-Some-Failures.html
date: 2006-04-05 09:11:52.000000000 +00:00
---
I have been really busy recently and so haven't had as much time as I might have liked to work on my PVR. After spending a while working on it lastnight I thought I would write a little about some of my failures. On the whole the solution is working reasonably well, and some of these issues could be related to me using it in 64 bit mode...<br />
<br />
The first is the image quality. Whilst playing DVDs I have found that xine works best and has DVD menu support which in my opinion is essential. On the whole the picture is pretty good but in fast moving scenes where large amounts of the background are moving quite quickly the motion becomes noticeably blocky during the motion. This can be really irritating and is not a great advert for the box when friends come around as even a Â£20 DVD player doesn't seem to suffer from this.<br />
<br />
The second is the picture quality from the TV. I never managed to get the composite or svideo connections working - I only ever saw black. So I am using the aerial and the picture is very noticeably more blurry than the same picture just fed straight to the TV. I am guessing this is just the poorer quality of the aerial signal or a hardware limitation. Either way it is not great.<br />
<br />
It would also appear that MythTV may have a memory leak as after the client had been running for a few weeks the system was out of memory. It would seem this leak is pretty slow though and so I am not sure how best to track it. This system has 1 GB of RAM so may be that helps give it a lot more time. The final issue I have not gotten to the bottom of is freezing after watching the TV for a while through MythTV.<br />
<br />
All in all it is not a bad solution, but it is certainly not a plug in and go solution. I wish I had just got myself a cheap DVD player as I just don't have the spare time right now. Hopefully this post will be seen as an honest appraisal of how things are working right now with my MythTV box. Your mileage may well vary and you may have a lot more time to tinker. My wife isn't all that impressed and quite honestly I don't know that I am...
