---
layout: page
title: About me
subtitle: Who am I and what do I do?
redirect_from:
  - "/about/"
  - "/info/"
---
Gilles Jacobs is currently researching text mining technologies for financial applications at Ghent University. He works on artificially intelligent systems for extracting fact and opinion from economic news in the SENTiVENT project. Before that, he created state-of-the-art systems for sentiment analysis, automated social media moderation, and several text classification applications. If you have any useful data trapped in unstructured text, Gilles’ bots will get it out.

He takes personal interest in blockchain technologies such as smart contracts and decentralized governance.

## Find me on:
<ul class="social-links">
  {% for social_link in site.social_links %}
    {% if social_link[1] != "" %}
      <li><a href="{{ social_link[1] }}" title="{{ social_link[0] }}">
        <i class="fa fa-{{ social_link[0] }}" aria-hidden="true"></i>{{ social_link[0] }}
      </a></li>
    {% endif %}
  {% endfor %}
</ul>
