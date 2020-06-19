---
layout: page
title: People
permalink: /people/
---

<style>
    * {
      box-sizing: border-box;
    }

    figure {
        display: inline-block;
        vertical-align: top;
        margin: 60px; /* adjust as needed */
    }
    figure img {
        vertical-align: top;
        width: 200px;
        /* height: 200px; */
    }
    figure figcaption {
        display: table;
        width: 200px;
        text-align: center;
        font-size: 18px;
        line-height: 1.5;
        font-weight: 200;
    }
</style>


# Principal Investigator

<figure>
    <a href="https://engineering.tamu.edu/mechanical/profiles/saripalli.html">
        <img src="images/sri2.jpeg" alt='missing' /> 
    </a> 
    <figcaption>
        <a href="https://engineering.tamu.edu/mechanical/profiles/saripalli.html"> Srikanth Saripalli </a><br>
    </figcaption>
</figure>

# Graduate Students


{% for people in site.people %}
{% if people.type == "PhD" %}
<figure>
    {% if people.show_profile %}
        <a href="{{people.url}}">
            <img src="images/{{people.image}}" alt='missing' /> 
        </a> 
        <figcaption>
            <a href="{{people.url}}"> {{people.title}}</a><br>
            {{people.type}} Candidate
    </figcaption>
    {% else %}
        <img src="images/{{people.image}}" alt='missing' /> 
            <figcaption>
                 {{people.title}}<br>
                {{people.type}} Candidate
            </figcaption>
    {% endif %}


</figure>
{% endif %}
{% endfor %}


{% for people in site.people %}
{% if people.type == "M.S." %}
<figure>
    {% if people.show_profile %}
        <a href="{{people.url}}">
            <img src="images/{{people.image}}" alt='missing' /> 
        </a> 
        <figcaption>
            <a href="{{people.url}}"> {{people.title}}</a><br>
            {{people.type}} Candidate
    </figcaption>
    {% else %}
        <img src="images/{{people.image}}" alt='missing' /> 
            <figcaption>
                 {{people.title}}<br>
                {{people.type}} Candidate
            </figcaption>
    {% endif %}
</figure>
{% endif %}
{% endfor %}


<h1><a href="/alumni"> Alumni & Former Students </a></h1>