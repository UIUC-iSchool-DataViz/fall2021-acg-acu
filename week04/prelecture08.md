
## bqplot

Our first engine, `bqplot`, is a Jupyter-based interactive plotting system.

It presents two principal interfaces:

 * `pyplot`-like interface, for making the transition from matplotlib easier
 * An object-oriented API for constructing interactive visualizations

We will be using the latter far more frequently than the former.

---

## bqplot

Now that we've learned a bit about widgets, we can start to dig into `bqplot`.
`bqplot` is based around traitlets and widget objects; every object you work
with will have traits and may be represented as a widget.

When we use `bqplot` we will be constructing `Figure` objects, which will
contain `marks` and `axes`.  To use these, we will build mark objects (`Bars`,
`Lines`, `Scatter`, `Map`, etc) and describe the relationship between points
using `Scale` objects.

We will be building out these objects and their relationships to develop
interactivity.

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

## Assignment 3

 * Using traitlets, widgets and bqplot, build a notebook that:
   1. Uses the UFO datasets
   2. Allows changing the x and y fields on a scatter plot from the UFO dataset
   3. Displays tooltips when hovering over individual items
 * Build a second widget that displays binned, aggregate values where you can change:
   1. The field to "bin"
   2. The method of aggregation (sum, mean, min, max, count)
   3. The number of bins

---

## Today: Let's Try Things

Today we are going to build comparisons with our (virtual) hands.

 * A Bit More Matplotlib
   * Patches and elements
   * "Projections"
   * Polar projections
 * Traitlets

---

## Next Week: Lab all day
