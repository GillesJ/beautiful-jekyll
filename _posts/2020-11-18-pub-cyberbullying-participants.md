---
layout: post
title: "Publication: Automatic classification of participant roles in cyberbullying"
subtitle: "New publication of cyberbullying research in journal Natural Language Engineering."
description: Can we detect victims, bullies, and bystanders in social media text?"
permalink: pub-cyberbullying-participants
image: /img/bullying-participants-icon.jpg
tags: [cyberbullying, publication, paper, amica, research, machine learning, bullying detection]
published: true
---

Successful prevention of cyberbullying depends on the adequate detection of harmful messages. Given the impossibility of human moderation on the Social Web, intelligent systems are required to identify clues of cyberbullying automatically. Much work on cyberbullying detection focuses on detecting abusive language without analyzing the severity of the event nor the participants involved.
Automatic analysis of participant roles in cyberbullying traces enables targeted bullying prevention strategies. In this paper, we aim to automatically detect different participant roles involved in textual cyberbullying traces, including bullies, victims, and bystanders. We describe the construction of two cyberbullying corpora (a Dutch and English corpus) that were both manually annotated with bullying types and participant roles and we perform a series of multiclass classification experiments to determine the feasibility of text-based cyberbullying participant role detection. The representative datasets present a data imbalance problem for which we investigate feature filtering and data resampling as skew mitigation techniques. 

We investigate the performance of feature-engineered single and ensemble classifier setups as well as transformer-based pretrained language models (PLMs). Cross-validation experiments revealed promising results for the detection of cyberbullying roles using PLM fine-tuning techniques, with the best classifier for English (RoBERTa) yielding a macro-averaged -score of 55.84%, and the best one for Dutch (RobBERT) yielding an -score of 56.73%. Experiment replication data and source code are available at https://osf.io/nb2r3.

We have published new research as an extension from the [AMiCA project on cybersafety](https://amicaproject.be/).

{% include image.html
            img="/img/bullying-participants-cartoon-opt.jpg"
            title="The participants in bullying." 
            caption="Not very cyber, the participants in real-life bullying. Copyright KidsFrontier https://kids.frontiersin.org/article/10.3389/frym.2018.00014"%}
            
The article full text can be read for free in open-access [here](https://www.cambridge.org/core/journals/natural-language-engineering/article/automatic-classification-of-participant-roles-in-cyberbullying-can-we-detect-victims-bullies-and-bystanders-in-social-media-text/A2079C2C738C29428E666810B8903342) after an initial period.

Here's a video showing what the AMiCA project is all about:
<iframe width="560" height="315" src="https://www.youtube.com/embed/6Rv_C09lTLc" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>