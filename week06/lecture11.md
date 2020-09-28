---
title: Viz Platforms and more Vega-lite
layout: lecture
tags:
  - platforms
  - vega-lite
  - web
  - javascript
description: >-
  We go over more details of using vega-lite and how to embed vega-lite visualizations in a web page.
---

## Evaluating Visualization Engines

 * Costs
 * Functionality
 * Aesthetics

---

## Choices

 * Can I get ahold of this software?
 * Do I install it, or do I use it on a server?
 * What's the user interface like?
 * Is it declarative or is it procedural?

---

## License: Software

 * What can you do with the software?
 * Can you study the software?
 * Who can you share it with?
 * Who can you give your derivative works to?

---

## License: Software

 * Copyleft: share and share-alike
 * Non-copyleft: share, but don't necessarily need to share-alike
 * https://choosealicense.com/

---

## License: Data

 * What can you do with the data?
 * How do you credit that data?
 * Can the data be redistributed, remixed, modified?
 * http://opendefinition.org/guide/data/
 * https://theodi.org/guides/publishers-guide-open-data-licensing

---

## Accessibility

 * Is the software installed locally on your machine?
 * Is it hosted at a local or remote instance?
 * Who owns the visualizations, and how is access to them controlled?

---

## Interface

How do you interact with the software?

 * Declarative: how do you want the plot to look?
 * Procedural: what are the steps to make the plot look that way?

---

## Example Declarative

```python
Chart(df).mark_bar().encode(
    X('precipitation', bin=True),
    Y('count(*):Q')
)
```

(From [Altair Docs](https://altair-viz.github.io/tutorials/exploring-weather.html))

<!-- .slide: data-background-image="images/altair_example01.png" data-background-size="30% auto" data-background-position="right 20% bottom 20%" -->

---

## Evaluation: Costs

The "cost" of software is not exclusively the number of dollars you place on
the counter when you get a big cardboard box with marketing blurbs on the side.

Think about cost in several ways:

 * Monetary cost for *you* to use the software
 * Monetary cost for *someone else* to view your creations
 * Temporal cost of setting up
 * Cognitive cost for learning and using the system (documentation matters!)
 * Transmission cost for sharing your creations

---

## Evaluation: Aesthetics

Visualization is trendy.

When you construct something, think about the different ways it will be
interpreted:

 * How will the viewer understand the story of the data?
 * What will the _message_ of the visualization be?
 * Does the visualization say something about you and your handling of the data
   or utilization of tools?

---

## Assignment 5

Your assignment is to pick four of the following possibilities and write up a
set of comparisons for constructing the *same* visualization.   You must evaluate matplotlib, vega-lite and bqplot, and you can choose one of the following in addition: D3, Bokeh, Plotly, R/RStudio.

These comparisons should be:

 * What is the license for the software?
 * What is the focus of the software?
 * Does it have interactivity, and how easy is it?
 * What are the pros and cons of using it?

These should total roughly half a page per engine.

---

## More vega-lite

Today we will fill out more components of our understanding of vega-lite.  Last
week we discussed marks and encodings.  This week we will continue with marks,
adding on transformations and selections.

Recall that vega-lite is defined in a JSON specification.  This specification will typically take a form similar to this:

```json
{
  "data": .. ,
  "transform": [ .. ],
  "mark": .. ,
  "selection": .. ,
  "encoding": .. ,
  "config": ..
}
```

---

## vega-lite marks

vega-lite has numerous different `mark` types.  We can break these down by the type of data they can represent.  We will only consider "primitive" marks today.

 * `area` & `line`
 * `bar` & `rect`
 * `point` & `circle` & `square`
 * `rule` & `text`
 * `tick`
 * `geoshape`

We will demonstrate several of these using our datasets, but first we need to learn how to transform data.

---

## vega-lite transformations

At the `view`-level of your definition, you can specify transformations that modify, filter, or reshape the data.

At the top level, we specify a transformation.  We can transform data within a given dataset (by specifying a new attribute of each data point) or by reshaping the data.

The types of transformations we will cover today are `filter` and `calculate`.

---

## vega-lite filtering

We apply a `filter` transform by specifying the field to filter on and the filtering characteristic.  This can be a selection, an expression, or a logical definition.  We will address selection and expression filtering later.

---

## vega-lite filtering

A logical filtering operation might look like one of these:

```json
"transform": [
  {"filter": {
      "field": "eye_color", "oneOf": ["blue", "brown"]
      }
  },
  {"filter": {"field": "age", "lte": 100 }
  }
]
```

We can use `lt`, `gt`, `lte`, `gte`, `eq`, `oneOf`, `range` and `valid`.

---

## vega-lite calculate

We can also compute a new field using the `calculate` transform.  This is an expression that is evaluated on every data point, which is supplied as the variable `datum` to the expression.

```json
"transform": [
  {"calculate": "datum.age / 7", "as": "dog_years"}
]
```

---

## vega-lite selections

Selections are defined with *names* -- this seems to be the most common stumbling block.  You get to choose the name!

We use selections in one of a few ways.

 * We can conditionally encode data -- for instance, change visibility, or alpha, or color.
 * We can use selections as input for filtering data.  Typically this is done with one plot showing unfiltered data and another using a filter from that selection.
 * Scale a domain based on a selection

---

## vega-lite selections

There are three types of selections:

 * `single` -- selecting a single point, 
 * `multi` -- multiple points
 * `interval` -- collections of values along encoding axes

We will focus on the `interval` selection.

---

## vega-lite interval selection

We can define a box-based selector that operates along the x axis by specifying which encoding it is linked to.  Here, we name it `valrange`, but we can choose whatever name we like.

```json
"selection": {
    "valrange": {"type": "interval",
                 "encodings": ["x"]
                 }
    }
```

Let's try this.

