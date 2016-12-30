---
layout: post
title: Using VTK's Image Regression Tests in Avogadro 2
categories:
- Avogadro
- Chemistry
- KDE
- Kitware
permalink: "/archives/266-Using-VTKs-Image-Regression-Tests-in-Avogadro-2.html"
s9y_link: http://blog.cryos.net/archives/266-Using-VTKs-Image-Regression-Tests-in-Avogadro-2.html
date: 2013-05-01 14:51:00.000000000 +00:00
---
<span>
<p>One of the really nice features of <a href="http://www.vtk.org/">VTK</a>'s testing framework is the use of image-based regression tests. These allow developers to write tests that result in a final image, which can be recorded and compared to known baseline images in order to verify that the OpenGL rendering code is rendering the same (or similar) image on all platforms. If this fails then <a href="http://www.cdash.org/">CDash</a> will display the image the test produced, the baseline image it was compared to and an image difference. Any project that performs rendering or visualization needs tests like these in addition to unit tests if they want to assure visualization code continues to function as expected across a range of platforms.</p>

<p>We recently extracted the relevant code from the VTK testing framework to <a href="http://review.source.kitware.com/#/t/2618/">perform image based regressions in Avogadro 2</a>, with the bulk of that code living in <a href="https://github.com/OpenChemistry/avogadrolibs/blob/master/utilities/vtktesting/imageregressiontest.h">utilities/vtktesting/imageregressiontest.h</a>. This is currently used in one of the tests, with plans to extend it to cover all major types of rendering, this can in seen in action in<a href="https://github.com/OpenChemistry/avogadrolibs/blob/master/tests/qtopengl/glwidgettest.cpp">tests/qtopengl/glwidgettest.cpp</a> with the important lines that take the snapshot/do the image comparison being:</p>

<div class="cpp geshi" style="text-align: left">&#160; <span style="color: #666666;">// Grab the frame buffer of the GLWidget and save it to a QImage.</span><br />&#160; QImage image <span style="color: #000080;">=</span> widget.<span style="color: #007788;">grabFrameBuffer</span><span style="color: #008000;">&#40;</span><span style="color: #0000ff;">false</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span><br />&#160; <span style="color: #666666;">// Set up the image regression test.</span><br />&#160; Avogadro<span style="color: #008080;">::</span><span style="color: #007788;">VtkTesting</span><span style="color: #008080;">::</span><span style="color: #007788;">ImageRegressionTest</span> test<span style="color: #008000;">&#40;</span>argc, argv<span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span><br />&#160; <span style="color: #666666;">// Do the image threshold test, printing output to the std::cout.</span><br />&#160; <span style="color: #0000ff;">return</span> test.<span style="color: #007788;">imageThresholdTest</span><span style="color: #008000;">&#40;</span>image, std<span style="color: #008080;">::</span><span style="color: #0000dd;">cout</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span></div>

<p>The CMake code that feeds in the command line arguments, and ensures the test runs correctly is in <a href="https://github.com/OpenChemistry/avogadrolibs/blob/master/tests/qtopengl/CMakeLists.txt">tests/qtopengl/CMakeLists.txt</a>, and largely involves passing in paths to the baseline directory, a temporary directory and the test name (using the standard CMake generated test driver).</p>

<div class="cmake geshi" style="text-align: left">&#160; <a href="http://www.cmake.org/cmake/help/cmake-2-8-docs.html#command:add_test"><span style="color: #1f3f81; font-style: bold;">add_test</span></a><span style="color: #197d8b;">(</span>NAME <span style="color: #912f11;">&quot;QtOpenGL-<span style="color: #b08000;">${test}</span>&quot;</span><br />&#160; &#160; <span style="color: #077807; font-sytle: italic;">COMMAND</span><br />&#160; &#160; &#160; AvogadroQtOpenGLTests <span style="color: #912f11;">&quot;<span style="color: #b08000;">${testname}</span>test&quot;</span><br />&#160; &#160; &#160; <span style="color: #912f11;">&quot;--baseline&quot;</span> <span style="color: #912f11;">&quot;<span style="color: #b08000;">${AVOGADRO_DATA_ROOT}</span>/baselines/avogadro/qtopengl&quot;</span><br />&#160; &#160; &#160; <span style="color: #912f11;">&quot;--temporary&quot;</span> <span style="color: #912f11;">&quot;<span style="color: #b08000;">${PROJECT_BINARY_DIR}</span>/Testing/Temporary&quot;</span><span style="color: #197d8b;">)</span></div>

<center><img src="http://blog.cryos.net/uploads/glwidgettest-valid.png" width="250" height="250" alt="Valid baseline image" /></center>

<p>The above is the baseline image, that is stored in a known location and compared with the image produced by the test (shown below).</p>

<center><img src="http://blog.cryos.net/uploads/glwidgettest-test.png" width="250" height="250" alt="Test image image produced" /></center>

<p>If the images don't match a difference image is produced and uploaded (shown below). In this case you can see that an extra sphere was rendered, and this can clearly be seen in the difference image. There is also a numerical difference returned by the test, which is a measure of how much the images differ. The tolerance can be tweaked depending on the test to allow some minor pixel differences, although care must be taken not to raise the number too high.</p>

<center><img src="http://blog.cryos.net/uploads/glwidgettest-diff.png" width="250" height="250" alt="Image difference from test to valid" /></center>

<p>We have not implemented it in Avogadro 2 yet, but VTK can use multiple baselines and returns the smallest image difference. This allows for OS/GPU specific baselines to be uploaded where necessary as an alternative to increasing the tolerance. Using special tags returned by the tests in the standard output will prompt the ctest command to upload the image files when necessary (in the case the baseline image cannot be found, or the image comparison fails).</p>
</span>
