---
layout: page
title: All News
permalink: /allnews/
---

<div>
{% assign sorted = site.data.news_list | sort: "date" | reverse %}
{% for article in sorted %}
    <h2 style="font-weight: 600">{{ article.date | date_to_string }}</h2>
    <h3>{{ article.headline }}</h3>
    {% if article.content.size > 1%}
        <ul>
        {% for item in article.content %}
            <li>{{item}}</li>
        {% endfor %}
        </ul>
    {% else %}
        <p>{{ article.content }}</p>
    {% endif %}
{% endfor %}
</div>