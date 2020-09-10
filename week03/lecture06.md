---
title: Colors and Colormapping
layout: lecture
tags:
  - scaling
  - colors
  - colormaps
description: >-
  How do colors work?  What are the different ways we can map colors to values?  What should we keep in mind when doing this?
---

## Today's Topics

 * What is color?
 * Visual encoding
 * Data transformation

---

<!-- .slide: data-background-image="https://upload.wikimedia.org/wikipedia/commons/e/e8/1414_Rods_and_Cones.jpg" data-background-size="auto 75%" data-background-position="right 30% bottom 50%"-->

## How Do Colors Work?

<div class="left" data-markdown=true>

Rods (low-light) and cones (color) mediate vision. Humans have about 20 times
as many rods (120 million) as cones (6 million).

Roughly speaking, cones see in the colors red, green and blue.

By OpenStax College [CC BY 3.0](http://creativecommons.org/licenses/by/3.0),
via Wikimedia Commons

</div>

---

## Let's Try It

http://enchroma.com/test/instructions/

---

## Color Matching Function

<!-- .slide: data-background-image="images/cmf.png" data-background-size="auto 75%" -->

---

## Responsivity Function

<!-- .slide: data-background-image="images/resp.png" data-background-size="auto 75%" -->

---

## "Naming" Colors

 * RGB triplets, often expressed in hexadecimel ("#00FFAA", etc)
 * Color spaces 
   * HSV (Hue, saturation, value)
   * [CIELAB](https://en.wikipedia.org/wiki/CIELAB_color_space)
   * sRGB, Adobe sRGB
 * List of colors by name
   * [Web](https://www.w3schools.com/colors/colors_names.asp)
   * [matplotlib](https://matplotlib.org/2.0.2/examples/color/named_colors.html)

---

## Color Palettes

 * Colorbrewer Categories
   * Sequential
   * Diverging
   * Qualitative
 * Resources:
  * colorbrewer.org
  * palettable (package)

---

## Sequential Colormaps

![blues discrete colormap](images/blues_discrete.png)

![blues continuous colormap](images/blues_continuous.png)

---

## Diverging Colormaps

![spectral discrete colormap](images/spectral_discrete.png)

![spectral continuous colormap](images/spectral_continuous.png)

---

## Qualitative Colormaps

![discrete set1 of colors](images/set1_discrete.png)

![continuous set1 of colors](images/set1_continuous.png)

(See?  Works better as discrete!)

---

## It's full of colors

https://commons.wikimedia.org/wiki/File:16777216colors.png

---

## HSV Wheel

https://commons.wikimedia.org/wiki/File:HSV_color_solid_cylinder.png

By HSV_color_solid_cylinder.png: SharkD derivative work: SharkD Talk [CC BY-SA 3.0
(http://creativecommons.org/licenses/by-sa/3.0) or GFDL
(http://www.gnu.org/copyleft/fdl.html)], via Wikimedia Commons

---

## Palette Mapping

![](images/set1_discrete.png)

Assign each value to a specific color or element.

---

## Color Mapping

$f(v) \rightarrow (R, G, B)$

We can also re-map:

$f(v') \rightarrow (R, G, B)$

$v' = f(v)$

For instance, with logs or squares.

---

## Color Mapping: Linear Mapping

We map from a range of values to (0, 1):

$ v' = (v - v_0)/(v_1 - v_0) $

---

## Colormaps: `gist_stern`

<!-- .slide: data-background-image="images/gist_stern_colors.png" data-background-size="auto 75%" -->

---

## Colormaps: `gist_stern`

<!-- .slide: data-background-image="images/gist_stern_3d.png" data-background-size="auto 75%" -->

---

## Colormaps: `gray`

<!-- .slide: data-background-image="images/gray_colors.png" data-background-size="auto 75%" -->

---

## Colormaps: `gray`

<!-- .slide: data-background-image="images/gray_3d.png" data-background-size="auto 75%" -->

---

## Colormaps: `jet`

<!-- .slide: data-background-image="images/jet_colors.png" data-background-size="auto 75%" -->

---

## Colormaps: `jet`

<!-- .slide: data-background-image="images/jet_3d.png" data-background-size="auto 75%" -->

---

## Colormaps: `magma`

<!-- .slide: data-background-image="images/magma_colors.png" data-background-size="auto 75%" -->

---

## Colormaps: `magma`

<!-- .slide: data-background-image="images/magma_3d.png" data-background-size="auto 75%" -->

---

## Colormaps: `viridis`

<!-- .slide: data-background-image="images/viridis_colors.png" data-background-size="auto 75%" -->

---

## Colormaps: `viridis`

<!-- .slide: data-background-image="images/viridis_3d.png" data-background-size="auto 75%" -->

---

## Image Coloring

<div class="fig-container" data-style="height: 600px;" data-file="figures/example_coloring_image.html" data-markdown=true>
</div>

---

## Colormapping Images

<div class="fig-container" data-style="height: 640px;" data-file="figures/apply_colormap.html" data-markdown=true>
</div>

---

## Colormaps: Loading Data

Today we will explore images and colors, and how our choice of colormaps
affects our perception of them.

You will need to load data into your notebook, which you can do using these
commands:

```
import numpy as np
import h5py

fn1 = "/home/shared/sp18-is590dv/data/michigan_lld/michigan_lld.flt"
michigan = np.fromfile(fn1, dtype='f4').reshape((5365, 4201))

fn2 = "/home/shared/sp18-is590dv/data/single_dicom.h5"
with h5py.File(fn2) as f:
    scan = f["/scan"][:]
```

---

## Colormaps: Prep Work

We will now utilize the `plt.imshow` command to show these images, and discuss
how to modify the transformation of the data beforehand.

---

## Colormaps

With the Michigan data and the scan data, evaluate:

 * How to choose a colormap
 * What are some good "bounds" for that colormap
 * How do we set our transform?

---

## Assignment 2

Using matplotlib, construct a visualization of the Illinois Building Inventory
that communicates the following information:

 * Relationship between the year acquired and the year constructed
 * Total square footage as a function of congressional district
 * Average square footage per floor as a function of congressional district
 * Square footage for the five most common departments as a function of year

Each component will be worth 5 points and *must* be a completely communicative
visualization -- including labels and a one paragraph writeup of successes and
shortcomings in your approach.  Submit a notebook to Moodle.  All source code
must be in these files.
