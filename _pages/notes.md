---
layout: page
title: Unmanned Lab Notes
permalink: /notes/
---

This webpage is meant to server as a collection of internal notes for our lab. We often post papers / videos to basecamp, but they can get buried after some time. To organize and prevent interesting things getting lost to time, it would be nice to add them here in a central location. With GitHub and the web editor, it's really easy to edit this page and add links as we post.



## Must Read Papers 

[**An Intelligent, Predictive Control Approach tothe High-Speed Cross-Country Autonomous Navigation Problem**](https://www.ri.cmu.edu/pub_files/pub1/kelly_alonzo_1995_1/kelly_alonzo_1995_1.pdf)

**Notes:** Al Kelly's PhD thesis (1995) is a massive tome, but it has a pretty good compendium of material on requirements for lookahead distance, field of view, resolution, etc. This is required reading for everyone working on autonomous vehicles (air or ground)

## Good Papers

[**An Open-Source System for Vision-Based Micro-Aerial Vehicle Mapping, Planning, and Flight in Cluttered Environments**](https://arxiv.org/pdf/1812.03892.pdf)

**Notes:** An overall nice paper that describes the entire architecture for uavs. Very relevant to ground vehicles also

[**High Fidelity Day  /Night Stereo Mapping with Vegetation and Negative Obstacle Detection for Vision-in-the-Loop Walking**](http://vigir.missouri.edu/~gdesouza/Research/Conference_CDs/IEEE_IROS_2013/media/files/0692.pdf)

**Notes** - None -

## GitHub Repositories

[**Kalman filter library**](https://github.com/commaai/rednose)

**Notes** This is interesting since it uses sympy to compute jacobians symbolically and then auto generates c code, one of the few KF libraries which uses modern python tooling and gets it right.

[**Pix2Pix**](https://sezan92.github.io/2020/04/14/pix2pix_thermal.html)

**Notes** Interesting method to generate thermal images from RGB images

## Video Tutorials / Lectures
[**Robotic's Today**](https://roboticstoday.github.io/index.html)

**Notes** Interesting seminar series from prominent roboticists, scheduled on Fridays at 3PM EDT (12AM PDT) 


[**Joan Solà - Lie theory for the Roboticist**](https://www.youtube.com/watch?v=QR1p0Rabuww&feature=emb_title)

**Notes** Very useful video on Lie Groups, needed for everyone working with rotation matrices. [Paper](https://arxiv.org/abs/1812.01537)

[**Power On and Go Workshop RSS-2020**](https://www.youtube.com/watch?list=PLOakwtiBw14IkuDBpYFwl-41PFeO847QU&v=1kjAi12AQkU)

**Notes** - None -

## Guides

[**ROS Docker Setup Stack for DARPA**](https://github.com/osrf/subt_hello_world/tree/master/posts)

**Notes:** A great set of posts that describe how to use ROS and setup the entire stack for the DARPA SubT challenge. Not only a good read but setting it up would be good to just learn ROS and setup a really good sim environment