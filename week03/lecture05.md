---
title: Transformations and Scaling
layout: lecture
tags:
  - scaling
  - transformations
description: >-
  How do we transform and scale data?  How can we apply scalings to data, and what does this have to do with color?
---

## Today's Topics

 * Transformations 
 * Scaling

---

## Transformations

We will need to transform data in order to apply consistent visual encoding.
There are many reasons we may need to accomplish this, including color mapping,
applying units, and co-registration or normalization of data.

One of the most important transformations we will have is that of an [Affine transformation](https://en.wikipedia.org/wiki/Affine_transformation).  This is a transformation that preserves:

 * Collinearity
 * Parallellism
 * Convexity
 * Ratios of parallel lines
 * Barycenters of point sets

---

## Transformations

Affine transformations satisfy:

$ \vec{y} = A\vec{x} + \vec{b} $

<!-- .slide: data-background-image="images/affine_1.svg" data-background-size="30% auto" data-background-position="right 20% bottom 50%" -->

---

## Transformations

Affine transformations satisfy:

$ \vec{y} = A\vec{x} + \vec{b} $

We can use these to accomplish:

 * Shifts

<!-- .slide: data-background-image="images/affine_2.svg" data-background-size="30% auto" data-background-position="right 20% bottom 50%" -->

---

## Transformations

Affine transformations satisfy:

$ \vec{y} = A\vec{x} + \vec{b} $

We can use these to accomplish:

 * Shifts
 * Rotations

<!-- .slide: data-background-image="images/affine_3.svg" data-background-size="30% auto" data-background-position="right 20% bottom 50%" -->

---

## Transformations

Affine transformations satisfy:

$ \vec{y} = A\vec{x} + \vec{b} $

We can use these to accomplish:

 * Shifts
 * Rotations
 * Scaling

<!-- .slide: data-background-image="images/affine_4.svg" data-background-size="30% auto" data-background-position="right 20% bottom 50%" -->

---

## Transformations

<div class="col" data-markdown=true>

In this figure, we can adjust the mixing vectors and the offset.  What do you notice about colinear points and parallel lines?

<div class="fig-container" data-style="height: 600px;" data-file="figures/affine_transformation.html" data-markdown=true>
</div>

---

## Scaling Data: Normalization

Last week, we began to address the notion of mapping between different numerical values, for the purposes of scaling between our "data" space and our "plot" space.

$f(v) \rightarrow (R, G, B)$

When we map to colorspace, we can also re-map:

$g(v') \rightarrow (R, G, B)$

$v' = f(v)$

This can be done using a linear mapping, or we can *stretch* or *distort* the mapping by using logarithms or square roots.

Are these affine transformations?

---

## Scaling Data: Linear Normalization

We map from a range of values to (0, 1):

$ v' = (v - v_0)/(v_1 - v_0) $

If we set $v_0$ and $v_1$ to be defined by the minimum and maximum values in our dataset, this will result in a map that is (inclusively) bound by 0.0 and 1.0.

We will call our output values our *range* and our input values our *domain*.

---

## Back to Matplotlib

We will explore these concepts using matplotlib.

Please be sure to see the "cheat sheets" affiliated with this, which can be found at:

[github.com/matplotlib/cheatsheets/](https://github.com/matplotlib/cheatsheets/)

and which have been duplicated in this repository.
