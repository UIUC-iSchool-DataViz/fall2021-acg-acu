---
title: Dashboards and Gaia
layout: lecture
tags:
  - python
  - voila
  - dashboards
description: >-
  This week, we tried bringing it all together: let's talk about dashboards in
  Jupyter, and we'll explore Gaia eDR3 data using the tools in our toolbox.
---

## Dashboards

We will utilize [Voila](https://voila.readthedocs.org/) to construct dashboards in Jupyter, but it's really straightforward!

---

## Dashboards: Voila

Voila can be run as either a standalone application or as a server extension to Jupyter.  Voila is not enabled on the iSchool jupyterhub, but can be installed using conda:

```bash
conda install voila
git clone https://github.com/voila-dashboards/voila voila-dashboards
cd voila-dashboards
voila notebooks/
```

Alternately, once it has been installed, you can check that it is enabled for a server extension:

```bash
jupyter serverextension list
```

---

## Voila Deployment

Voila can be deployed to Binder, Heroku, and so forth.  There are instructions in the Voila Documentation for [how to do so](https://voila.readthedocs.io/en/stable/deploy.html).

---

## Putting This All Together

Welcome to the capstone section!

Today we will be exploring the new data release from the Gaia satellite!

![Gaia spacecraft](https://upload.wikimedia.org/wikipedia/en/0/01/Gaia_spacecraft.jpg)<!-- .element: class="centered" -->

---

## Gaia Data

The Gaia eDR3 -- just out! -- includes a collection of `.csv.gz` files.  The full collection can be found here:

https://gea.esac.esa.int/archive/

but we're most interested in those under this URL:

http://cdn.gea.esac.esa.int/Gaia/gedr3/gaia_source/

The data model for these can be found [here](https://gea.esac.esa.int/archive/documentation/GEDR3/Gaia_archive/chap_datamodel/sec_dm_main_tables/ssec_dm_gaia_source.html) but the most important parts are:

| Name           | Info                         |
|----------------|------------------------------|
| `RA`           | Right ascension (Angle[deg]) |
| `DEC`          | Declination (Angle[deg])     |
| `PARALLAX`     | Parallax ([mas])             |
| `PMRA`         | Proper motion RA ([mas/y])   |
| `PMDEC`        | Proper motion dec ([mas/y])  |
| `PSEUDOCOLOUR` | "Colour" ($\mu m^{-1}$)      |

---

## Our Task

Our task for today is to *explore* this data, using Python.  We will utilize this set of tools:

 * Pandas for reading the data
 * Matplotlib for static plots and distributions
 * bpqlot and ipywidgets for detailed exploration

Each of you will pick out three random data files, read them using pandas, and
explore the distribution of these objects based on these parameters.

At the conclusion, we will voila-ize our notebook!
