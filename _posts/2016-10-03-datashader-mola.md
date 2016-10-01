---
layout:     post
title:      "Handle millions of points in seconds"
subtitle:   
author:     mdamore
header-img:
category: Tools
tags: [reduction, data , Python]
slack_channel: tools
image:
---

Watching Scipy videos always brings interesting findings.
In the 2016 edition I found [this](https://www.youtube.com/watch?v=6m3CFbKmK_c) great introduction to [datashader](https://github.com/bokeh/datashader/) by Dr. James Bednar([@jamesabednar](https://twitter.com/jamesabednar)), part of the big [Continuum Analytics](https://www.continuum.io) contribution to the python environment.

At its core, datashader is a highly efficient library to reduce non-gridded data to 2D images using a variety of functions to calculate pixel value.
Look at the [documentation](http://datashader.readthedocs.io) and these amazing [notebooks](https://github.com/bokeh/datashader/tree/master/examples) for further details and examples. 

I adapted [^adapt] the `nyc_taxi.ipynb` notebook that uses ~6M unstructured datapoints to visualize an example planetary dataset.

[^adapt]: someone would define this as "copying", I would say "tinkering".

I cheat a little bit creating an unstructured dataset from MOLA projected images.

I downloaded the MOLA [meg016](http://pds-geosciences.wustl.edu/missions/mgs/megdr.html) (16 pixels per degree) data from the PDS and converted each file to csv with [^gdal] : 

[^gdal]: this needs GDAL installed, present in your PATH, working and all the stuff.

```sh
for i in $(ls *.md )
    do
    base=$( echo $i | cut -d. -f1)
    echo $base
    gdal_translate -of XYZ $i $base.xyz
done
```

They call it 'ASCII Gridded XYZ'. Loading all those data brings around 66M points in as tabular data.

Visualizing them could be challenging: honestly all the examples that James did (undersampling, oversampling and/or playing with opacity) are my daily life.

Datashader helps to generate 2D images with some predefined functions to calculate pixel values, like the mean of all data point mapped to a particular bin, the min/max/variance and so on.

I ran all the code on my old 13" Macbook mid 2012, 2.9GHz i7, 16GB of RAM.
That is not the brightest machine nowadays, nevertheless it achieved good performance. 
The funniest thing was that loading all the data with the super [pandas](http://pandas.pydata.org) library [^pandas] took _30 seconds_, when the reduction of **all the data** on a 800x400 grid with datashader took less then __6 seconds__.
I'm more than impressed!

[^pandas]: you are using pandas for tabular data, I hope.

Obviously, a more powerful machine achieves better results: on my desktop MacPro ( 32 Cores / 64 GB RAM ) it took and order of magnitude less.

Datashader works pretty well in combination with [Bokeh](http://bokeh.pydata.org), always from Continuum Analytics.
The last cell in the notebook below will produce an interactive plot with live data reduction every time the user pans or zooms.

The only downside I found was the limited set of available functions for the reduction, James opened an [issue](https://github.com/bokeh/datashader/issues/245) on github to discuss my proposal. 
I had in mind something more robust then the mean to handle the noisy dataset that we all know, like the median or density function related characteristics.
Sadly, it seems that the current implementation cannot easily accomplish this, mainly due to the extreme optimization and parallelization they use.
They agreed that it is interesting and maybe they will add an example for less-then-optimized functions in the future.

Here is the notebook (original [link](https://gist.github.com/kidpixo/c501eb874e1fc44b77067c5fa6606a71)): if you want to run it, please take care of the dependencies and that datashader isn't pip installable (yet).

{% gist kidpixo/c501eb874e1fc44b77067c5fa6606a71 %}
