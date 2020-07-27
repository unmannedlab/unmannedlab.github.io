---
layout: page
title: All News
permalink: /allnews/
---

<div>
{% for article in site.data.news_list %}
    <h3>{{ article.date }}</h3>
    <h4>{{ article.headline }}</h4>
    <p>{{ article.content }}</p>
{% endfor %}
</div>