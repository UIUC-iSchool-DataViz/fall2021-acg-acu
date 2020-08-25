---
title: Lecture 1
layout: lecture
---
<!-- .slide: class="titleslide" -->

# Data Visualization

## Matthew Turk
## Fall 2020 - BOU/BOG

---

## Land Acknowledgment

Please see the Land Acknowledgment in the Syllabus.

[More information can be found on the Chancellor's
Website.](https://chancellor.illinois.edu/land_acknowledgement.html)

---
<!-- .slide: class="vertical_center" -->
## Basics

9:30AM-10:50AM on Tuesdays and Thursdays, online

Matthew Turk - `mjturk@illinois.edu`
Office Hours: By appointment

TA Mohammad Amanzadeh `amanzad2@illinois.edu`

https://uiuc-ischool-dataviz.github.io/fall2020-BOG-BOU/

---

## Online Accommodations

I will attempt to:

 * Livestream via Zoom (and possibly Twitch)
 * Monitor slack for questions and zoom for "raised hands"
 * Record lectures to post them at a later date

---

## Summary of Locations

 * Grades and assigmnets will be on [Moodle](https://learn.illinois.edu/).
 * Course repo is at [UIUC-iSchool-DataViz/fall2020-BOG-BOU](https://github.com/UIUC-iSchool-DataViz/fall2020-BOG-BOU/), automatically built at [uiuc-ischool-dataviz.github.io/fall2020-BOG-BOU/](https://uiuc-ischool-dataviz.github.io/fall2020-BOG-BOU). Lecture notes, notebooks, data and course info will be placed there.
 * Slack is the best place to ask questions: https://is445-fall2020.slack.com/

You are invited to clone the repo, fork and submit changes (typos, etc!), and
to use any information in it in the future.

---

## "Quiz"!

In advance of class today, you were asked to take a "quiz" online.  We're now going to break out into groups to do something with this.  The quiz was:

* What are the most memorable movies you saw over the last year?
* Do you prefer cats or dogs?
* How would you quantify your experience in visualization?
* How many hours do you spend online in classes each week?

---

## "Quiz"!

I'm going to send you into breakout rooms and give you about ten minutes.  

https://bit.ly/32mfIf7

On your group's number, visualize your results.

---

## Viz Systems We Will Cover

 * [matplotlib](https://matplotlib.org)
 * [vega-lite](https://vega.github.io/vega-lite)
 * [D3](https://d3js.org/)
 * [bqplot](https://bqplot.readthedocs.io)

There'll be a few more along the way, but these are the main ones.  Each touches on different aspects of visualization differently.

---

## Tools We Will Use

 * [GitHub](https://github.com/)
 * [Jupyter](https://jupyter.org/)
 * [Observable](https://observablehq.com/)

And we might use a few of:

 * [Iodide](https://iodide.io/)
 * [Glitch](https://glitch.com/)
 * [Colaboratory](https://colab.research.google.com/)

---

## Getting Python Setup

If you want to use your own Python setup, I recommend:

 1. Download Anaconda: [anaconda.com/download](anaconda.com/download)
 2. Ensure that Jupyterlab is installed and working
 3. Ensure that you have matplotlib, pandas and numpy installed and working.

We are working to provide a managed installation of Jupyter with the
appropriate Python stack available.

---

## Syllabus

 * Weeks 1-5: Basics of visualization
 * Weeks 6-10: Interactivity and Viz Types
 * Weeks 11-15: Platforms and dimensionality

notes:
This is a rough syllabus!  These are many of the topics we will cover, but
based on how the course proceeds and how folks respond, we may shorten or
lengthen different topics.

The organization here is designed to start out slow, dealing with how to
program python and javascript for visualization, understanding how data is laid
out, which operations we can apply to that data, and then moving on to
representing data in different ways.

---

## Weeks 1-5

 * How are files laid out?
 * What is in our operational palette?
 * Basics of using Javascript, Python, and writing JSON
 * Basic quantitative visualizations

---

## Weeks 6-10

 * Distributions of values in different dimensions
 * Simple interactivity 
 * Reactive programming
 * Colors, images
 * Comparisons across datasets

---

## Weeks 11-15

 * Scientific Visualization
 * Alternative visualization platforms
 * Dashboarding
 * Group projects

notes:
Toward the end of class we are going to have a slightly more free-form set of
discussion points.  Your final projects will be somewhat open-ended, requiring
more group work and collaboration than the preceding assignments.

---

# Class Mission

Your role as a _consumer_ of visualizations should change to also include the
perspective of a _producer_ of visualizations.

You should be comfortable reading _and_ writing imagery.

notes:
We will be discussing this as the semester goes on, but the principal outcome I
want you to take away from this class is understanding how to transform data
into its visual representation, and to take that understanding with you as you
observe visualizations presented to you.

By developing visualizations, you will grow to understand the choices that
influence those visualizations, and you will bring that with you while
consuming information visually.

---

## The Things I Want You To Take Away

 * You should know the basics of how to manipulate data -- aggregations,
   filterings, and other operations.
 * I want you to know _some_ of the packages that are out there to visualize
   data.  These will mostly be Python-based, with a couple in Javascript.
 * You won't learn how to use dashboarding software in detail.  Instead, we
   will talk about the different operations that go into dashboarding software.
 * By the end of the course, you will have had the opportunity to look at and
   build visualizations in several different domains and understand how to
   interpret, critique and improve them.

notes:
This course *will* teach you some things about how to code, how to build
visualizations, but we're going to focus much more on learning about how to
construct visualizations and why we make the choices that we do.  If we choose
one way to present data, does that convey information more readily?  Or does it
get in the way of the underlying meaning?

---

## Overview - Themes and Goals

1. What are the components of an effective visualization of quantitative data?
1. What tools and ecosystems are available for visualizing data?
1. What systems can be put in place to generate visualizations rapidly and with high-fidelity representation?

---

## Structure of Class

 * Tuesday Lecture: topic introduction, some lecturing
 * Thursday Lecture: some lecturing, greater focus on interactive discussion and code-along

This is my first time teaching this fully online, and it's *also* my first time
teaching it split in half!  So we might fiddle with the format as time goes on.

notes:
This structure will likely be deviated from during the course, but in general
we will start with lecture, take a break, then continue with collaborative or
hands-on exercises using group coding.

During the group coding, I might lead the class in some visualization in
Python, Javascript, or something else.  During this section, I expect that
students will *follow along* with what is going on -- typing in the specific
commands, and maybe even trying different things as we go.  It is not meant to
simply be a "performance" of coding, but instead an opportunity to learn.

---

## Grading

 * 40% Standard assignments in prose or code form
 * 30% Weekly visualization reports
 * 30% Final project

notes:
Your weekly assignments will take different forms.  The first assignment will
be exclusively prose and hand-writing, but subsequent assignments will be
either notebook (coding) based or prose-based as well.

The final project will be described later in class, but will take the form of a
group project that touches on coding as well as visual design.

---

## Weekly Visualization Reports

Every week, you are to turn in a visualization you have found in the media
(newspapers, magazines, online journalism) and a brief summary of something you like/don't like,
think is interesting, etc.

_These are meant to be easy points:_ No more than 2-3 sentences are needed in your description.

Each week, one of you will at random be asked to describe the visualization you picked to the class.

---

## Assignments (not necessarily weekly)

 * Weekly, assigned in class, collected following class
 * Prose assignments: deconstruction or analysis of a visualization or a dataset.
 * Coding assignments: Jupyter/JSMD/etc notebooks following step by step
   through collection and processing of data and the visualization of that
   data

---

## Plagiarism

 * Plagiarism is about copying ideas.
 * Cite all code you utilize from elsewhere.

notes:
When programming, I expect that you will do things like search on the internet
to find help with a given problem.  This is fine.

But, you *must* cite where any code snippets came from.  And you *must* note if
you are working with other people in the group!

Using snippets of code is fine -- but you may not copy large-scale amounts of
code from other work (for example, other visualizations) and pass it off as
your own.  Always cite, and be reasonable in what you utilize.

---

## Our tools

 * Python and Javascript
 * Jupyter and Jupyter notebooks on a Jupyterhub
 * The occasional usage of a shell such as bash
 * Javascript via Observable, or in console or webpage
 * Once in a while some git, and GitHub
 * Slack

notes:
You will be expected to write code in Python, and to learn the very basics of
Javascript.  Your projects may be turned in via git.  We will also utilize
Slack for class communication.

---

![](images/jh_arch.svg)

notes:
Jupyterhub is a software system for launching multiple independent notebooks
that can share access to data and installed software.  Ours is administered by
the iSchool.

---

## Jupyterhub Guidelines

 * [jupyterhub.ischool.illinois.edu](https://jupyterhub.ischool.illinois.edu/)
 * Please store your notebooks on- and off-site
 * You will have access to conda, etc, but I may rebuild images to add packages.

We are still working on getting some of the kinks out, but it should be usable!
We may be submitting assignments via `nbgrader` or via github classroom.

notes:
It is possible that your JupyterHub instance may be lost -- don't store mission
critical data there without a backup.  It should be possible to share data
between people on the system, but I won't pretend to know the right way to do
that.

---

## Assignment Flow

![](images/assignment_flow.png)

 1. Instructor "releases" an assignment
 1. Assignment appears in student "Assignments" tab
 1. Students "fetch" assignment, which copies it to their work directory
 1. When done, students "submit" assignment, which copies it to the
    instructor’s inbox
 1. Grades and feedback will be posted on Moodle.

notes:
We will be using `nbgrader` for notebook grading.  This will in general allow
you the opportunity to see *most* of the results of your grade prior to
submission.

---

## Slack

We will be sharing a slack channel with the online-only class, so feel free to
converse with them as well!

Team is at `is445-fall2020.slack.com` and we share it with the other section

 * `#general` : General announcements
 * `#is445-fall2020-bog-bou` : Specific questions/issues for *this* class.
 * `#random` : see a cool viz you want to share?  This is the place!

---

## Slack

 * Use the `@` sign appropriately: `@[person]`, `@here`, `@channel`
 * Web client, standalone client and mobile devices can access this team.
 * At the end of the semester, the team will be discontinued.
 * Please think carefully before direct messaging if you could ask in a public
   forum instead.
 * Conduct will be held to same standards as any educational venue.

As always, you can also post questions to the Moodle forum as well.

notes:
Please use slack as much as you need!  You can use it to share items and
articles with the class, to collaborate, to discuss and ask questions and get
feedback.  However, please do behave in a professional fashion.

---

## How do I access Slack?

 * Should have received instructions in welcome email
 * Ask me after class or send me an email with _your_ email

---

## Github

 * Course repo is at [UIUC-iSchool-DataViz/fall2020-BOG-BOU](https://github.com/UIUC-iSchool-DataViz/fall2020-BOG-BOU/)
 * Automatically built to [uiuc-ischool-dataviz.github.io/fall2020-BOG-BOU/](https://uiuc-ischool-dataviz.github.io/fall2020-BOG-BOU/)
 * Copy the notebooks to your directory before using them.
 * Supplemental materials can be found at [UIUC-iSchool-DataViz/support-files](https://github.com/UIUC-iSchool-DataViz/support-files)

---

## Choose Your Own Adventure

(Have any of you ever "read" a [CYOA](https://en.wikipedia.org/wiki/Choose_Your_Own_Adventure) book?)

There are probably at least three pathways to consider in this course:

 1. "I am here to get better at programming and play with viz platforms"
 1. "I am thinking about a career in data viz."
 1. "I don't know/I am new to programming and I want to focus on that."

---

## Choose Your Own Adventure

**"I am here to get better at programming and play with viz platforms"**

Strategy:

 * Look at the code and the extended examples
 * Do the Javascript parts

---

## Choose Your Own Adventure

**"I am thinking about a career in data viz."**

Strategy: 

 * Look at the code and the extended examples
 * Do the Javascript parts
 * Read the optional texts and documents

---

## Choose Your Own Adventure

**"I don't know!"** or **"I am new to programming and I want to focus on that."**

Strategy: 

 * Look at the code, focus heavily on Python
 * Read the prep notebooks before class!
 * Do the Javascript parts _in class_ and build on them for any homework
 * Come back to the optional texts and documents after the course is over

---

## On to visualization!

---

<!-- .slide: data-background-image="https://thumbnails-visually.netdna-ssl.com/what-is-data-visualization_50290b9240bd8_w1500.png" data-background-size="contain" -->

notes:
there is a *huge* overlay of topics that cover data viz - from the neurology of how your prefrontal cortex process information, to how humans process storytelling, to data analytics, and color theory and the list goes on!

---

### Data Viz is a big topic

<!-- .slide: data-background-image="images/diagram_for_gradclass.png" data-background-size="auto 75%" -->

notes:
this is another way of looking at this.

here is the overall diagram of the things we'll cover in this class -- you can see there are a lot of topics from different areas and they are all interconnected.


---

## This week

 * What is a visualization?
 * Why do we visualize?
 * What types of data do we visualize?
 * How do we visualize?

notes:
We're going to start out at a very high-level, discussing why we choose to
visualize versus other types of representation, what types of data, and how we
might do it.

---

## What is a visualization?

 > Computer-based *visualization* systems provide visual representations of
 > datasets designed to help people carry out tasks more effectively.

<p class="right">
Tamara Munzer, <i>Visualization Analysis & Design</i>
</p>

<div class="fragment" data-markdown=true>

---

## What is a visualization?

Data Viz is **task-oriented**.

<!-- .slide: data-background-image="https://www.savalli.us/BIO370/Anatomy/AnatomyImages/TyrannosaurusSkeletonLabel.jpg" data-background-size="auto" -->

notes:
I really like this definition because it gives us a sense of purpose - i.e. that our visualization must help a human with a task that has to do with data.

here for example, we might want to know the labels of bones or how they fit together

---

## What is a visualization?

Artistic representations are used to convey emotions:

<!-- .slide: data-background-image="https://i.etsystatic.com/5150206/r/il/fe175b/1823842266/il_570xN.1823842266_b9y3.jpg" data-background-size="auto" -->

---

## What is a visualization?

Movies, comics, or other cinematic representations are used to tell stories:

<!-- .slide: data-background-image="http://www.dinopit.com/wp-content/uploads/2012/08/funny-dinosaur.jpg" data-background-size="auto" -->

notes:
we will be using artistic concepts and elements of storytelling, BUT that is not our focus -- here we are TASK oriented.


---

# Why?

(Or rather, why _wouldn't_ we visualize?)

notes:
Not everything suits itself to visualization -- and part of the reason for that
is the necessary reductionism that visualization can require.

---

<iframe width="1024" height="576"
src="https://www.youtube.com/embed/In72QAQJ1tY?rel=0" frameborder="0"
allow="encrypted-media" allowfullscreen></iframe>

notes:
"There are lots of thing you can compare on a graph / Like who is the shortest
or the tallest giraffe / You can chart how much you walk / How much that you
laugh / There are lots of things you can compare on a graph"

"But the one thing you can't chart / Is how you feel in your heart"

---

<!-- .slide: data-background-image="images/fov.svg" data-background-size="contain" -->

notes:
Visual information is communicated through our eyes, where it is processed.  At
the most basic level, we can see a range of about 210 degrees horizontally with
one or both eyes.  The region that is covered by both ("binocular") is about
114 degrees in extent.

You can only cram so much information into the human eye.

---

![](https://upload.wikimedia.org/wikipedia/commons/2/27/AcuityHumanEye.svg)

By Vanessa Ezekowitz [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0), via Wikimedia Commons

notes:
When we think about visual communication of information, we *must* think about
how human physiology interacts with that communication.

Also, fair warning: I'm not a medical doctor.

This diagram shows the visual acuity of a "standard" human eye, as a function
of angular distance from the fovea.  We have to think about this in
*conjunction* with our field of view.

---

## Your brain does interpolation

<!-- .slide: data-background-image="images/dotsillusion.jpg" data-background-size="auto 50%" -->

There are 12 dots, can you count them all at the same time?


---

## Your brain does interpolation

<!-- .slide: data-background-image="images/blindspotcross.png" data-background-size="auto" -->

1. Look at the cross
2. Close left eye, keep looking at the cross
3. Slowly move your head toward & away from screen until dot disappears

---

## Your brain does interpolation

Even despite these oddities, the visual cortex is great for information transfer!  

Your visual cortex is processing information from different parts of this page **at the same time** -- it can do impressive things very quickly!

---

## Can you spot the difference?

<!-- .slide: data-background-image="https://www.rd.com/wp-content/uploads/2018/01/Can-You-Spot-the-10-Differences-in-This-Picture-_585659516-Ksenya-Savva.jpg" data-background-size="auto 75%" -->

notes:
compare this to how long it would take to spot differences in 2 songs - you'd have to listen to both songs (probably more than once) and compare after!  This would be sequential rather than parallel data transfer!

---

## Try it with sound

* [Moonlight Sonata, 1](https://soundcloud.com/redreapergrell/beethoven-moonlight-sonata)
* [Moonlight Sonata, 2](https://soundcloud.com/user-37232775/sets/beethoven-moonlight-sonata)

Try doing the same thing with these on your own!

notes:
time this activity, give them 1.5 minutes

ask: how long did this take you?  How many differences were there?
I spotted tempo as one (but you can cheat by looking at the timer on the bottom!)

Also, you can look at how different each of the sound-bars are on each link and see how different the music looks visually!

---

## Why visualize?

Visualization **augments** human data analysis capabilities:

 * It enhances our ability to pattern find
 * It allows us to summarize data quickly
 * It allows us to search our data quickly


---


## I need a volunteer!

notes:
(This part is a bit of a stunt.  Sorry.)

---

*Read these numbers:*

| | |
|:-|-:|
| 2007-01-01 | 14233.2 |
| 2007-04-01 | 14422.3 |
| 2007-07-01 | 14569.7 |
| 2007-10-01 | 14685.3 |
| 2008-01-01 | 14668.4 |
| 2008-04-01 | 14813.0 |
| 2008-07-01 | 14843.0 |
| 2008-10-01 | 14549.9 |
| 2009-01-01 | 14383.9 |

notes:
See what I mean?  It's a stunt.  You're supposed to hear these, or look at the
numbers, and not have as clear an impression.  It also takes a lot longer.

---

![FRED Graph](images/fredgraph.png)

notes:
You might immediately notice a few things about this image, but one item that
we will talk about as class goes on is that often visualizations can have a
consistent style.  FRED in particular has a "branding" that is quite obvious,
even without the logo.

---

## Anscombe's Quartet

<!-- .slide: data-background-image="https://upload.wikimedia.org/wikipedia/commons/thumb/e/ec/Anscombe%27s_quartet_3.svg/1280px-Anscombe%27s_quartet_3.svg.png" data-background-size="auto 50%" -->

This famous example shows 4 datasets with the exact same mean, variance and correlation coefficient.

Statistics can be useful, but visualization generated context!

---

## Anscombe's Quartet -- Dinosaur Edition

<!-- .slide: data-background-image="https://miro.medium.com/max/600/1*W--cGoA3_n2ZlU6Xs4o2iQ.gif" data-background-size="auto 50%" -->

Statistics can be useful, but visualization generated context!

---

# Who are you visualizing for?

* For yourself?
* For a peer?
* For someone else?

notes:
*Whenever* you build a visualization you need to think about the context that
you can assume on the part of your viewer.

---

# Tenet 1:

"Visualizing data" is not a strict subset of "making an image."

 * Collection of the data
 * Organization of that data
 * Representation of that data

notes:
We will approach visualization as encompassing several different stages in the
collection, organization and representation of data.

---

# Tenet 2:

We tell lies to visualize, but we _must_ be honest.

 * No representation is going to convey the entire complexity of a dataset.
 * Some representations are better than others.

---

# Tenet 2:

"The Principle of Proportional Ink" -- [callingbullshit.org](https://callingbullshit.org/)
<!-- .slide: data-background-image="images/proportionalInk.png" data-background-size="auto 50%" -->

notes:
So let's first talk about how misleading visualizations can be. This 3D pie chart violates the "principle of proportional ink" which states that the number of pixels that represent a value should be proportional to the value. With the raised edge on the pie chart, the blue wedge gets way more ink than it deserves and you get a disproportionate sense of value.

---

# Tenet 2:

"Spurious Correlations" -- [tylervigen.com](https://tylervigen.com/)

<!-- .slide: data-background-image="images/spurious.png" data-background-size="auto 50%" -->

notes:
you can have a lot of absurd fun with data - but when data is presented in a visualization, people often believe the authority of it even if it's outlandish. 

This website has some good ideas of where to find sample datasets for upcoming homework assignments too!

---

<!-- .slide: data-background-image="images/barCharts.png" data-background-size="contain" -->

notes:
Each of these bar chart examples are meant to show the same data. But you can see how they're a bit problematic.

---

<!-- .slide: data-background-image="images/gunDeaths.jpg" data-background-size="contain" -->

notes:
Now here's an example that's more brazen. I'll give you a minute to analyze this and tell me what's wrong with this graph.

Some people will claim the Y-axis should always start from the bottom - at zero - to avoid confusion.

---

<!-- .slide: data-background-image="images/keelingCurve.svg" data-background-size="contain" -->

notes:
however, the Keeling Curve is an interesting counter-argument. This is the famous graph that was the original evidence for global warming, showing the rate at which atmospheric carbon dioxide was growing. 

Does anyone know why it's generally accepted to show the y-axis like this, without it starting at the zero axis?

---

<!-- .slide: data-background-image="images/hearts_battery.svg" data-background-size="contain" -->

notes:
here are a few more representations of data that you've probably run into!


---

<!-- .slide: data-background-image="images/hearts_battery.svg" data-background-size="contain" -->

---

<!-- .slide: data-background-image="images/battery.svg" data-background-size="contain" -->

<div style="padding-top: 15em;" data-markdown=true>

 1. Sensors read the current "fill" of the battery
    * Analog / digital conversion
    * Normalized with respect to expected "full"
 1. This is then scaled to a percentage
 1. The battery image is filled from left to right
 1. The image is then rasterized and displayed

</div>

---

<!-- .slide: data-background-image="images/hearts_bw.svg" data-background-size="contain" -->

 * Some fixed maximum amount of damage
 * Each time damage is taken, decrement
 * Each time damage is reversed, increment
 * Display number of hearts as appropriate

---

2 out of 3 "points"

<!-- .slide: data-background-image="images/hearts_color.svg" data-background-size="contain" -->

---

<!-- .slide: data-background-image="images/hearts_color.svg" data-background-size="contain" -->

![](images/doom_status.png)

---

<!-- .slide: data-background-image="images/stitch_bg.png" data-background-size="contain"-->

notes:
This is a screenshot from the movie "Lilo and Stitch" where the little girl Lilo is graphing how much evil is in the alien Stitch. It borrows from a familiar visual - the thermometer. But how could this visualization be misinterpreted? How is it different from a thermometer?

---

<!-- .slide: data-background-image="images/stitch_nobg.png" data-background-size="contain"-->

notes:
The angle can be misleading. So can the relative width of the head vs the feet. The surface area is not consistent from top to bottom. Also there are empty areas in the mouth and eyes!


---

<!-- .slide: data-background-image="images/stitch_nobg_tilted.png" data-background-size="contain"-->

notes:
If we rotate the image so that the red liquid is level, do we get a different impression for how much bad is in Stitch?

---

<iframe width="1024" height="576"
src="https://www.youtube.com/embed/D-uBv6jB7r0" frameborder="0"
allow="autoplay; encrypted-media" allowfullscreen></iframe>

---

## Honesty

Our choices must be:

 * Deliberate
 * Informed
 * Motivated
 * Justifiable

---

## Election Maps

Mark Newman of the University of Michigan has created visualizations of the
election maps from several of the most recent elections.  For more information
and context, see his page http://www-personal.umich.edu/~mejn/election/2008/ .

 * [Map 1](http://www-personal.umich.edu/~mejn/election/2008/statemapredbluer1024.png)
 * [Map 2](http://www-personal.umich.edu/~mejn/election/2008/statepopredblue1024.png)
 * [Map 3](http://www-personal.umich.edu/~mejn/election/2008/countymapredbluer1024.png)
 * [Map 4](http://www-personal.umich.edu/~mejn/election/2008/countymappurpler1024.png)
 * [Map 5](http://www-personal.umich.edu/~mejn/election/2008/countycartpurple1024.png)

notes:
These are great, but some criticisms might be that the color red is more apparent to the human eye than the color blue. And in the population-to-area adjusted maps, it's difficult to read for people used to geographic accuracy.

Map1 - this is just a geographical map of red and blue

Map2 - cartogram weighted by population (note, NOT by electoral college population)

Map3 - election results by county

Map4 - percentage of votes by county

Map5 - percentage of votes by county, weighted by population

---

## This week: Wrap-up

 1. We visualize to change how we understand things.
 1. We visualize data for ourselves, for our peers, and for others.
 1. Visualization is a series of steps that we take to produce a different
    representation of data.

---

## Assignment 1

 * Identify three visualizations in pop culture -- *not* academic literature.
   This could be, for instance, from:
   * Movies / TV / Music videos
   * Everyday life
   * Advertisements
 * Describe each one in detail
   * Where did the data come from?
   * Is the data quantitative, qualitative, categorical, etc?
   * How was the data processed before being displayed?
   * What method was used to display that data?
 * Replicate the visualization with different, but similarly “shaped,” data
   * By hand is acceptable
   * Computational methods should include source code
