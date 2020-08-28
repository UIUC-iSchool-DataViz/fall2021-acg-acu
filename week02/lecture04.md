---
title: Data Manipulation and Distributions
layout: lecture
tags:
  - operations
  - distributions
  - scaling
description: >-
  What operations can we do on data, how can we represent and compute distributions, and how do we scale values in relation to each other?
---

## Doing Stuff with Data

Now that we understand a few ways that data can be stored, and
how we draw with it, let's do some things to it.

---

<div class="left" data-markdown="true">

![palette of operations](images/palette.svg)<!-- .element: style="height: 20em;" -->

</div>

<div class="right" style="font-size: 150%;">
<div style="height: 4.0em;"></div>
You have a palette of operations to apply.
</div>

---

## Filtering Operations

 * Relationships:
   * Equality, inequality
   * Quantitative value (less than, greater than)
   * Intersection, disjoint
 * Subsampling
   * Regular sampling
   * Randomized sampling
   * Nyquist frequency
 * Related data queries
   * Queries on other columns at fixed row location
   * External membership queries

|||||||||||||
|-|-|-|-|-|-|-|-|-|-|-|-|
|&nbsp;<!-- .element: class="table-hl" --> |&nbsp;<!-- .element: class="table-hl" --> |&nbsp;<!-- .element: class="table-hl" --> |&nbsp;<!-- .element: class="table-hl" --> |&nbsp;<!-- .element: class="table-hl" --> |&nbsp;<!-- .element: class="table-hl" --> |&nbsp;<!-- .element: class="table-hl" --> |&nbsp;<!-- .element: class="table-hl" --> |&nbsp;<!-- .element: class="table-hl" --> |&nbsp;<!-- .element: class="table-hl" --> |&nbsp;<!-- .element: class="table-hl" --> |&nbsp;<!-- .element: class="table-hl" -->|
|&nbsp;<!-- .element: class="table-hl" --> |&nbsp; |&nbsp; |&nbsp; |&nbsp;<!-- .element: class="table-hl" --> |&nbsp;<!-- .element: class="table-hl" --> |&nbsp; |&nbsp;<!-- .element: class="table-hl" --> |&nbsp; |&nbsp; |&nbsp;<!-- .element: class="table-hl" --> |&nbsp;<!-- .element: class="table-hl" -->|

---

## Relationships Examples

 * Equality
   * Identity
   * Quantitative values
 * Ordering or quantitative
   * Less than (or equal)
   * Greater than (or equal)
   * "Comes before" and "Comes after"
 * Set-based operations
   * "Is a member"
   * "Is not a member"
   * "Shares members"
   * "Shares no members"

---

## Examples

### Equality

```
value == "hello"
value == 10
```

### Ordering and Quantitative

```
value < 30
value > July 1, 2010
```

### Set-Based

```
value in ("red", "blue")
value not in (3.141, 2.7)
```

---

## Sampling

We can choose a subset of points and use those to explore our data.  This is
not without its possible faults, however.

---

<!-- .slide: data-background-image="images/sampling_fig1.png" data-background-size="contain" -->

---

<!-- .slide: data-background-image="images/sampling_fig2.png" data-background-size="contain" -->

---

<!-- .slide: data-background-image="images/sampling_fig3.png" data-background-size="contain" -->

---

<!-- .slide: data-background-image="images/sampling_fig4.png" data-background-size="contain" -->

---

<!-- .slide: data-background-image="images/sampling_fig5.png" data-background-size="contain" -->

---

<!-- .slide: data-background-image="images/sampling_fig6.png" data-background-size="contain" -->

---

## Mutation Operations

 * Mathematical operations, such as injective operations.
   * Logarithmic versus linear representations
   * Arithmetic or multiplicative relationships
   * Manifold remapping
 * Smoothing (reduction; not injective)
 * Histograms (reduction; not injective)

---

## Binning and Histograms

<!-- .slide: data-background-image="images/circles.svg" data-background-size="auto 75%" data-background-position="right 10% bottom 50%"-->

<div style="width: 50%">
We can aggregate data points according to their position along defined
dimensions.
</div>

---

## Binning and Histograms

