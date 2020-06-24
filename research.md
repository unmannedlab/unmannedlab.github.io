---
layout: page
title: Research
---

{% assign sorted = site.research | sort: 'date' | reverse %}
{%for post in sorted %}
<article class="listpost">
  {% if post.thumbnail %}
    <a class="listpost-thumbnail" style="background-image: url({{post.thumbnail}})" href="{{post.url | prepend: site.baseurl}}"></a>
  {% else %}
  {% endif %}
  <div class="listpost-content">
    <h2 class="listpost-title"><a href="{{post.url | prepend: site.baseurl}}">{{post.title}}</a></h2>
    <p>{{ post.content | strip_html | truncatewords: 40 }}</p>
    <span class="listpost-words">{% capture words %}{{ post.content | number_of_words }}{% endcapture %}{% unless words contains "-" %}{{ words | plus: 250 | divided_by: 250 | append: " minute read" }}{% endunless %}</span>
  </div>
</article>
{% endfor %}

