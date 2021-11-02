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

The outermost layer is takes precedence, and then is modified by the inner
layer, which is applied in order.

---

## Transforming

There are several `transform` options that we have not yet explored in detail.

 * `fold`
 * `flatten`
 * `lookup`
 * `window`

---

## Transform: `fold`

"`fold`"-ing a dataset transforms it by *expanding* to include additional keys,
to enable an additional parameter for selection.  For instance, if we have a
dataset of the form:

```
[ {'name': ..., 'prop1': ..., 'prop2': ...}, ... ]
```

we can apply a `fold` of `prop1` and `prop2` to obtain:

```
[ {'key': 'prop1', 'value': ..., 'name': ..., 'prop1': ..., 'prop2': ...},
  {'key': 'prop2', 'value': ..., 'name': ..., 'prop1': ..., 'prop2': ...} ]
```

---

## Transform: `flatten`

This operates similarly to `fold`, except that the inputs for `prop1` and
`prop2` are allowed to be arrays.  This produces a new set of rows in the
output data, one for each element in the corresponding arrays.

(This is less likely to be useful for input CSV data.)

---

## Transform: `lookup`

Occasionally we will want to use keys for lookup, based on other data rows.  We
can look up either in a named data source or in a fully-specified inline
datasource.

```json
{ "lookup": "primaryKey",
  "from": {
    "data": {"name": "referenceData"}
    "key": "keyInReference",
    "fields": ["prop1", "prop2"],
  }
}
```

---

## Transform: `window`

A `window` transform lets us perform an operation on a set of multiple rows in
our dataset.  *Crucially* we can also specify the *order* that they are
processed in.  It is defined like this:

```
  "window": [{
	  "op": ...,
	  "field": ...,
	  "param": ...,
	  "as": ...
  }],
  "sort": [
	{"field": ..., "order": ...}
  ],
  "ignorePeers": ...,
  "groupby": [
	"..."
  ],
  "frame": [...,...]
```

(We will demonstrate this!)

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

## Marks:

 * arc
 * trail
 * image
 * geoshape

---

## Encoding Channels

 * latitude / longitude
 * color
 * text / tooltip / href

---

## Putting this Together

We can now put this together to construct a COVID-19 dashboard.

It must have these characteristics:

 * Linking states to county-level visualizations
 * Supplemental information about states, including an image
 * Time series for national cases

How can we utilize our transforms, filters and view composition to this end?
