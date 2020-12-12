---
layout: post
title: "Extracting Fine-Grained Economic Events from Business News."
subtitle: "New publication and presentation in economic NLP research."
description: "Can we extract what, who, when, how much is happening in business news?"
permalink: fnpfns-economic-events
image: img/sentiventlogo.jpg
tags: [economic events, financial nlp, sentivent, presentation, coling2020, research, machine learning]
published: true
---

I will be presenting new work on economic event extraction at the FNP-FNS workshop @ COLING2020.
TL;DR: We created a dataset and system that automatically gets "what, who, when, how much, and why" is happening from economic news text.
Turns out this is quite a difficult task, even with using the latest techniques in deep learning!

You can view my presentation here:
<iframe width="560" height="315" src="https://www.youtube.com/watch?v=iKF7hUMdCw8" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Read the paper at [this link](https://www.aclweb.org/anthology/2020.fnp-1.36.pdf).

Based on a recently developed fine-grained event extraction dataset for the economic domain,we present in a pilot study for supervised economic event extraction.
We investigate how a state-of-the-art neural model for event extraction performs on the trigger and argument identification andclassification.
While F1-scores of above 50% are obtained on the task of trigger identification,we observe a large gap in performance compared to results on the benchmark ACE05 dataset.
We show that single-token triggers do not provide sufficient discriminative information for a fine-grained event detection setup in a closed domain such as economics, since many classes have alarge degree of lexico-semantic and contextual overlap.