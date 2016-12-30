---
layout: post
title: ePiX Updates - Easier File Reading
categories:
- Gentoo
- Linux
- PhD
permalink: "/archives/137-ePiX-Updates-Easier-File-Reading.html"
s9y_link: http://blog.cryos.net/archives/137-ePiX-Updates-Easier-File-Reading.html
date: 2007-04-08 09:39:00.000000000 +00:00
---
<span><p>In the past few weeks I have been doing lots of data analysis and graph plotting. I use some graphical tools such as <a href="http://plasma-gate.weizmann.ac.il/Grace/">Grace</a>, <a href="http://home.gna.org/veusz/">Veusz</a> and <a href="http://soft.proindependent.com/qtiplot.html">QtiPlot</a> but when doing lots of plots for a big document I wanted something a little more scriptable.</p>

<p><a href="http://mathcs.holycross.edu/~ahwang/current/ePiX.html">ePiX</a> seemed to fit this bill and when I contacted the author about a few problems I had getting it to work he was very responsive. He is a mathematician whereas I am a physicist and have to handle lots of data in general. So I found the data file reading quite fragile. It does however have some great advantages such as being able to write LaTeX equations right into the graphs and figures.</p>

<center><img src="http://blog.cryos.net/uploads/absorptionprofile.png" width="648" height="427" alt="Absorption profile plotted by ePiX" /></center>

<p>The image shown above shows a plot of the absorption profile of a gold nanoparticle suspension. In the recent ePiX 1.0.24 release I added a tokeniser to the file reading functions of the data_file class in order to make data file reading more robust and I was able to read all my data files in using a simple loop and plot them as shown.</p>

<p>I have also just finished a data pruning function for the same class, but I am not sure if there is a better way to implement it. It uses brute force right now to iterate through the data and erase unwanted points. It does work well but I am not sure if there is a better way to accomplish its goal using some of the STL algorithms. It does need to delete the whole row though.<p>

<pre>  void data_file::prune(double min, double max, unsigned int col)
  {
    // Erase rows where the data is outside of the specified range
    std::vector<std::vector<double>::iterator> iter(m_data.size());
    for (unsigned int i = 0; i < m_data.size(); i++)
      iter.at(i) = m_data.at(i).begin();

    while (iter.at(0) != m_data.at(0).end())
    {
      if ( *iter.at(col-1) < min || *iter.at(col-1) > max )
      {
        for (unsigned int j = 0; j < m_data.size(); j++)
          m_data.at(j).erase(iter.at(j));
      }
      else
      {
        for (unsigned int j = 0; j < m_data.size(); j++)
          iter.at(j)++;
      }
    }
  }</pre>

<p>This pretty much covers the extra bits I needed for data analysis. A nice legend function would be good as drawing legends isn't as automated as I might like. I would welcome any feedback on the prune function as I think this would make a good addition to ePiX.</p></span>