<!-- .slide: data-background-image="images/circles_grid.svg" data-background-size="auto 75%" data-background-position="right 10% bottom 50%"-->

<div style="width: 50%">
We can aggregate data points according to their position along defined
dimensions.
</div>


---

## Binning and Histograms

<!-- .slide: data-background-image="images/circles_grid_filled.svg" data-background-size="auto 75%" data-background-position="right 10% bottom 50%"-->

* $\Sigma 1$ (count)
* $\Sigma v_i$ (sum)
* $\frac{\Sigma v_i }{ \Sigma 1}$ (average)
* $\frac{\Sigma v_i w_i}{\Sigma w_i}$ (weighted average)

---

## Splitting Operations

We can split or group collections of data based on some characteristic.

<!-- .slide: data-background-image="images/split.svg" data-background-size="65% auto" data-background-position="top 5.0em center"-->

---

## Splitting Operations

We can split or group collections of data based on some characteristic.

<!-- .slide: data-background-image="images/split_finished.svg" data-background-size="65% auto" data-background-position="top 5.0em center"-->

---

## Data Types

When we are examining data, what can we look for?

 * Does this data describe a **geometric** object?
 * Are the data points **connected** to each other?
 * Can we describe data points with a fixed set of **categories**?
 * Is there a **quantity** associated with the data?
 * Are the datapoints **continuous** along one or more dimensions?

---

## Example: Geometric Object

<div class="left" data-markdown="true">

| v1 | v2 | cat |
|:-|:-|-:-|
|8.5|-9| r |
|10|-8| r |
|11.5|-7| r |
|12.5|-5.5| r |
|13|-4| r |
| ... | ... | ... |
|-2.5|-6|b|
|-1.5|-7|b|
| ... | ... | ... | 

</div>

---

## Example: Geometric Object

<div class="left" data-markdown="true">

| v1 | v2 | cat |
|:-|:-|-:-|
|8.5|-9| r |
|10|-8| r |
|11.5|-7| r |
|12.5|-5.5| r |
|13|-4| r |
| ... | ... | ... |
|-2.5|-6|b|
|-1.5|-7|b|
| ... | ... | ... | 

</div>

<!-- .slide: data-background-image="images/mushroom.svg" data-background-size="30% auto" data-background-position="right 20% bottom 50%" -->

---

## Examples: Quantity

We can encode the values associated with a data point by modifying how we
express it.  To do so, we need to be able to identify the different components
of representation, and how we can scale between them.

---

## Dimensions of Representation

Given a single datum on a visualization, we can control several different
components of its representation.

 * Position

<!-- .slide: data-background-image="images/dimensions_1.svg" data-background-size="auto 50%" data-background-position="right 20% bottom 50%"-->

---

## Dimensions of Representation

Given a single datum on a visualization, we can control several different
components of its representation.

 * Position
 * Color

<!-- .slide: data-background-image="images/dimensions_2.svg" data-background-size="auto 50%" data-background-position="right 20% bottom 50%"-->

---

## Dimensions of Representation

Given a single datum on a visualization, we can control several different
components of its representation.

 * Position
 * Color
 * Size

<!-- .slide: data-background-image="images/dimensions_3.svg" data-background-size="auto 50%" data-background-position="right 20% bottom 50%"-->

---

## Dimensions of Representation

Given a single datum on a visualization, we can control several different
components of its representation.

 * Position
 * Color
 * Size
 * Shape

<!-- .slide: data-background-image="images/dimensions_4.svg" data-background-size="auto 50%" data-background-position="right 20% bottom 50%"-->

---

## Dimensions of Representation

Given a single datum on a visualization, we can control several different
components of its representation.

 * Position
 * Color
 * Size
 * Shape
 * Relationship

<!-- .slide: data-background-image="images/dimensions_5.svg" data-background-size="auto 50%" data-background-position="right 20% bottom 50%"-->

---

<iframe width="1024" height="576"
src="https://www.youtube.com/embed/kY-pUxKQMUE" frameborder="0"
allow="autoplay; encrypted-media" allowfullscreen></iframe>

---

## Just to remove any ambiguity

Don't do this!

---

http://adsabs.harvard.edu/abs/2013ApJ...763...38S 

