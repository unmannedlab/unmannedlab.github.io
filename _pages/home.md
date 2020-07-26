---
layout: default
permalink: /
---

<style>
    .carousel{
        max-width: 640px;
        margin: auto;
    }
    /* Grid overrides */
    .col-sm-1, .col-sm-2, .col-sm-3, .col-sm-5, .col-sm-6,
    .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12 {
        padding-left: 16px;
        padding-right: 16px;
    }

    /* Grid overrides */
    .col-sm-4 {
        padding-left: 26px;
        padding-right: 26px;
    }
</style>

<div class="row">
    <div id="homeid" class="col-sm-8">
        <h1>Welcome to the Unmanned Systems Lab</h1>
        <p> 
            Our research focuses on Mapping, Localization, Guidance, Navigation and Control for developing autonomous ground and aerial vehicles. 
            Our projects span from algorithmic design and implementation to field experimentation of aerial and ground robots.  
            A specific goal is field deployment of such vehicles in relevant environments. 
            We are currently deploying autonomous shuttles on campus, self-driving cars, trucks and Unmanned Aerial Vehicles (UAVs).
        </p>
        <div id="homeCarousel" class="carousel slide" data-ride="carousel" data-interval="5000">
        <ol class="carousel-indicators">
            <li data-target="#homeCarousel" data-slide-to="0" class="active"></li>
            <li data-target="#homeCarousel" data-slide-to="1"></li>
            <li data-target="#homeCarousel" data-slide-to="2"></li>
            <li data-target="#homeCarousel" data-slide-to="3"></li>
            <li data-target="#homeCarousel" data-slide-to="4"></li>
        </ol>
        <div class="carousel-inner">
            <div class="carousel-item active">
            <img class="d-block w-100" src="/assets/carousel/warthog.jpg" alt="Slide 1">
            </div>
            <div class="carousel-item">
            <img class="d-block w-100" src="/assets/carousel/trolley.png" alt="Slide 2">
            </div>
            <div class="carousel-item">
            <img class="d-block w-100" src="/assets/carousel/truck.jpg" alt="Slide 3">
            </div>
            <div class="carousel-item">
            <img class="d-block w-100" src="/assets/carousel/ranger.jpg" alt="Slide 4">
            </div>
            <div class="carousel-item">
            <img class="d-block w-100" src="/assets/carousel/UAS.png" alt="Slide 5">
            </div>
        </div>
        <a class="carousel-control-prev" href="#homeCarousel" role="button" data-slide="prev">
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="sr-only">Previous</span>
        </a>
        <a class="carousel-control-next" href="#homeCarousel" role="button" data-slide="next">
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="sr-only">Next</span>
        </a>
        </div>
    </div>
    <div id="newsid" class="col-sm-4" >
        <div class="well">
            <h1>News</h1>
            {% for article in site.data.news_list limit:7 %}
            <h2>{{ article.date }}</h2>
            <p>{{ article.headline }}</p>
            {% endfor %}
            <h4><a href="{{ site.url }}{{ site.baseurl }}/allnews/">... see all News</a></h4>
        </div>
    </div>
</div>