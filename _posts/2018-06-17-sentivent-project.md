---
layout: post
title: SENTiVENT Text Mining for Economic News.
subtitle: A layman's introduction to my PhD research project.
description: My research project SENTiVENT investigates text mining and machine learning for economic news.
permalink: sentivent
image: /img/sentiventlogo.jpg
tags: [SENTiVENT, machine learning, economic news, text mining, NLP, event extraction, sentiment analysis]
published: true
---
In this post I outline my PhD research in non-technical terms.
I explain the SENTiVENT project's goals and challenges.

![SENTiVENT logo]({{ "/img/sentiventlogoname.jpg" | absolute_url }})

# SENTiVENT
In 2016, I wrote a research proposal to the Research Foundation Flanders.
In 2017, the PhD research project was granted and I started research at Ghent
University and Solvay Business School/VUB.
The idea is to test and develop methods for getting useful information out of
economic news text using the latest and greatest in machine learning.
The SENTiVENT name comes from two of the artificial intelligence methods used to achieve this:
SENTiment analysis and eVENT extraction.

![SENTiVENT output]({{ "/img/sentiventoutputexample.jpg" | absolute_url }})

# Event extraction
Event extraction tries to automatically get a schematic overview of a real-world occurrence of a certain type from text.
It summarizes an event and tells us who is involved in what event with which event properties.
This overview shows the event type and all persons or groups of people that participate in the event.
For example, if an article describes that one company bought another company it will find the parts of the text that talks about this event,
assign it the type "Acquisition" and fill in the "Acquirer" and "Target" participant roles with the names of the companies.
![Event extraction example]({{ "/img/sentiventeventextractionexample.jpg" | absolute_url }})
These event schema provides a description of what is discussed in the text.
Automatically getting this information is valuable because it summarizes what is going on with a company, stock or market without a human having to read every single newspaper.

# Sentiment analysis
In economic news, journalists give objective information on recent events while also discussing the implications of events in a subjective manner.
Sentiment analysis tries to automatically determine if the opinions expressed in a text are positive or negative.
When someone writes "Enchanting comedy with a nice sense of whimsy." about a movie, the sentiment analysis system marks the review as positive.
For economic news articles this is a lot harder to do than for movie reviews:
Economic journalists do not tend to express their opinions in such explicit terms as "enchanting" and "nice".
For instance, "Motorola sees an increase in revenue" implies a positive sentiment towards the company.
You know that more sales is good for a company because of your knowledge of how the business world works.
Current systems do not handle common-sense implicit sentiments attached to certain events or situations.
Turns out implicit sentiment makes up half of the opinion expressions in economic news, so processing it is important for making financial technology applications.

I also want to go even further than just pointing to the positive, negative or neutral opinion in a text:
Wouldn't it be cool to know exactly which opinion is expressed about what part of a company or event?
This is called aspect-based sentiment analysis and automatically gives us an overview about what negative or positive opinion is expressed about what part of an event or entity.

# Applications
What is all this technology useful for?
