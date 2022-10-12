+++
author = "Sean Westgate"
title = "Datashader"
date = "2022-09-09"
draft = true
description = "Visualising Big Data using Datashader"
tags = [
    "shortcodes",
    "privacy",
]
+++
I love data visualisation. Probably no surprise as my previous company was all about bringing pretty pictures to stages and screens on events. But those are mostly *canned* - meaning videos that have been created and now need mapping onto screens and projectors. Visualising data has a whole new dimension as it contains meaning that can be discovered and serves for new insights rather than simply making a point.

There are a ton of awesome data visualisation packages out there, but most require you to massage the data into a particular way to be able to look at it. This especially goes for larger data sets. So I was interested in finding a way to look at large datasets of raw data. Why? Well, using statistics like mean, min, max is all very useful, but how about just looking at one million datapoints and seeing outliers and the general shape of their value distribution? Can't be done? Oh yes, it can - thanks for Datashader.




{{< img src="/images/datashader.png" title="Shaded Data">}}






## Why Datashader?

**Accurately render even the largest data**

New to Datashader? Check out this [quick video introduction to what it does and how it works](https://youtu.be/U6dyIRolIhI)!

{{< youtube U6dyIRolIhI >}}



Datashader is a graphics pipeline system for creating meaningful representations of large datasets quickly and flexibly. Datashader breaks the creation of images into a series of explicit steps that allow computations to be done on intermediate representations. This approach allows accurate and effective visualizations to be produced automatically without trial-and-error parameter tuning, and also makes it simple for data scientists to focus on particular data and relationships of interest in a principled way.

The computation-intensive steps in this process are written in ordinary Python but transparently compiled to machine code using [Numba](https://numba.pydata.org)  and flexibly distributed across CPU cores and processors using [Dask](https://dask.pydata.org) or GPUs using [CUDA](https://github.com/rapidsai/cudf). This approach provides a highly optimized rendering pipeline that makes it practical to work with extremely large datasets even on standard hardware, while exploiting distributed and GPU systems when available.

```
import datashader as ds, pandas as pd, colorcet
df  = pd.read_csv('census.csv')
cvs = ds.Canvas(plot_width=850, plot_height=500)
agg = cvs.points(df, 'longitude', 'latitude')
img = ds.tf.shade(agg, cmap=colorcet.fire, how='log')
```



This code reads a data file into a Pandas dataframe `df`, and then projects the fields `longitude` and `latitude` onto the x and y dimensions of an 850x500 grid, aggregating it by  count. The results are rendered into an image where the minimum count  will be plotted in black, the maximum in white, and with brighter colors ranging logarithmically in between.

With code just like the above, you can plot 300 million points of data (one per person in the USA) from the 2010 census without any parameter tuning:


{{< figure src="/images/image-20220909112054317.png" title="datashader in action " >}}

## Installation

Please follow the instructions on [Getting Started](https://datashader.org/getting_started) if you want to reproduce the specific examples on this website, or follow the instructions at [HoloViz.org](https://holoviz.org) if you want to try out Datashader together with related plotting tools.



## Other resources

You can see Datashader in action in the [2019 HoloViz SciPy tutorial](https://www.youtube.com/watch?v=7deGS4IPAQ0) (3 hours!), listen to the [Open Source Directions](https://www.youtube.com/watch?v=6m3CFbKmK_c) episode from July 2019, or see how it is used in many of the projects at [examples.pyviz.org](https://examples.pyviz.org).

Some of the original ideas for Datashader were developed under the name Abstract Rendering, which is described in a [2014 SPIE VDA paper](http://spie.org/Publications/Proceedings/Paper/10.1117/12.2041200).

The source code for datashader is maintained on [Github](https://github.com/holoviz/datashader), and is documented using the API link on this page.

We recommend the Getting Started Guide to learn the basic concepts and start using Datashader as quickly as possible.

The User Guide covers specific topics in more detail.

The API is the definitive guide to each part of Datashader, but the same information is available more conveniently via the `help()` command as needed when using each component.

Please feel free to report [issues](https://github.com/holoviz/datashader/issues) or [contribute code](https://help.github.com/articles/about-pull-requests). You are also welcome to chat with the developers on [gitter](https://gitter.im/pyviz/pyviz), but please use the official channels for reporting issues or making feature requests so that they are captured appropriately.