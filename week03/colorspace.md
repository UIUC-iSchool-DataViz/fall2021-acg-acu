---
title: RGB Color Space
layout: assignment
description: 
---


The purpose of this assignment is to get you comfortable thinking in the RGB
color space. In class we made some histograms of the different RGB colors
present in the image of Stitch.  Pick 3 of your own images (from the web, from
your own photos) and create a visualization that shows how similar/different
these images are using these histogramming methods presented in class.

Note: it is possible that one or more of the images you use may not have an
"alpha" channel and will only have RGB triplets.  You will then have to modify
the code we used in class and take out any references to the "alpha" mask.

You are free to choose 3 images that look "similar" to you or very different
and describe how mapping them into color space (i.e. making histograms of their
color distributions like we did for Stitch in class) either confirms or negates
these differences or similarities.  (For example, let's say you choose a
painting of a beach and a photo of a beach their color spaces might look very
different although they are representations of similar objects). You may also
want to choose a set of images that you like and those you don't like to see if
there are any differences due to color choices.

The attached notebook & example image are an example of how to downsample your
image into its most frequent colors or a user-selected set of colors.  While
you do not have to necessarily use this for your visualization, you should
nevertheless take some time to look over the code and answer the following
prompt in a few sentences (3-5 sentences is fine): 

 > Both of the color re-mappings presented in this notebook are not perfect.
 > What are some issues you can think of in how color is rebinned from a full
 > color image into an image with less colors with the functions provided?

 The coding portion is worth 15 points, writeup 15 points of your code.  Your
 exploration of the rebinning code is worth 10 points.