([This
plot](http://iopscience.iop.org/article/10.1088/0004-637X/763/1/38/meta#apj455166f4)
might be a bit too busy.)

<!-- .slide: data-background-image="images/skory_et_al.png" data-background-size="auto 75%" data-background-position="right 20% bottom 50%" -->

---

## Continuous Data

Data organized in a continuous fashion along one or more dimensions can enable
additional operations.

<!-- .slide: data-background-image="images/cube.png" data-background-size="auto 50%" data-background-position="right 20% bottom 50%"-->

---

## Continuous Data

Data organized in a continuous fashion along one or more dimensions can enable
additional operations.

<!-- .slide: data-background-image="images/cube_z_slice.png" data-background-size="auto 50%" data-background-position="right 20% bottom 50%"-->


---

## Distributions

Given a point or set of points, how do we make them into a "continuous"
distribution?

<!-- .slide: data-background-image="images/binning_1.svg" data-background-size="75% auto" data-background-position="bottom 30% center"-->

---

## Distributions

Given a point or set of points, how do we make them into a "continuous"
distribution?

<!-- .slide: data-background-image="images/binning_2.svg" data-background-size="75% auto" data-background-position="bottom 30% center" -->

---

## Distributions

Given a point or set of points, how do we make them into a "continuous"
distribution?

Uniform-width bins allow us to compute:

```python
bin_id = floor( (value - left_edge ) / bin_width)
```

<!-- .slide: data-background-image="images/binning_2.svg" data-background-size="75% auto" data-background-position="bottom 30% center" -->

---
## Distributions

Given a point or set of points, how do we make them into a "continuous"
distribution?

Non-uniform bins require searching.

<!-- .slide: data-background-image="images/binning_3.svg" data-background-size="75% auto" data-background-position="bottom 30% center" -->

---

## Binning and Histograms

<!-- .slide: data-background-image="../week03/images/circles_grid_filled.svg" data-background-size="auto 75%" data-background-position="right 20% bottom 50%"-->

* $\Sigma 1$ (count)
* $\Sigma v_i$ (sum)
* $\frac{\Sigma v_i }{ \Sigma 1}$ (average)
* $\frac{\Sigma v_i w_i}{\Sigma w_i}$ (weighted average)

---

## Summation

Useful for describing total quantity measured.

 * Inches of rain.
 * Total time of recorded UFO sitings in the area.
 * How many votes were cast?

---

## Arithmetic Average

Useful for describing average or mean quantity.

* Average rainfall in the area.
* Average time of UFO sighting.
* Who was the average candidate?

---

## Weighted Average

Useful for describing mean, but not strict arithmetic mean.

* Average rainfall, weighted by how humid it was that day.
* What was the most commonly seen UFO type, as a function of the time it was
  seen?
* What's the mean age of a voter, as a function of the total years of
  experience in the election?

---

## Scales and Scaling

Displaying a quantity requires assigning to it a given representation.
A common mechanism for doing this is to vary the color of a particular region
or set of display units with respect to the quantity expressed in those units.

In mathematical notation, we first "normalize" our data value by assigning to a
range:

$g(v) \rightarrow v' \in [0, 1]$

and then, given a color mapping function, assign to this a given color:

$f(v') \rightarrow (R, G, B)$

---

## Scales and Scaling

Group discussion:

  * How is this similar to or different from our discussions of "binning" and
    histogramming?
  * What are some functions we can use for $g(v)$?
  * What are some considerations we need to take into account for variable
    bins?

---

## Histograms and Binning

Group work:

Write a function -- in plain language at first, and then in python -- that
takes a set of values, a series of bin "edges," and returns to you the integer
IDs of the bins that each belongs to.

---

## Assignment 2

Using one of the tools that we have discussed (matplotlib or vega-lite),
construct a visualization of the Illinois Building Inventory that communicates
the following information:

 * Relationship between the year acquired and the year constructed
 * Total square footage as a function of congressional district
 * Average square footage per floor as a function of congressional district
 * Square footage for the five most common departments as a function of year

Each component will be worth 5 points and *must* be a completely communicative
visualization -- including labels and a one paragraph writeup of successes and
shortcomings in your approach.  Submit a notebook or a set of JSON gists to
Moodle.  All source code must be in these files.
