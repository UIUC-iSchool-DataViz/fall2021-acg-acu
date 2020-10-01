---
title: Putting it Together
layout: lecture
tags:
  - platforms
  - vega-lite
  - web
  - python
  - javascript
  - github-pages
description: >-
  We talk about putting together the process of prototyping a visualization, preparing data for it, and then putting that visualization on a website.
---

## Today

 1. Embedding vega-lite
 2. Publishing github pages
 3. Preparing our building dataset

---

## Embedding vega-lite

You must include the correct javascript includes to embed vega-lite in the `&lt;head&gt;` section of your HTML.  For instance:

```html
&lt;script src="https://cdn.jsdelivr.net/npm/vega@5.16.1"&gt;&lt;/script&gt;
&lt;script src="https://cdn.jsdelivr.net/npm/vega-lite@4.16.2"&gt;&lt;/script&gt;
&lt;script src="https://cdn.jsdelivr.net/npm/vega-embed@6.12.2"&gt;&lt;/script&gt;
```

---

## Embedding vega-lite

Embedding vega-lite requires identification of a DOM element within which to place your visualization as well as providing the specification of that visualization.  For example, we can define a `&lt;div&gt;` like so:

```html
&lt;div id="viz"&gt;
&lt;/div&gt;
```

And then we can utilize the `vegaEmbed` function like so:

```javascript
vegaEmbed('#viz', vlSpec);
```

---
