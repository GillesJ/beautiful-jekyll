---
layout: page
title: About me
subtitle: Who am I and what do I do?
redirect_from:
  - "/about/"
  - "/info/"
---
Gilles Jacobs is currently researching text mining technologies for financial applications at Ghent University. He works on artificially intelligent systems for extracting fact and opinion from economic news in the SENTiVENT project. Before that, he created state-of-the-art systems for sentiment analysis, automated social media moderation, and several text classification applications. If you have any useful data trapped in unstructured text, my bots will get it out.

He takes personal interest in blockchain technologies such as smart contracts and decentralized governance.

## Contact
You can message me by using the email form below:

<form method="POST" id="formaction">
  <input name="_replyto" placeholder="Your email" type="email"><br />
  <input name="_subject" placeholder="Message subject" /><br />
  <textarea name="message" placeholder="Your message"></textarea><br />
  <button type="submit">Send</button>
  <input type="hidden" name="_next" value="//jacobsgill.es/thanks.html" />
  <input type="text" name="_gotcha" style="display:none" />
  <input type="hidden" name="_format" value="plain" />
</form>
<script>
    var contactform =  document.getElementById('formaction');
    contactform.setAttribute('action', '//formspree.io/' + 'gilles' + '@' + 'jacobsgill' + '.' + 'es');
</script>

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
