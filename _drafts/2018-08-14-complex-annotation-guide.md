---
layout: post
title: Complex annotation for supervised machine learning: a practical guide.
subtitle: "A practical guide to dataset creation for supervised machine learning."
description: A time- and cost-saving practical guide to dataset creation.
permalink: complex-annotation-guide
image: /img/gilles-jacobs-econlp-acl18-icon.jpg
tags: [dataset, annotation, SENTiVENT, machine learning, text mining, NLP, event extraction]
published: false
---
What this post is: no collection but focus on annotation or data enhancement.
This post discusses the phases, the choices and issues involved in the different, proposed solutions, .

I draw on years of professional experience in commercial and academic research.
My specialty is NLP and information extraction, but the principles carry over to computer vision, robotics and any AI application requiring annotated data.
The example use-case is one of the most complex annotation schemes I have implemented yet: hierarchical and complex annotation structures with multiple interconnected annotation units for describing economic events in business-news.

Phases: guidelines, annotator sourcing, annotator training, inter-annotator study, annotation, curation.
Feedback measured by Annotation evaluation at all stages.

<!-- insert image of flow here  -->

Separate phases should be implemented separately in the annotation tool you are using either entirely or by using data subsets.
I also recommend implementing testing and production deployments.

## Goals: Cost⇩ Kappa⇧
The goal of planning is to keep the cost down and improve data quality (i.e., inter-annotator agreement).
There is a clear trade-off between data quality and time and money invested in preparation, training and annotation.

Apply proper project management and budgetting techniques as you would any other project.
Each project has its own budget but I advice you to prioritize quality of the data over quantity:
You cannot expect learning algorithms to generalize well, if even humans cannot agree on annotations.

## Phase 1: Guidelines
- What are Guidelines: what the annotators will use. Describe annotation units, information units, and how to distinguish between all types of units.
- Rules for annotation.
- Mention purpose and finality (downstream application).
- Clearly define the dataset purpose and the envisioned learning task in simple terms: this will help annotators disambiguate.

## 🔧 Pre-annotation: sense and non-sense
Automatic pre-annotation, also called bootstrapping.

## 🔧 Monitoring and evaluation
In line with SMART principles, annotation quality should be measurable: setting up on inter-annotator study.
Setting choosing an annotation evaluation method and setting it up an automated tool should be done as early as possible.
This evaluation metric will is used at each phase and iterative step.
It is used for gauging your guidelines and training

## Phase 2: Annotator sourcing
- hiring temp workers.
- domain expertise.
- crowd sourcing.
- pre-test: limited set when complex. Select best or set treshhold.

## Phase 3: Training annotators
cite interannotator quality paper: it is almost as good to have intensively trained and monitored.
