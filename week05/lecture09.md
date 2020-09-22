---
title: Beginning Interactivity
layout: lecture
tags:
  - interactivity
  - concepts
  - bqplot
description: >-
  The foundations of interactivity, and how we can think about it and how we use it.
---

## Warm-Up Activity

1. What is the visualization trying to show?
1. What are its methods?
1. What are the strengths / weaknesses?


 * https://www.vox.com/policy-and-politics/2018/9/28/17914308/kavanaugh-ford-question-dodge-hearing-chart

---

## Comparison

 * Among Items
   * One Variable, Few Categories: Column, or  collection of bars
   * Two Variables: Variable Width Column Chart
   * Many variables: Embedded table or charts
 * Changing Over Time
   * Many Periods, non-cyclical: Line chart
   * Few Periods: Column or Line (depending on number of categories)

---

## Pandas

 * [pandas.pydata.org](http://pandas.pydata.org/)
 * Support for indexing, multi-indexing
 * Data structures
   * Series
   * DataFrame
   * Panel
 * Groupby, select, aggregation features
 * IO features
   * Reading/writing CSV, HDF5
   * Loading data from remote sources

---


# Interactivity

 * Interactivity -- brief review of terminology
 * Tools and frameworks
    * ipywidgets
    * bqplot
 * Web Viz
    * (Sort of) How the web works
    * (Very, very) Basic javascript
    * vega-lite

---

## Status Update: Concepts

 * Basic Visualizations
   * Plot components
   * Aggregation (binning, histograming)
 * Basic interactivity
   * Traitlets
   * Reactivity / data-binding

---

## Status Update: Tools

 * Python
   * matplotlib -- introduced
   * bqplot -- introduced
 * Javascript
   * vega-lite -- introducing next time

---

## Status Update: What's Left

 * Dynamic data (dashboarding)
 * Interactivity
 * Plot types
   * Heat maps / chloropleths
   * Geospatial data
   * Time-series and multi-series
   * etc
 * Advanced utilization of tools

---

## Interactivity

This week, we'll talk about some basics principles of interactivity in
visualization, and you will get a whirlwind introduction to some interactive
visualization libraries in python.

What do you think of when you think of interactive visualizations?

---

<iframe width="1024" height="576"
src="https://www.youtube.com/embed/B7XoW2qiFUA" frameborder="0"
allow="autoplay; encrypted-media" allowfullscreen></iframe>

---

## Interactivity: Parameters

<!-- .slide: data-background-image="images/brushlink_01.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

 * Point characteristics
 * Axis limits/bounds
 * Transform/scale

---

## Interactivity: Parameters

<!-- .slide: data-background-image="images/brushlink_01.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

 * Click-and-drag
 * Rectangle zoom
 * Adjustment

---

## Interactivity: Linking & Brushing

<!-- .slide: data-background-image="images/brushlink_02.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

---

## Interactivity: Linking & Brushing

<!-- .slide: data-background-image="images/brushlink_02.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

`filter( variable2 > variable1 )`

---

## Interactivity: Linking & Brushing

<!-- .slide: data-background-image="images/brushlink_03.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

`filter( variable2 > variable1 )`

---

## Interactivity: Linking & Brushing

<!-- .slide: data-background-image="images/brushlink_04.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

`filter( variable2 > variable1 )`

---

## Interactivity: Linking & Brushing

<!-- .slide: data-background-image="images/brushlink_05.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

---

## Interactivity: Linking & Brushing

<!-- .slide: data-background-image="images/brushlink_06.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

---

## Interactivity: Linking & Brushing

<!-- .slide: data-background-image="images/brushlink_07.svg" data-background-size="80% auto" data-background-position="right 50% bottom 50%" -->

---

## Implementing This

Two main approaches to the selection process:

 * Concurrent filtering
 * Index-based selection

What are the pros and cons of each?

What are methods of showing "linked" and "brushed" data if you have:

 * Scatter plot
 * Histogram
 * Field / image plot

---

## bqplot review

Construct `Figure` objects from `Mark` objects.  Relate points to each other with `Scale` objects, display them using `Mark` objects that are keyed to a set of `Scale` objects, and apply interaction using `ipywidgets` and `traitlets`.

I've received feedback about past lectures, and so we will be moving more slowly today.

---

## bqplot objects

 * A mark is some mechanism for displaying data.  For example, we might have
   data that has a set of x and y values, which we can use `Lines` to
   represent.
 * `Scale` objects describe relationships between visual attributes (position)
   and data values.
 * `Axis` objects are where data are placed.
 * `Figure` objects contain marks and axes, as well as interaction.

---

## bqplot: Very Simple

Our first example will be a simple lineplot.

```#python
import bqplot
import numpy as np

x = np.arange(100)
y = np.random.random(100) + 5

x_sc = bqplot.LinearScale()
y_sc = bqplot.LinearScale()
lines = bqplot.Lines(x = x, y = y, scales = {'x': x_sc, 'y': y_sc})
ax_x = bqplot.Axis(scale = x_sc, label = 'X value')
ax_y = bqplot.Axis(scale = y_sc, label = 'Y value', orientation = 'vertical')
fig = bqplot.Figure(marks = [lines], axes = [ax_x, ax_y])
display(fig)
```

---

## More bqplot

With bqplot, we construct a set of objects that are related:

 * Scales
 * Axes
 * Marks
 * Figures
 * Interactions

---

## Scales

We have dealt primarily with quantitative scales.  bqplot provides several
scales we can utilize:

 * `LogScale`
 * `LinearScale`
 * `DateScale`
 * `OrdinalScale`
 * `ColorScale`
 * A few more as well.

([documentation](https://bqplot.readthedocs.io/en/latest/_generate/bqplot.scales.Scale.html))

---

## Marks

bqplot has several different marks we can explore.  We will utilize a few more
today:

 * `HeatMap`
 * `GridHeatMap`
 * `Bars`
 * `Graph`

([documentation](https://bqplot.readthedocs.io/en/latest/_generate/bqplot.marks.Mark.html))

---

## bqplot interaction

As noted in the previous class, bqplot widgets are all based on ipywidgets.  This
means we use the same systems for describing the two.

We add an interaction to a given figure via the `interaction` keyword argument
to a figure.

---

## bqplot interactors

We will be able to use these different interaction methods:

 * `FastIntervalSelector`
 * `IndexSelector`
 * `BrushIntervalSelector` & `BrushSelector`
 * `MultiSelector` 
 * `LassoSelector`
 * `HandDraw`
 * `PanZoom`
 * `Tooltip`

---

## Datasets

This week we will use a dataset from
[FiveThirtyEight](https://fivethirtyeight.com/), specifically from their
[datasets repository](https://github.com/fivethirtyeight/data/).

Please take care to abide by their licensing terms (CC-BY 4.0).

Candidate datasets:

 * [librarians](https://github.com/fivethirtyeight/data/tree/master/librarians)
   (2014)
 * [bachelorette](https://github.com/fivethirtyeight/data/tree/master/bachelorette)
 * [comic-characters](https://github.com/fivethirtyeight/data/tree/master/comic-characters)
 * [bob-ross](https://github.com/fivethirtyeight/data/tree/master/bob-ross)
