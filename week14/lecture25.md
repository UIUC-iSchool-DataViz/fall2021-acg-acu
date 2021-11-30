---
title: Workflows and Reusability
layout: lecture
tags:
  - d3
  - javascript
description: >-
  This week we talked about making things reusable.
---

# This Week: Putting it Together

This week we will focus on how to "put it all together" and turn your
visualization experiments into systems and workflows.

We will focus on Python for the time being.

---

# Reusability

Why would we want to "reuse"?  Why is it worth our time and effort to make our
code and projects reusable?

 * Prevent mistakes <!-- .element: class="fragment" -->
 * Save time <!-- .element: class="fragment" -->
 * Increase flexibility <!-- .element: class="fragment" -->
 * Foster experimentation <!-- .element: class="fragment" -->

But I won't lie to you: this will take time, effort, and it's probably going to
be annoying. <!-- .element: class="fragment" -->

It's probably also worth it. <!-- .element: class="fragment" -->

---

# Reusability

There are two main approaches to constructing a reusable bit of code -- the
forward-thinking way, and the retrofitting way.

(Confession: I usually end up doing the second one, not the first.) <!-- .element: class="fragment" -->

---

## Reusability: Forward-thinking

[Think about what you're going to
do](https://illinois.pbslearningmedia.org/resource/1de0b56d-7049-4335-98e0-e8a4fd82b51e/pick-the-clothes-that-are-right-for-you-daniel-tigers-neighborhood/)
and how you might want to use your functions, and plan ahead.

 * Put everything into functions!  Even if you don't think you should! <!-- .element: class="fragment" -->
 * Don't use globals, just use default arguments <!-- .element: class="fragment" -->
 * Need to carry around some info? Maybe a "class" is a good idea! <!-- .element: class="fragment" -->
 * Don't use the code from within the code.  Write scripts to use the code. <!-- .element: class="fragment" -->

---

## Reusability: Retrofit

This one is the one I usually end up with.  I don't figure out that I need to
do it until I'm waist-deep in copy/pasted code (usually in a notebook) and I
miss a parameter to change or something.

When you find yourself in this type of situation, here's what I recommend:

 * Identify coarse pieces of code you use more than once <!-- .element: class="fragment" -->
 * Pull anything that can be reused by varying parameters into functions <!-- .element: class="fragment" -->
 * Put function definitions at the top of your file or notebook <!-- .element: class="fragment" -->
 * Find places where you have data or "state" and jam them into dictionaries or dataclasses <!-- .element: class="fragment" -->
 * Take all your functions and classes and put them in a different file <!-- .element: class="fragment" -->

---

## Reusability: Parameters

Compare these two pieces of code:

```python
plt.loglog(df['x'], df['y'], '-')
plt.xlabel("Stimulus Amount")
plt.ylabel("Response Function")
plt.savefig("resp.png")
```

and

```python
def make_plot(x, y, suffix = ""):
   plt.loglog(x, y, '-')
   plt.xlabel("Stimulus Amount")
   plt.ylabel("Response Function")
   plt.savefig("resp%.png" % suffix)
make_plot(df['x'], df['y'])
```

What are some of the pros and cons of these approaches?

---

## Reusability: Interactivity

We have seen how to utilize interactivity with the `@ipywidgets.interact` decorator.  For instance:

```python
@ipywidgets.interact(color = ["red", "green"])
def make_plot(color):
    plt.scatter(x, y, c = color)
```

We can also use `ipywidgets.interact` on functions that we have defined in
external files.  For instance:

```python
from my_script import make_plot

ipywidgets.interact(color = ["red", "green"])(make_plot)
```

But, this can be clunky.  You might prefer to write a wrapper function and use
the traditional `@ipywidgets.interact` method.

---

## Reusability: Interactivity

But can we expose interactivity from a function?  You bet!

```
def make_interactive_plot(df):
    @ipywidgets.interact(...)
    def _make_plot(...):
        ...
    return _make_plot
```

Now, we can have some *external* parameters to our function that are provided
to the internal parameters.  For instance, we could use this to set filter
values via interactivity on a dataframe that is set through a function
argument.

---

## Reusability: Flexibility

The biggest reason you might want to focus on reusability is so that you can
repeatedly make changes to something without having a long process of
reinvention and reimplementation.

This can be useful both for the project you're working on *now* as well as the
project you'll be working on *in the future*.

---

# Functions and Classes

You can think about functions as blocks of code that aren't meant to retain
anything between calls, and classes as things that progressively build or
modify some collection of "state" or data.

In this class (haha) we have mostly eschewed using classes, because we have
been focused on single-purpose outputs.  This is not the best long-term strategy!

When might we want one versus the other?

---

## Functions

Functions are the first tool in your toolbox when putting it all together.
Think of functions like [Mad Libs](https://en.wikipedia.org/wiki/Mad_Libs).

For instance:

<blockquote class="fragment" data-fragment-index=1>
<span class="fragment" data-fragment-index=2>It was a very </span>
<input type="text" value="[adjective]"/>
<span class="fragment" data-fragment-index=2>December morning in Matt's </span>
<input type="text" value="[adjective]"/>
<span class="fragment" data-fragment-index=2>data visualization class.  The students were all </span>
<input type="text" value="[adverb]">
<span class="fragment" data-fragment-index=2>checking their email while he </span>
<input type="text" value="[adverb]">
<span class="fragment" data-fragment-index=2>prattled on about something or another.</span>
</blockquote>

---

## Functions

You can define a function in python with `def`, as we have seen (implicitly)
before.  This can receive both "positional" and "named" arguments.  For
instance, in this function, there is one positional argument and there are two
named arguments:

```python
def my_function(filename, location = ".", write_header = False):
    ...
```

The `filename` argument is not optional, but both `location` and `write_header`
will use default values if not specified.

---

## Classes

We have mostly used classes in the context of traitlets, when we subclassed
`traitlets.HasTraits`.  (In much of my work, I use traitlets in a similar way!)
Classes can have state, and can implement so-called "dunder" methods to provide
special behavior.  The most important dunder method is `__init__`, which is
called when a class is created.

```python
class MyObject:
    def __init__(self, my_name):
        self.my_name = my_name

    def say_hello(self):
        print("Hello, this is %s" % (self.my_name))
```

Variables associated with the class will be stored and can be utilized within
an instance of an object.  Note that they do not *have* to be pre-declared.

---

## Classes: State and View

When dealing with classes, particularly for visualizations, it's important to
separate the "state" of the object from the "view" of that object.  As an
example, we can imagine having an object that constructs a complex interactive
visualization that it implements in the special (single-under) method
`_ipython_display_`.

```python
class ...
    def _ipython_display_(self):
        range_slider = ipywidgets.IntRangeSlider(...)
        ...
        container = ipywidgets.HBox([ ... ])
        traitlets.link((self, 'range'), (range_slider, 'value'))
        display(container)
```

Here, we make no assumptions about how many other "views" onto the object
exist, and instead we focus on linking the current view to it using traitlets
linkages.

---

# Libraries

At some point you might think, alright, maybe it's time I put this all together
into something I can use lots of times, and maybe somebody else will want to as well.

(That second part is optional, of course.)

How do we make that transition?

---

## Libraries: Layout

The first iteration of your "library" should just be a single `.py` file, next
to your application code.  So for instance, if you find yourself using the same
function over and over, toss it into its own file, import that file, and use
it.  That's it!

(When doing this in a Jupyter notebook, it's often best to either use the
deep-reloading capabilities of IPython or to restart your kernel when you edit
the file.)

But what if you want to use it in multiple projects?  That's where things get a bit trickier.

---

## Libraries: Layout

A basic python package looks something like this:

```
my_package/setup.py
my_package/README.md
my_package/MANIFEST.in
my_package/LICENSE
my_package/requirements.txt
my_package/my_package/__init__.py
my_package/my_package/file1.py
my_package/my_package/...
my_package/tests/test_mypackage.py
my_package/tests/...
my_package/docs/...
my_package/examples/...
```

The important parts here are `setup.py` and the `my_package` subdirectory.

---

## Libraries: Make this easy

This sure seems like a lot to keep straight, right?

Fortunately, there's a project that can really help out!
[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) is a templating
system that has been applied to making it easy to create python packages.

Let's try it out!

```bash
$ pip install --user cookiecutter
$ cookiecutter gh:audreyr/cookiecutter-pypackage
```

---

## Next Time

Next time, we start with presentations!
