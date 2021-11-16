---
title: Dynamics in D3
layout: lecture
tags:
  - d3
  - javascript
description: >-
  This week we talked about using D3 for transitions, interaction, and we started sketching out our final project.
---

# Housekeeping

 * Having issues with uploading notebooks that will be corrected.
 * Starting after Thanksgiving break, we will be doing group presentations.
 * Order to be announced after groups assigned.

---

# Final Project

Your final project, to be completed in (assigned) groups, is to build a semi-realtime "observatory" of data.  You can find a few different possibilities for the data, but I want to encourage you to think of data related to things like:

 * Earthquakes
 * Space weather, rocks and satellites
 * Weather
 * Political events and news
 * Nothing directly COVID related

---

# Final Project: Phases

Your final project will have three phases, each of which will have a component for you to turn in.  The second and third components will be turned in as a group, but the first component will be individually graded.

**Before beginning, clear your dataset with me and Esther.**

Some places to look for dataset ideas:

 * [Awesome Public Datasets](https://github.com/awesomedata/awesome-public-datasets)
 * [Public APIs](https://github.com/public-apis/public-apis)
 * [Awesome JSON](https://github.com/jdorfman/awesome-json-datasets)

---

# Final Project: Part One

The first part of your project will be to *explore* the data; this is worth
**30 points out of 100**.  You are to turn in a notebook -- whether in
Observable, Python, Iodide, or a *combination* of them, that includes every
single cell and step you took in exploring the data.  This is an example of the
"visualization for self" process.  This means you might take shortcuts, you
might make mistakes, and you might make really, really awful visualizations.

Showing that you explored the data individually (even if you did it while
talking to a collaborator or classmate) is enough to satisfy this portion of
the project.

Download the data.  Dig in to it.  Look at it.  Find interesting things.
Experiment.  Make plots, make summary statistics, and make it familiar to
yourself.

---

# Final Project: Part Two

The second component of your project will be to design your "observatory." Note
that this is *pseudo* realtime.  It does not need to *automatically* update its
data; a refresh button, or requiring a page reload, is sufficient.  This is
worth **40 points out of 100**.

This could consist of drawings, prototypes of web pages or notebooks, and the
code necessary to build the different components.  This component is
*scaffolding*, not the final product.  It should be thought of as the "viz for
peers" stage of the process.  You can submit drawings (including photos of
drawings), jamboards, notebooks (which you *are* allowed to clean up), and
stages of prototypes.

You should walk me through the process of how you built your observatory, and
it does not need to be a linear, successes-only process.

---

# Final Project: Part Three

The final component of your project will be an in-class presentation of your
work, and the deployment of that work online.  This will be worth **30 points
out of 100**.

Your "observatory" should be located somewhere online, either as a notebook I
can download and run (or that runs on [binder](https://mybinder.org/)) or view
on observable, iodide, or Github Pages.

You will also have five minutes, as a *group*, to present your work in class.
This presentation needs to include the final product, as well as a summary of
any stumbling blocks you might have had, and a little bit of the process.

These presentations will be on the 2nd and 7th of December.  The project will
be due by the end of finals week, but you are **strongly encouraged** to submit
earlier.

---

## Review of D3 Basics

Last week we covered the very basics of [d3.js](https://d3js.org/), using
[observablehq.com](https://observablehq.com).

Review topics:

 * Creating a canvas
 * Adding items to the canvas
 * Positioning items

---

## Creating an SVG canvas

```javascript
const svg = d3.create("svg")
  .attr("width", 300)
  .attr("height", 300);

yield svg.node();
```

---

# Selecting and binding data

```javascript

var dataset = [
  {x1: 1.0, y1: 3.0, x2: 3.5, y2: 2.0, radius: 10},
  {x1: 2.5, y1: 2.0, x2: 0.75, y2: 3.5, radius: 5},
  {x1: 3.1, y1: 0.6, x2: 4.1, y2: 3.4, radius: 25}
];

svg.selectAll("circle")
   .data(dataset)
   .enter()
   .append("circle")
   .attr("cx", d => xScale(d.x1))
   .attr("cy", d => yScale(d.y1))
   .attr("r", d => d.radius)
   .style("fill", "black");
```

---

## Scaling

```javascript
var xScale = d3.scaleLinear().range([0, 100]).domain([0.0, 1.0]);
```

We will cover other scales later today.

---

## Events

There are many events that we can "listen" for, and respond to.  For instance, the `click` event is a common event to manage.

The function receives the data (if any), the index of the node, and the nodelist.

```javascript
d3.selectAll("circle")
  .on("click", (d, i, n) => {
    d3.select(n[i]).attr("r", 100)
  });
```

---

## Transitions

We can also update items through transitions, which can accept both a `delay` and a `duration`, both specified in milliseconds.

```javascript
d3.selectAll("circle")
  .data(dataset)
  .transition()
  .duration(2000)
  .attr("x", d => d.x + 2)
```

Updating attributes utilizes "tween"-ing functions for interpolation.  Many are
built in, but you can choose to build your own.

---

## Observable Notes: Data

There are ways to get data into observable.  The simplest is to use `await` on an asynchronous loading function, like this:

```
var near_earth = await d3.json("https://data.nasa.gov/resource/2vr3-k9wn.json");
```

(More ideas at https://github.com/jdorfman/awesome-json-datasets )

---

## Observable Notes: HTML

You can specify HTML as well, and then modify that in code.  This does not always require that you yield nodes.

```
html`<p id="my_hi">hi there</p>`
```

These can be selected by d3 as well.

In fact, we can modify *any* item in the DOM, not just SVG elements.  Can we modify this paragraph?

---

## Transformations

SVG specifies a number of [possible transformations](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/transform).  These include rotation, translations, skews and scales.  We can set these through the `.attr` call, but note that this requires a bit of string manipulation.

```javascript
svg.selectAll("circle").attr("transform",
    (d, i) => "skewY(" + i*5 + ")");
```

Note that we're concatenating an integer to a string here, which casts the int
to a string.  This is a bit non-intuitive.

We can use this to reshape our objects in many different ways -- especially using the index of the data point!

---

## Scales

D3 provides a number of different [scaling types](https://github.com/d3/d3-scale).  We will be discussing, specifically, banded scales and color scales.

One thing to note is that d3 also provides handy functions for computing properties of [arrays](https://github.com/d3/d3-array).  For instance:

 * `d3.min`, `d3.max`, `d3.minIndex` and `d3.maxIndex`, all of which accept both an iterable *and* an "accessor" function.
 * `d3.extent`, which provides the format required by a scale.
 * `d3.sum`, `d3.mean`, `d3.median`, `d3.quantil`, `d3.variance`

---

## Banded Scales

Banded scales provide discrete categorization of values, often used for categorical data.


```javascript
var band = d3.scaleBand(["low", "medium", "high"], [0.0, 100.0]);
```

This takes an array of input values for the domain.  Additional changes can be made to the bandwidth, padding, etc. The d3 wiki has a  
[diagram](https://raw.githubusercontent.com/d3/d3-scale/master/img/band.png) describing this.

---

## Color Scales

We can use `d3.scaleSequential` to generate colormaps for continuous values.  These accept an interpolator function.  d3 provides interpolator functions for many common colormaps.  For instance:

```javascript
var csc = d3.scaleSequential(d3.interpolateViridis).domain([1.0, 100.0])
```

We can also use log versions of these, and quantized versions.

---

## Brushing

Brushing in d3 requires some build-it-yourself effort, but building a brush object itself is straightforward.  You create a brush object with extents, and you call that on your object.  Here, `brushed` is a function to be called when the brush selection changes.

```

function brushed() {
  console.log(d3.event.selection);
}

var brush = d3.brush()
              .extent([[0.0, 0.0], [512, 512]])
              .on("brush", brushed);
svg.append("g").attr("class", "brush").call(brush);
```

What could we do with this?

---

## Paths

d3 can also generate `path` objects.  Typically these are generated using curve
generators.

```javascript
var line = d3.line().curve(
            d3.curveCatmullRom.alpha(0.5));
var myPath = svg.append("path")
              .attr("d", line(myPoints))
              .attr("stroke", "black");

```

Interpolation of paths can be tricky, but it is possible.

---

## Experiment Time

Let's build a near-earth object explorer.

 * Sketch out a design in groups
 * Discuss as a class the different designs
 * Build as a class 

---

## Exporting to a webpage

Now how do we export this to a webpage?
