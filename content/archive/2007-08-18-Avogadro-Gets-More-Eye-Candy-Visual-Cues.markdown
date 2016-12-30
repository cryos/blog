---
layout: post
title: Avogadro Gets More Eye Candy (Visual Cues)
categories:
- GSoC
- KDE
- Linux
permalink: "/archives/153-Avogadro-Gets-More-Eye-Candy-Visual-Cues.html"
s9y_link: http://blog.cryos.net/archives/153-Avogadro-Gets-More-Eye-Candy-Visual-Cues.html
date: 2007-08-18 14:27:42.000000000 +00:00
---
<span><p>During my trip to Paris Benoit and I discussed our ideas for adding some nice eye candy to Avogadro that would give better visual cues as to what exactly the tool was doing. In the case of the navigation tool each mouse button triggers a movement around the atom in a different sense, i.e. the left mouse initiates rotation, the middle initiates zooming/tilting and the right initiates translation. We had considered how best to convey this to the user without them needing to read the manual as most of us avoid doing that!</p>

<center><img src="http://blog.cryos.net/uploads/avo20070818.png" width="446" height="502" alt="Avogadro rotation" title="Avogadro rotation" /></center>

<p>The screen shot above shows the visual cue we worked on for atom centric rotation. Benoit and I worked on the initial code in the Versailles gardens and I finished it off when I got back. I really like this one which shows rotation about the x and y axes. As you rotate about the atom the arrows rotate around too allowing you to quickly see how much you have rotated the view by. I have been thinking about the usefulness of adding a text display of x and y rotation to the tool too.</p>

<center><img src="http://blog.cryos.net/uploads/avo20070818a.png" width="446" height="502" alt="Avogadro translation" title="Avogadro translation" /></center>

<p>This screen shot shows the visual cue for atom centric translation. This cue isn't quite as dynamic as the rotation one but I think it conveys very quickly what the tool is doing. It also moves around the atom surface with perspective and that looks quite nice. We have planned one for zooming and tilting but I haven't had chance to implement that yet.</p>

<center><img src="http://blog.cryos.net/uploads/avo20070818b.png" width="446" height="502" alt="Avogadro angle measurement" title="Avogadro angle measurement" /></center>

<p>Today I added another visual cue to our click measure tool too - showing the angle which is being measured by the tool. Much credit goes to the guys who worked on the bond centric manipulation tool who added the code to the painter for drawing shaded sectors. I took the opportunity to add units to the displayed measurements too as they really should be displayed.</p>

<p>I do have more plans for eye candy and will try to highlight them as they are implemented. I would love to know if people think that these additions are useful. I think it makes the tools far more intuitive and so reduces the learning curve.</p></span>
