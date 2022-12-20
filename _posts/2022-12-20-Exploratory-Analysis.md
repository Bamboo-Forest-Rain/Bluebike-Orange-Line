---
title: "Exploratory Analysis - Changes in Trend"
date: 2022-12-20
published: true
tags: [dataviz, hvplot, holoviews]
excerpt: "How did orange line shutdown contributed changed the travel pattern during the time?"
hv-loader:
  hv-chart-1: ["charts/ridership_line.html", "500"] # second argument is the height
  hv-chart-2: ["charts/stacked_bar_usertype.html", "500"]
  hv-chart-3: ["charts/averagestationridership.html", "500"]
toc: false
toc_sticky: false
---

# Looking at the Trend prior and during Orange Line Shutdown

This post will show examples of embedding interactive charts produced using [Altair](https://altair-viz.github.io) and [Hvplot](https://hvplot.pyviz.org/).

## Altair Example

Below is a chart of the incidence of measles since 1928 for the 50 US states.

<div id="altair-chart-1"></div>

This was produced using Altair and embedded in this static web page. Note that you can also display Python code on this page:

```python
import altair as alt
alt.renderers.enable('notebook')
```

## HvPlot Example

Lastly, the measles incidence produced using the HvPlot package:

<div id="hv-chart-1"></div>

## Notes

- See the [raw source code]([https://raw.githubusercontent.com/MUSA-550-Fall-2021/github-pages-starter/main/_posts/2021-11-29-measles-charts.md](https://raw.githubusercontent.com/MUSA-550-Fall-2022/github-pages-starter/main/_posts/2019-04-13-measles-charts.md)) of this post for details on how these charts were embedded.
- See the [lecture 13A slides](https://github.com/MUSA-550-Fall-2022/week-13/blob/main/lecture-13A.ipynb) for the code that produced these plots.

**Important: When embedding charts, you will likely need to adjust the width/height of the charts before embedding them in the page so they fit nicely when embedded.**
