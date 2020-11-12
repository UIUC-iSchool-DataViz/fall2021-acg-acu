---
title: Starting D3
layout: lecture
tags:
  - d3
  - javascript
description: >-
  
---

## A Little Bit of D3

We're going to learn a very small bit of [d3.js](https://d3js.org/).

The easiest way to utilize D3 is through [observablehq.com](https://observablehq.com):

```
d3 = require("d3@5");
```

although it is straightforward to include the necessary code in an HTML page:

<code>
&lt;script src="https://d3js.org/d3.v5.min.js"&gt;&lt;/script&gt;
</code>

---

## Concepts in d3: outline

The basic concepts here we will convey, focusing on *static* visualizations:

 * `.select()` and `.selectAll()`
 * `.enter()`
 * `.attr()` and `.style()`
 * `d3.scaleLinear()`

---

## Concepts in d3: data and elements

When we manipulate items in d3, we connect the concept of a data item to an
element in a document.

Typically, this will be an element in an SVG -- for instance, a `line`,
`circle`, `rect` or `text` element.

Our typical workflow:

 1. Select all items of a specific criteria
 2. Bind these items to a set of data
 3. Update, append or remove items based on their corresponding item.

---

## Concepts in d3: accessors and setters

We will very frequently run into the case where we call something, and supply a
*function* to it, rather than supplying a value.  For instance, *both* of these
calls to `attr` are valid in a typical d3 workflow:

```javascript
.attr("cx", 1.0)

// or

.attr("cx", d => d.x)
```

In one, we are setting the value static; in the other, we base the value on the datapoint supplied.

---

## Concepts in d3: Let's make circles

For our first exploration, let's just make some circles.  I will demonstrate this in observable, but here is the key snippet of code:

```
var dataset = [ {'x': 100, 'y': 200, 'radius': 15},
                {'x': 150, 'y': 300, 'radius': 30} ];
svg.selectAll("circle").data(dataset).enter()
   .append("circle")
   .attr("cx", d => d.x)
   .attr("cy", d => d.y)
   .attr("r", d => d.radius)
   .style("fill", "black");
```

What does this do?

---

## Concepts in d3: Objects

We will mostly use the objects

 * [`rect`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/rect) -- which has `x`, `y`, `width` and `height` 
 * [`circle`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/circle) -- which has `cx`, `cy`, and `r`
 * [`line`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/line) -- which has `x1`, `x2`, `y1` and `y2`.

Each of these objects can be controlled in style, appearance, position, etc, according to standard SVG and CSS rules.

Let's experiment!

---

## Concepts in d3: Scaling

To map from a given range to a different range in a linear fashion, we can construct a linear scale:

```javascript
var xScale = d3.scaleLinear().range([0, 100]).domain([0.0, 1.0]);
```

This is now an object we can use to map the values 0 .. 1 to 0 .. 100.  This is useful for, among other things, computing the position of a given value:

```javascript
.attr("cx", d => xScale(d.x))
```

---

## Additional Basic Topics

`d3.axisBottom(xScale)` can be used to create ticks and axes; however, it
requires manual translation using the `transform` attribute, using something
like `.attr("transform", "translate(0, 30)")`.  This then brings up our concept
of margins, width, height, and the like!  How can we manage these?

Let's try it out!

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
