---
title: Subselection, Layouts and Dashboards
layout: lecture
tags:
  - bqplot
  - python
  - pandas
  - dashboards
description: >-
  Today we'll talk about map projections, how to properly wrap a baseball, and continue with our dashboarding.
---

## Today

 * Visualization reports
 * Talk a little about maps
 * Intro CartoPy
 * Continue with our bqplot interactivity

Alternately, we can move the middle two items to Thursday.

---

## Visualization Reports

---

## Today

 * A little more pandas
 * Setting up linking and brushing
 * Layouts

---

## Pandas

We'll need a few things today:

 * You can select based on the index column using `.loc`
 * Selections based on integer position use `.iloc`
 * We will split our dataframe into per-state groups, then index based on the date

---

## Linking and Brushing

We will update our visualization to include:

 1. Display time series aggregations based on selection
 2. Display county-by-county visualizations for Illinois
 3. State-by-state counties, based on state selection

---

## Layouts

We now need to update our layouts, utilizing `HBox` and `VBox` and our styles.

---

## Object-Orientation

Our next step will be to utilize an object in python that tracks the current state of our view.  We will build this on top of the `traitlets` library, using the `traitlets.HasTraits` class to handle state changes.

```
class TimeSeriesDataDisplay(traitlets.HasTraits):
    dataframe = traitlets.Instance(pd.DataFrame)
```

This is our simplest container, that holds our original dataframe.  We will extend this using decorator syntax, `@traitlets.observe` and `@traitlets.default` to set up observer functions and default values.

Within our object, we will hold all the information necessary to describe our visualization.  What will this include?

---

## Object-Orientation

Once we have our stateful object, we will extend it with a `_display_ipython_` method.

This method must use the `display` function to actually construct a display, and connect attributes of itself to the attributes of the displayed object.  For instance, selection, dataframe, and the like.

What else can we do with this?
