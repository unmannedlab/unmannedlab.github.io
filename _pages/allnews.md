---
layout: page
title: All News
permalink: /allnews/
---

<div>
{% assign sorted = site.data.news_list | sort: "date" | reverse %}
{% for article in sorted %}
    <h3>{{ article.date | date_to_string }}</h3>
    <h4>{{ article.headline }}</h4>
    <p> {{ article.content }}</p>
{% endfor %}
</div>