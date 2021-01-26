---
layout: post
title: SENTiVENT Information Extraction for Economic News.
subtitle: "Introduction to my SENTiVENT PhD research project."
description: My research project SENTiVENT investigates text mining and machine learning for economic news.
permalink: sentivent-project
image: /img/sentiventlogo.jpg
tags: [SENTiVENT, machine learning, economic news, text mining, NLP, event extraction, sentiment analysis]
published: true
---
In this post I outline my PhD research in non-technical terms.
I explain the SENTiVENT project's goals and challenges.

![SENTiVENT logo](/img/sentiventlogotextnobackground.jpg){:class="img-responsive"}

# The SENTiVENT project
In 2017, my research proposal was approved and I was granted my fellowshop by the Research Foundation Flanders.
I started research at Ghent University and Solvay Business School/VUB.
The idea is to test and develop methods for getting useful information out of economic news text using the latest-and-greatest in machine learning.
The SENTiVENT name comes from two of the artificial intelligence methods used to achieve this:
SENTiment analysis and eVENT extraction.

{% include image.html
            img="/img/sentiment-and-event-example.svg"
            title="SENTiVENT example output"
            caption="Example output of the proposed SENTiVENT system." %}

## Economic Events
Event extraction tries to automatically get a schematic overview of a real-world occurrence of a certain type from text.
It summarizes an event and tells us who is involved in what event with which event properties.
This overview shows the event type and all persons or groups of people that participate in the event.
For example, if a sentence describes that one company bought another company it will find the parts of the text that talks about this event,
assign it the type "Acquisition" and fill in the "Acquirer" and "Target" participant roles with the names of the companies.

{% include image.html
            img="/img/sentiventeventextractionexample.jpg"
            title="Simplified event annotation example"
            caption="Simplified example sentence with annotations." %}

Events provide a schematic description of what is discussed in the text as long as they belong our event typology.
Our annotated typology currently consists of 18 carefully constructed event types each with subtypes and argument roles.

{% include image.html
            img="/img/type_treemap_matplot.svg"
            title="Event types and their frequency distribution in our dataset."
            caption="Event types and their frequency in our dataset." %}


The event annotations are enhanced with sentiment polarity tags, more about that in the next section.
But linking events to opens whole new avenues of research into to interaction between factual and opinion data in economic news: it allows us to automatically understand "common-sense" opinions related to events.
For example, a company missing a sales target is bad likely for investors, a missed target is thus commonly associated with bad investor sentiment.

{% include image.html
            img="/img/multiple-event-example.svg"
            title="Complete event annotation example"
            caption="Complete example sentence with two event annotations." %}

Automatically obtaining this information at scale is valuable because it summarizes what is going on with a company, stock or market without a human having to read every single newspaper.

## Investor Sentiment

In addition to factual event data, opinion data is also extracted in a fine-grained manner.
We annotated positive, negative and neutral investor sentiment as a seperate category, but also on-top of event annotations.

{% include image.html
            img="/img/sentiment-annotation-examples.svg"
            title="Standalone aspect-based sentiment extraction example."
            caption="Seperate fine-grained investor sentiment example." %}

In economic news, journalists give objective information on recent events while also discussing the implications of events in a subjective manner.
Sentiment analysis tries to automatically determine if the opinions expressed in a text are positive or negative.
When someone writes "Enchanting comedy with a nice sense of whimsy." about a movie, the sentiment analysis system marks the review as positive.
For economic news articles this is a lot harder to do than for movie reviews:
Economic journalists do not tend to express their opinions in such explicit terms as "enchanting" and "nice".
For instance, "Motorola sees an increase in revenue" implies a positive sentiment towards the company.
A human knows that more sales is good for a company because of their knowledge of how a business works.
Current systems do not handle common-sense implicit sentiments attached to certain events or situations.
Turns out implicit sentiment makes up half of the opinion expressions in economic news, so processing it is important for making financial technology applications.

I also want to go even further than just pointing to the positive, negative or neutral opinion in a text:
Wouldn't it be useful to know exactly which opinion is expressed about what part of a company or event?
This is called aspect-based sentiment analysis and automatically gives us an overview about what negative or positive opinion is expressed about what part of an event or entity.

# Applications
What is all this technology useful for?
Combining the "what, why, how, who and when" of factual events with subjective opinion data "how do people feel about what" unlocks a valuable data source at scale previously unavailable for a wide range of financial applications.
Extracting structured factual and opinion data from business news allows for many downstream applications in financial analysis and economic market studies.
- Asset price prediction: asset pricing, stock movement prediction rely traditionally on numerical key financial data. Performance of price prediction has shown to be enhanced by inclusion of fundamental data such as topics, events, and sentiment from news and social media text.
- Document retrieval: Find more relevant news articles or financial reports based on the events described in the text. Retrieved documents can be used for explaining movements in investment portfolio's. Document search can be made more efficient by restricting to particular events for economic event studies.
- Market sentiment: Which asset are currently showing bearish or bullish sentiment? And why?
- Summarization: Summarize the most important events related to an asset in a certain time period and show whether these is positive, negative or neutral opinion. 

