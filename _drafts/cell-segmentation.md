---
layout: post
title:  "Cell Segmentation"
date:   2020-04-28 00:44:42 -0700
categories: thoughts
tags: [cs, machine learning]
author: "Brandon"
---

I will be revisiting a few problems I encountered during my time in the lab. Primarily, cell activity identification. I want to take it slowly so this project may take several weeks, but hopefully by the end of it, I will have learned/developed a more effective approach.

<b>First off, the problem:</b> The overarching goal is to accurately identify and label cells even with varying conditions. I have previously encountered three scenarios.
<img src="{{ 'assets/img/cell_scenarios.png' | relative_url }}">
* Scenario 1 is a static plane with a large number of cells. The main difficulty is the high variance in cell intensity and large clusters.
* Scenario 2 is a static plane containing a portion of a dendrite. Activity is located either on the stem or the spine, however, there is a lot of noise throughout.
* Scenario 3 is a dynamic video with neuron activity changing across time.

<b>My Previous Approaches:</b>

Threshold + Watershed
<img src="{{ 'assets/img/cell_watershed.png' | relative_url }}">
First, set an intensity threshold to capture
<img src="{{ 'assets/img/cell_deltaf.png' | relative_url }}">
Side note. Most of my previous work was done in MATLAB. I'll be experimenting with python this time.
