+++
categories = ["general", "avogadro"]
tags = ["development"]
images = ["images/avogadro-vtk-charts.png"]
banner = "images/avogadro-vtk-charts.png"
date = "2023-04-12T15:40:00-04:00"
title = "Avogadro, VTK Charts and Parenting"
menu = ""
description = "Some updates on Avogadro using VTK's charts and parenting windows correctly"

+++

So, day four, I now don't want to end my blogging streak but it will surely come to and end soon. This is not my random tips on parenting of children, although I do try do do that as well as I can, it is more the Qt parenting. In Qt all QObject derived classes, including the widgets typically used in graphical user interfaces like Avogadro, have a concept of a parent and its children. It gets a little macabre as Qt parents will destroy their children before destroying themselves - programmers, what can I say?!? The charts in VTK were one of my first big projects upon joining Kitware many years ago now.

Mixing Ownership Models
-----------------------

As I jokingly said above Qt has a singular parent to one or more child objects ownership model for the QObject derived classes. The VTK classes employ reference counting where any vtkObject derived class (most of them) have a reference count internally, so the VTK ownership can be quite a bit more complex than Qt with a potential many-to-many relationship. Bringing VTK classes into Qt can be a little confusing due to these two different ownership models and how they behave. Qt classes can also be allocated on the stack whereas this is not possible in VTK - they are always allocated on the heap.

Both libraries employ their own smart pointers, both of which diverge from those found in the broader C++ standard libraries. I should dig out the thread(s) but while at Kitware I campaigned for a third smart pointer that would allow for simpler allocation of VTK classes in the case where strong ownership was preferred, after much debate the name vtkNew was adopted and I got it into VTK. The cool thing it does is let you largely treat VTK like it will allocate on the stack, deleting the object it points to when it goes out of scope. The confusing thing is that you can then increase the reference count by assigning it to a smart pointer or other thing to keep it around.

Back to Qt and Parenting
------------------------

As all good programmers do, if things seem confusing I just add another layer of abstraction! I had been meaning to get to this for years, but I recently added a couple of classes to Avogadro's VTK support library. One for the chart widget, and another for a dialog to display the widget in. This lets you treat the VTK-based chart like any other Qt widget, and set the parenting correctly so that it will be destroyed as the application is closed. The charts can then be used in a fairly simple way, but it is still pretty rough right now.

The plot PDF plugin is the only one to benefit right now, and I will work through the other uses of the old VTK chart invocations until I can remove the old version. The major thing I want to accomplish is a very simple API for common plot types we want in Avogadro, with the correct parenting so that the dialog shows up in the right position and will close if you close the application. A small C++ snippet to demonstrate:
```cpp
m_chartDialog->setWindowTitle(windowName);
auto* chart = m_chartDialog->chartWidget();
chart->clearPlots();
chart->addPlot(xData, yData, VTK::color4ub{ 255, 0, 0, 255 });
chart->setXAxisTitle(xTitle);
chart->setYAxisTitle(yTitle);
m_chartDialog->show();
```

You would need to look at the whole thing to get all the context, but effectively m_chartDialog is the dialog in the plugin, you can get the chart widget from that, and I clear the plots to allow for reuse as this method always adds a plot, and then I add the x and y columns, with a color and add some titles to the axes. Then show the dialog that you can see in the screenshot above.

Simple Calling Code
-------------------

Under the covers these classes use VTK's smart pointers to manager the lifetime of the VTK classes. I want to add integration with the Qt data classes, color classes, etc so that it is natural, and retain support for std::vector columns. I would also like to look at adding a TrueType font to bundle for better text rendering. There is another plugin I wrote a few years ago to add volume rendering with a color opacity map editor that I want to standardize a little better. The intent here is very much to offer a way of constructing VTK charts without wandering too far from what is more familiar Qt API semantics for Avogadro developers.

Wrap Up
-------

This was one of the first things I looked at when getting back into the Avogadro code base. The chart classes are something I did a long time ago, they are not as pretty as some, but they are able to use OpenGL and VTK data structures to attain interactive speeds. Another thought as I sketch out the Qt API is to offer more than one backend so that I could drop in a higher quality non-interactive backend for publication. For now I think all we need in Avogadro is interactive plots and the addition of some methods of exporting the data if you want something prettier.
