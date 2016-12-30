---
layout: post
title: 'AMD64 Based PVR: Part 2 - Mostly Successful'
categories:
- FOSS
- Gentoo
- Hardware
- Linux
permalink: "/archives/70-AMD64-Based-PVR-Part-2-Mostly-Successful.html"
s9y_link: http://blog.cryos.net/archives/70-AMD64-Based-PVR-Part-2-Mostly-Successful.html
date: 2006-02-11 20:14:23.000000000 +00:00
---
Well I have been mostly successful I think with my MythTV project. Dabs still have me waiting around on the 300 GB hard drive and new case, so it is stuck on a temporary 40 GB hard drive and an old case. It is very quiet though. I finally got the two tuners working on my Hauppage PVR-500 MCE. I took out the tuner=57,57 and let it automatically detect the correct tuners! They now both work, and composite in works too. I tried to use svideo in though and that does not seem to work, although it could be a cable issue. I bought a SCART to svideo and two phono adaptor. I get nothing but a black screen from my Sky Digibox.<br />
<br />
I can't get anything out of the radio tuner either. I discovered why xawtv and tvtime made terrible test programs - they don't understand the MPEG2 output I get from the hardware encoders. MPlayer made a much better test program. So so far I have managed to get both tuners working, using the mce_usb2 driver form the latest lirc ebuilds I managed to get the remote control and infrared receiver working, although still no luck on the built in IR blaster. There are two IR blaster ports and one supplied IR blaster - anyone got any tips on that one at all?<br />
<br />
The DVD player is working great although I switched to xine for the DVD menu support. I tried using svideo output but all I could get was black and white no matter what I tried. So I switched back to composite output which works well. So it seems that svideo sucks over here and doesn't work, but composite works just fine. I still haven't quite figured out MythTV either - I need to tell it about the five analogue channels and my Sky Box which is on a sixth channel - I have the channels but need to program them into MythTV. Right now I am using ivtvctl and ivtv-tune until I figure MythTV out.<br />
<br />
So it wasn't the easiest thing in the world to set up, but it is working pretty well right now. Need to figure out how to record programs too, but the core functionality is working well. I am really busy with lots of other stuff so this little project has ended up on a bit of a back burner. I do still find Linux very empowering though, and certainly have no intention of moving back to Windows any time soon for a number of reasons despite the extra effort required to get some things done.
