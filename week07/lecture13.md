---
title: Time Series Data
layout: lecture
tags:
  - matplotlib
  - python
  - timeseries
  - github-pages
include_twitter: true
description: >-
  Today we'll cover some time-series axes, use bqplot to display a Map and talk about how to use Pandas for time-series data.
---

## Today

 1. Updates
 2. Trigger Warning for Today
 3. Time series data on maps

---

## Visualization Report Presentation

---

## Updates on a Few Things

Jupyter Lab has been updated, and we can now edit vega-lite files without difficulty inline.

To access Jupyter Lab and edit a vega-lite file:

 1. Go to your `jupyterhub.ischool.illinois.edu` server
 2. Replace the trailing `/tree?` in the URL with `/lab` at the main listing of notebooks.
 3. Create a new text file and name it with the suffix `.vg`.
 4. Right-click on the file and choose "Open With -> Editor"
 5. Double-click on the file to open in the vega-lite viewer.

---

<iframe width="1008" height="567" src="https://www.youtube.com/embed/BzqIVxtwoj4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

## Re-enabling bqplot

With the current jupyterlab, you will need to reenable bqplot by executing these commands in notebook cells:

```bash
!pip install bqplot
```

```bash
!jupyter labextension install bqplot
```

You'll then have to close your browser window and re-open it.

---

## Buildings and Dates

Let's revisit our building dataset.  When we first load the data:

```python
df = pd.read_csv("building_inventory.csv", na_values={
    "Year Acquired": 0,
    "Year Constructed": 0,
    "Square Footage": 0
})
```

Our columns, from `df.dtypes`, look like:

```
...
Year Acquired              float64
Year Constructed           float64
...
```

But maybe we want these to be date time.

---

## Converting to datetime

We can convert our dataframe columns using casting and assignment:

```python
df["Year Acquired"] = ...
```

Note that if default parsing worked, we could supply a `parse_dates` argument.  But ours requires some modification.

We can use `pd.to_datetime` to convert our dates.  What happens if we use it without any arguments?  Why?

It accepts a `format` argument, which for us will be `"%Y"`.

---

## Before We Begin

Today we're going to talk about data from the COVID-19 pandemic.

This is a serious topic, and one that touches all of us, and if you are uncomfortable with this topic, I invite you to sign off and connect with me directly.

---

<blockquote class="twitter-tweet tw-align-center"><p lang="en" dir="ltr">Everyone under that red line was a real person. Hundreds of thousands of people are dead, and every one of them was as real as you. Brave or fearful, weak or tough, flamboyant or shy, the virus doesn&#39;t give a shit. <a href="https://t.co/MevDh61mvK">pic.twitter.com/MevDh61mvK</a></p>&mdash; Kieran Healy (@kjhealy) <a href="https://twitter.com/kjhealy/status/1313276959263162368?ref_src=twsrc%5Etfw">October 6, 2020</a></blockquote>

---

<blockquote class="twitter-tweet tw-align-center"><p lang="en" dir="ltr">Racial disparities in COVID-19 Death rates are shockingly high at younger ages. The Black/White death rate by age range:<br><br>30-49: 7.3<br>50-64: 5.5<br>65-74: 4.5<br>75-84: 3.2<br>85+: 2<br><br>h/t <a href="https://twitter.com/familyunequal?ref_src=twsrc%5Etfw">@familyunequal</a> <a href="https://t.co/sevXWp1NNF">pic.twitter.com/sevXWp1NNF</a></p>&mdash; Trevon D Logan (@TrevonDLogan) <a href="https://twitter.com/TrevonDLogan/status/1313450709875134465?ref_src=twsrc%5Etfw">October 6, 2020</a></blockquote>

---

<blockquote class="twitter-tweet tw-align-center"><p lang="en" dir="ltr">MICHELLE McCRACKIN, 53, a teacher in Carson City, Michigan, has died of COVID-19. <br><br>“There are now 15 positive COVID-19 cases in the rural school district of 900 students.”<a href="https://t.co/56WpndVMoI">https://t.co/56WpndVMoI</a></p>&mdash; FacesOfCOVID (@FacesOfCOVID) <a href="https://twitter.com/FacesOfCOVID/status/1313300319464497153?ref_src=twsrc%5Etfw">October 6, 2020</a></blockquote>

---

<blockquote class="twitter-tweet tw-align-center"><p lang="en" dir="ltr">SHARON BASCOM, 61, a kindergarten teacher at PS 306 in Brooklyn, died of COVID-19 on April 6. <br><br>She &quot;loved teaching math and seeing the smiles on her students’ faces – as if a lightbulb had gone off – as they figured out the answer to a math problem.&quot;<a href="https://t.co/PI3uKsjIy5">https://t.co/PI3uKsjIy5</a> <a href="https://t.co/T4dFk98HFt">pic.twitter.com/T4dFk98HFt</a></p>&mdash; FacesOfCOVID (@FacesOfCOVID) <a href="https://twitter.com/FacesOfCOVID/status/1313282830299009025?ref_src=twsrc%5Etfw">October 6, 2020</a></blockquote>

---

<div style="height: 600px; position: relative;">
  <div style="max-height: 100%; overflow: auto;">
    <a class="twitter-timeline tw-align-center" href="https://twitter.com/FacesOfCOVID?ref_src=twsrc%5Etfw">Tweets by FacesOfCOVID</a>
  </div>
</div>

---

## Time Series Data

We will utilize some data from the NY Times.

[NYT COVID-19 Data](https://github.com/nytimes/covid-19-data)

```
!rm -f us-counties.csv ; wget https://raw.githubusercontent.com/nytimes/covid-19-data/master/us-counties.csv
```

---

## Geographic Locations

bqplot provides the `Map` mark.

The `scales` property for the `Map` mark should have entries for both `projection` and `color`.  `projection` will be one of the geographic projections (more on that next time) such as `AlbersUSA`.

The `Map` mark must also have `map_data` defined, which is a TopoJSON file.  For our purposes, we will use the built-in `bqplot` function `topo_load`, which can accept one of:

 * `map_data/USCountiesMap.json` for US county-level data keyed by FIPS
 * `map_data/USStatesMap.json` for US state-level data
 * `map_data/EuropeMap.json` for European countries
 * `map_data/WorldMap.json` for the full Earth

---

## Today

Today, we will use the `Map` mark, our interval selectors, and our county/state level data to generate some visualizations of COVID cases.

Each number we see is a human life, changed.
