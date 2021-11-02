---
title: More Vega Lite
layout: lecture
tags: 
  - vega-lite
description: >-
  What else can we do with vega-lite?
---

## Visualization Reports

---

## Today: vega-lite

 * vega-lite
    * transforming data
    * filtering data
 * view composition
    * layers
    * faceting
    * repeating
 * types of marks
    * arc
    * trail
    * image
    * geoshape
 * encodings
    * tooltips

---

## Thinking about vega-lite

We've seen 

Think about the progression thusly:

 * Outer-to-inner in JSON objects
 * First-to-last in arrays

---

## Thinking about vega-lite

So for instance, when examining a specification with outermost values defined:

```
{
  ...
  { "transform": [ ... ] },
  "mark": {
    "type": "bar",
    "transform": [ .. .]
    ...
  }
}
```

The outermost layer is takes precedence, and then is overridden by the inner
layer, which is applied in order.

---

## Transforming

 * `fold`
 * `flatten`
 * `lookup`
 * `window`

---

## Filtering

 * ranking
 * parameters

---

## View Composition

 * Layering
 * Faceting
 * Repeating

---

## Marks: arc

---

## Marks: trail

---

## Marks: image

---

## Marks: geoshape

projection albers, albersusa, encoding lat/lon

---

## Encoding Channels

 * latitude / longitude
 * color
 * order
 * text / tooltip / href
 *
