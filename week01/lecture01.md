---
title: Class Introduction
layout: lecture
tags:
  - overview
  - concepts
description: >-
  The syllabus for the course, along with discussions about "what"
  visualizations are, and how to orient yourself in the course.
date: 2020-08-25
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

 * Grades and assignments will be on [Moodle](https://learn.illinois.edu/).
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
   filtering, and other operations.
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
