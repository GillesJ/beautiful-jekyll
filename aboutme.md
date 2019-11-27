---
layout: page
title: About me
redirect_from:
  - "/about/"
  - "/info/"
---
Gilles Jacobs is currently researching text mining technologies for financial applications at Ghent University and Solvay Business School/VUB. He works on artificially intelligent systems for extracting fact and opinion from economic news in the SENTiVENT project. Before that, he created state-of-the-art systems for sentiment analysis, automated social media moderation, and several text classification applications. If you have any useful data trapped in unstructured text, my bots will get it out.

He takes personal interest in blockchain technologies such as smart contracts and decentralized governance.

## Contact
You can message me by using the email form below:

<form action="https://formspree.io/mzbzzggb" method="POST">
  <label>
    Your email:
    <input type="text" name="_replyto">
  </label>
  <label>
    Your message:
    <textarea name="message"></textarea>
  </label>
  <button type="submit">Send</button>
</form>

If you need more secure and confidential communication you can find [my PGP public encryption key on keybase](https://keybase.io/gillesjacobs).

## Find me on:
<ul class="social-links">
  {% for social_link in site.aboutme-social-links %}
    {% if social_link[1] != "" %}
      <li><a href="{{ social_link[1] }}" title="{{ social_link[0] }}">
        {{ social_link[0] }}
      </a></li>
    {% endif %}
  {% endfor %}
</ul>
