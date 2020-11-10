---
title: Basics of Scientific Visualization
layout: lecture
tags:
  - scientific
  - python
description: >-
  What makes scientific data "different"?
---

# Visualization Highlights

 * [How Migration is Changing Our World](https://www.bloomberg.com/graphics/2019-how-migration-is-changing-our-world/)
 * [15 Visualizations](https://blog.udacity.com/2015/01/15-data-visualizations-will-blow-mind.html), especially:
   * Shooting stars, satellites, workday, music timeline
 * [Citibike Data](https://twitter.com/CraigTaylorGIS/status/1191282070380789760)
 * [Opiod Overdoes](https://medium.com/@chaitupramod/redesigning-a-bad-graph-spaghetti-to-micromaps-374d68b5df6c)
 * [Letter Frequency](https://public.tableau.com/en-us/gallery/frequency-letters)

---

## Today

 1. Scientific Visualization
 2. Big-ish Data

---

## Scientific Visualization

What characterizes "scientific" visualization?

 * Spatial organization - distance metrics
 * Dimensionality reduction or mapping
 * Multiple overlapping quantities with implicit or explicit extent

---

## Scientific Visualization - Data Representations

<div class="multiCol">
<div class="col">
<div class="fig-container" data-style="height: 600px;" data-file="figures/blank_axes.html" data-markdown=true>
</div>
</div>
<div class="col" data-markdown=true>

Commonly, data will be represented in "scientific visualization" through one of a few mechanisms:

 * Discrete points
 * Volume-filling information
 * Meshed values

</div>
</div>

---

## Discrete Points: Data

<div class="multiCol">
<div class="col">
<div class="fig-container" data-style="height: 600px;" data-file="figures/scatter.html" data-markdown=true>
</div>
</div>
<div class="col" data-markdown=true>

 * Associated field values
 * May have extent
 * Values can be either
   * Locally defined
   * Integrated over neighbors
</div>
</div> 

---

## Discrete Points: Techniques


<div class="multiCol">
<div class="col">
<div class="fig-container" data-style="height: 600px;" data-file="figures/discrete_tech.html" data-markdown=true>
</div>
</div>
<div class="col" data-markdown=true>

 * Associated field values
 * May have extent
 * Values can be either
   * Locally defined
   * Integrated over neighbors
</div>
</div> 

---

## Discrete Points: Density Estimates

 * Searching
   * Quadtree
   * kD-tree
 * Integration
   * Kernels
   * Nearest-neighbor

---

## Volume-filling: Data

For this, we will be using Python to collaboratively explore what volume-filling data is.

Install yt and ipyvolume.

```
!pip install install cython sympy unyt pooch
```

```
!pip install git+https://github.com/yt-project/yt.git
```

---

## data for yt

We will acquire a bit of data.

```python
import yt
ds = yt.load_sample("IsolatedGalaxy")

ds.r[:].max("density", axis="z")

```

---

## Volume data: strategies

To analyze volume data, typically we conduct one or more of these operations:

 * Select data based on spatial or non-spatial criteria
 * Reduce the dimensionality of that data either along spatial or other axes
 * Aggregate data

This can include operations such as volume rendering, axial projection, histogramming/binning and resampling.

Let's try some of this out.

---

## Big-ish Data

How do we deal with data that is too large to fit into memory?

 * Can we cycle our operations?
 * Can we use tools to cycle operations?

---

## Operations

Some operations we can manually cycle through, storing only reductions in
memory rather than the full dataset.

Clear candidates:

 * Mean
 * Extrema
 * Histograms and "binning"

Is this the same as incremental updates to a dataset?

(What about the median?)

