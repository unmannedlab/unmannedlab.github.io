---
layout: page
title: People
permalink: /people/
---

<link rel="stylesheet" type="text/css" href="/assets/css/people.css">

# Faculty


 <div class="flex-container">
    <div class="person">
        <a class="person-thumbnail" style="background-image: url(images/sri2.jpeg); min-height: 260px;" href="https://engineering.tamu.edu/mechanical/profiles/saripalli.html"></a>
        <div class="person-title">
            <h2 class="person-name"><a href="https://engineering.tamu.edu/mechanical/profiles/saripalli.html">Dr. Srikanth Saripalli</a></h2>
            <p>Professor</p>
        </div>
    </div>
</div> 

<br>

# Graduate Students

<div class="flex-container">
{% for people in site.people %}
    {% if people.show_profile %}
        <div class="person">
            <a class="person-thumbnail" style="background-image: url(images/{{people.image}}); background-size: 200px 200px;" href="{{people.url}}"></a>
            <div class="person-title">
                <h2 class="person-name"><a href="{{people.url}}">{{people.title}}</a></h2>
                <p>{{people.type}}</p>
            </div>
        </div>
    {% else %}
        <div class="person">
            <img src="images/{{people.image}}" class="person-thumbnail">
            <div class="person-title">
                <h2 class="person-name">{{people.title}}</h2>
                <p>{{people.type}}</p>
            </div>
        </div>
    {% endif %}
{% endfor %}
</div>


<br>
<h1><a href="/alumni/"> Alumni & Former Students </a></h1>
