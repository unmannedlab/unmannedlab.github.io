---
layout: page
title: Research
---

{% assign sorted = site.research | sort: 'date' | reverse %}
{%for post in sorted %}
<article class="listpost" href="{{post.url | prepend: site.baseurl}}">
  {% assign wordcount = post.content | number_of_words %}
  {% if wordcount > 75 %}
    {% if post.thumbnail %}
      <a class="listpost-thumbnail" style="background-image: url({{post.thumbnail}})" href="{{post.url | prepend: site.baseurl}}"></a>
    {% endif %}
    <div class="listpost-content">
        <h2 class="listpost-title"><a href="{{post.url | prepend: site.baseurl}}">{{post.title}}</a></h2>
        <p>{{ post.content | strip_html | truncatewords: 75 }} 
        <span class="listpost-words" >{% capture words %}{{ post.content | number_of_words }}{% endcapture %}{% unless words contains "-" %}{{ words | plus: 250 | divided_by: 250 | append: " minute read" }}{% endunless %}</span> </p>
      </div>
  {% else %}
    {% if post.thumbnail %}
      <a class="listpost-thumbnail" style="background-image: url({{post.thumbnail}})"></a>
    {% endif %}
      <div class="listpost-content">
        <h2 class="listpost-title">{{post.title}}</h2>  
        <p>{{ post.content | truncatewords: 75 }}</p>
      </div>
  {% endif %}  
</article>
{% endfor %}

