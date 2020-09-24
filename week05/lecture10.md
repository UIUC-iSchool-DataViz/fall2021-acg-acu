---
title: Web and Vega-lite
layout: lecture
tags:
  - vega-lite
  - web
  - javascript
description: >-
  We introduce a little bit of javascript, how to publish websites on GitHub,
  and we start learning vega-lite.
---

## Status Update: What's Left

Today, we are introducing the *final* major tool we will use: [vega-lite](https://vega.github.io/vega-lite/).

We will likely explore, in brief one-offs, a handful of additional tools.

---

# The Web

 * Content is transmitted from point-to-point
 * Content can be manipulated locally or remotely
 * Not all servers can manipulate data before sending

---

# Your Browser

 * Your browser contains -- essentially -- an entire operating system.  It can
   manage:
    * Display mechanisms
    * Interaction with you, the user
    * Input/output from files and file-like objects
    * Interpreter to execute code
 * Most of its activities are mediated via a document object model (DOM) and
   the programming language Javascript

---

# Things to Note

 * Javascript is "garbage collected"
 * Javascript is single-threaded
 * Asynchronous programming can be a real noodle-bender

---

# Document Object Model

The Document Object Model (DOM) is how we interact with the collection of HTML
objects in our document.

For instance, a page can be composed of `<div>` objects, `<p>` objects, etc,
and we can construct and interact with these.  This includes things like
modifying style sheets.  See, for example, the
[jsfiddle](https://jsfiddle.net/) for [jQuery
boilerplate](https://jsfiddle.net/boilerplate/jquery).

One alternative, as we will see, is to have rendering tied to data and data
values, and to have those automatically update as needed.

---

# Synchronous programming

In Python, we would fetch a website and wait for that to finish before we move
on.

```
import requests

r = requests.get("https://google.com/")
print(r.text)
print("Request completed!")
```

---

# Asynchronous programming

In Javascript, we would tell the code to fetch, but we would also tell it what
to do *after* it finished.

This uses jQuery, but you can [do it without
that](http://youmightnotneedjquery.com/#json).

```
$.get("https://google.com/", function(data, status){
      alert("Data: " + data + "\nStatus: " + status);
});
console.log("Hey, I've done the thing.");
```

Note that you can't always get this to work. In fact, that example won't even
work!

---

# Async and Event-Driven

Async is how we can think about event driven programming, as well.  We have
done this using `traitlets` and `ipywidgets` in Python, and we will do it here
as well.

```
var button = $("button");

button.on("click", function() {
    console.log("I've been clicked!");
});
```

---

# Basic Javascript

We will go over a few things, and then move on to vega-lite.

You can declare variables in Javascript implicitly or explicitly, depending on how you want them scoped.

```
var myArray = [1, 2, 3, 4];
var myString = "Hello there!";
var myConcatString = "Hi " + "there " + 5;
var myObject = {'a': 1, 'b': 2, 'c': [1, 2, 3, 4]};
```

---

# Updating variables

If you have an array of objects, there are three very handy functions you can
utilize: `slice`, `forEach` and `filter`.  If you have an object, you can
update it either by accessing a property with a period (`obj.something`) or by
accessing it like you would a dictionary in python (`obj['something']`).

---

# Arrays: `filter`

```
var myArray = [1, 5, 1, 3, 50, 14, 2];
myArrayFiltered = myArray.filter(val => val > 2);
```

Note that here I'm using `=>` as shorthand for declaring a function.

---

# Arrays: `forEach`

To execute something on every value in an array, you can call `forEach` with a
function.

```
var myArray = [1, 2, 3, 4, 5];
myArray.forEach(val => console.log(val * 2));
```

---

# Arrays: `slice`

You can set a start and a stop on an array with a `slice` call:

```
var myArray = ["Hello", "I", "am", "here", "now"];
myArray.slice(3).forEach(word => console.log(word));
```

---

# Publishing a Website

We will utilize `github.com` for publishing.  When you use Github for
publishing a website, it will be deployed at `username.github.io` (where
`username` is your username!)

GitHub has a tutorial at [pages.github.com](https://pages.github.com/).

---

# GitHub Pages: Getting Started

Create a new repository named `username.github.io`, where you have replaced
`username` with your username.

---

# GitHub Pages: Clone your Repository

At the command line, including on the iSchool jupyterhub, you can type:

```bash
git clone https://github.com/username/username.github.io.git
cd username.github.io
```

Other environments, like Visual Studio Code or Atom, also work well for this.

---

# GitHub Pages: Adding a page

Create a file -- you can do this within JupyterHub or from the command line -- called `index.html`.  It can contain anything, for instance:

```html
&lt;!doctype html&gt;
&lt;html&gt;
  &lt;head&gt;
    &lt;title&gt;This is the title of the webpage!&lt;/title&gt;
  &lt;/head&gt;
  &lt;body&gt;
      &lt;p&gt;
      This is an example paragraph. Anything in the &lt;strong&gt;body&lt;/strong&gt;
      tag will appear on the page, just like this &lt;strong&gt;p&lt;/strong&gt;
      tag and its contents.
      &lt;/p&gt;
  &lt;/body&gt;
&lt;/html&gt;
```

---

# GitHub Pages: Publishing

You will need to add the page to your repository.  You can do this with:

`git add index.html`

Once this has been "staged" for commit, you can execute the commit with:

`git commit -m "Adding index.html"`

Your commit message can me anything. This will need to be "pushed" to GitHub, with:

`git push`

After a few moments, it should be accessible at `https://username.github.io/`
where `username` is, again, your username.

---

# vega-lite

Up until now, we have *mostly* written code that is _imperative_.

This means we have described *how* we wanted to have things accomplished,
rather than *what* we want to accomplish.  vega-lite is a declarative grammar
for (interactive) visualizations that allows us to specify the connection between components.

We will utilize an interactive editor for vega-lite.  This helps us to ease
some of the pains of correctly writing JSON, of knowing what we can and cannot
use in a given spot, and it also provides us with lots of [sample
datasets](https://github.com/vega/vega-datasets).

https://vega.github.io/editor/#/custom/vega-lite

---

## vega-lite: specification

vega-lite visualizations are defined in a JSON specification.  This
specification will typically take a form similar to this:

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

The syntax you will need to be the most familiar with:

 * [`mark`](https://vega.github.io/vega-lite/docs/mark.html): how to visually represent something
 * [`encoding`](https://vega.github.io/vega-lite/docs/encoding.html): the translation between data and the mark
 * [`aggregate`](https://vega.github.io/vega-lite/docs/encoding.html): operating over a collection of points -- `mean`, `sum`, `median`,
   `min`, `max`, `count`
 * [`type`](https://vega.github.io/vega-lite/docs/type.html): `quantitative`, `temporal`, `ordinal`, or `nominal`

---

# vega-lite syntax: basics

From the vega-lite examples, you can make a bar chart that is an aggregate like so:

```
{
  "$schema": "https://vega.github.io/schema/vega-lite/v4.json",
  "data": {"url": "data/movies.json"},
  "mark": "bar",
  "encoding": {
    "x": {
      "bin": true,
      "field": "IMDB Rating",
      "type": "quantitative"
    },
    "y": {
      "aggregate": "count",
      "type": "quantitative"
    }
  }
}
```

---

# vega-lite syntax

There are several mechanisms by which we describe data representations in
vega-lite, but the overarching principle is that it is declarative.  We define
what it does based on what we say we want it to look like.

(The place where this is no longer true is when we modify `datum` values, but
we'll get to that next time.)

---

## Assignment 4

Your assignment for this week is to build a web page on GitHub pages (which can
be with a "burner account", as long as you supply that info to us) that
includes a vega-lite visualization of the building inventory dataset.

This will have three steps:

 1. Develop a visualization using vega-lite using the building inventory data
 2. Deploy this visualization in JSON format to your GitHub pages
 3. Write the initialization javascript code to create the visualization in your page

You will have a week and a half to do this, as we have not covered quite enough
yet to make this work.
