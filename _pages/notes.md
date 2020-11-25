---
layout: page
title: Unmanned Lab Notes
permalink: /notes/
---

This webpage is meant to server as a collection of internal notes for our lab. We often post papers / videos to basecamp, but they can get buried after some time. To organize and prevent interesting things getting lost to time, it would be nice to add them here in a central location. With GitHub and the web editor, it's really easy to edit this page and add links as we post.


## Introduction to SLAM
[**Simultaneous Localisation and Mapping ( SLAM ) : Part I The Essential Algorithms**](https://www.semanticscholar.org/paper/Simultaneous-Localisation-and-Mapping-(-SLAM-)-%3A-I-Durrant-Whyte-Bailey/666b8959abc3be4d6026f2053711a62119bec4a5)

[**Simultaneous localization and mapping (SLAM): part II**](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwj-9Pupn-DsAhUBY6wKHVQxBooQFjABegQIAhAC&url=https%3A%2F%2Fwww.doc.ic.ac.uk%2F~ajd%2FRobotics%2FRoboticsResources%2FSLAMTutorial2.pdf&usg=AOvVaw1v5KOphkEgwJU18CX2YqGh)

[**Globally Consistent Range Scan Alignment for Environment Mapping**](https://link.springer.com/article/10.1023/A:1008854305733)

[**A Tutorial on Graph-Based SLAM**](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwiWsdnun-DsAhUFc60KHdShDfgQFjAAegQIBRAC&url=http%3A%2F%2Fwww2.informatik.uni-freiburg.de%2F~stachnis%2Fpdf%2Fgrisetti10titsmag.pdf&usg=AOvVaw3_l9o1dOk82MwBGeOO-eE4)

[**INTERACTIVE COURSE ON EKF AND SLAM**](http://www.iri.upc.edu/people/jsola/JoanSola/eng/course.html)
**Notes:** Includes easy to modify and run Matlab code.

## Must Read Papers 

[**An Intelligent, Predictive Control Approach tothe High-Speed Cross-Country Autonomous Navigation Problem**](https://www.ri.cmu.edu/pub_files/pub1/kelly_alonzo_1995_1/kelly_alonzo_1995_1.pdf)

**Notes:** Al Kelly's PhD thesis (1995) is a massive tome, but it has a pretty good compendium of material on requirements for lookahead distance, field of view, resolution, etc. This is required reading for everyone working on autonomous vehicles (air or ground)

## Good Papers
[**Under the Radar: Learning to Predict Robust Keypoints forOdometry Estimation and Metric Localisation in Radar**](https://arxiv.org/pdf/2001.10789.pdf)
**Notes** - None - 

[**An Open-Source System for Vision-Based Micro-Aerial Vehicle Mapping, Planning, and Flight in Cluttered Environments**](https://arxiv.org/pdf/1812.03892.pdf)

**Notes** An overall nice paper that describes the entire architecture for uavs. Very relevant to ground vehicles also

[**High Fidelity Day  /Night Stereo Mapping with Vegetation and Negative Obstacle Detection for Vision-in-the-Loop Walking**](http://vigir.missouri.edu/~gdesouza/Research/Conference_CDs/IEEE_IROS_2013/media/files/0692.pdf)

**Notes** - None -

## GitHub Repositories

[**The X Navigation Framework by JPL-NASA**](https://github.com/jpl-x)
**Notes** Robot navigation using visual, thermal, range, solar, GPS and inertial measurements.

[**OpenVINS**](https://github.com/rpng/open_vins)
**Notes** The OpenVINS project houses some core computer vision code along with a state-of-the art filter-based visual-inertial estimator.

[**Kalman filter library**](https://github.com/commaai/rednose)

**Notes** This is interesting since it uses sympy to compute jacobians symbolically and then auto generates c code, one of the few KF libraries which uses modern python tooling and gets it right.

[**Pix2Pix**](https://sezan92.github.io/2020/04/14/pix2pix_thermal.html)

**Notes** Interesting method to generate thermal images from RGB images

[**ROS Bag Editor**](https://github.com/facontidavide/rosbag_editor)

**Notes** Good GUI to handle rosbags

## Video Tutorials / Lectures
[**Robotic's Today**](https://roboticstoday.github.io/index.html)

**Notes** Interesting seminar series from prominent roboticists, scheduled on Fridays at 3PM EDT (12AM PDT) 


[**Joan Solà - Lie theory for the Roboticist**](https://www.youtube.com/watch?v=QR1p0Rabuww&feature=emb_title)

**Notes** Very useful video on Lie Groups, needed for everyone working with rotation matrices. [Paper](https://arxiv.org/abs/1812.01537)

[**Power On and Go Workshop RSS-2020**](https://www.youtube.com/watch?list=PLOakwtiBw14IkuDBpYFwl-41PFeO847QU&v=1kjAi12AQkU)

**Notes** - None -

## Awesome Tech Reports
[**Quaternion kinematics for the error-state Kalman filter**](https://arxiv.org/abs/1711.02508)

[**Indirect Kalman Filter for 3 D Attitude Estimation**](https://www.semanticscholar.org/paper/Indirect-Kalman-Filter-for-3-D-Attitude-Estimation-Trawny-Roumeliotis/2c8e95bc331024105cbde6f6918cda8493f263c8)

[**A Multi-State Constraint Kalman Filter for Vision-aided Inertial Navigation**](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwi4ppGrwODsAhUHI6wKHVRqDOYQFjABegQIBhAC&url=https%3A%2F%2Fintra.ece.ucr.edu%2F~mourikis%2Ftech_reports%2FTR_MSCKF.pdf&usg=AOvVaw2Qr10VBlnglPsvvZmjdoDx)

[**Continuous Preintegration Theory for Graph-based Visual-Inertial Navigation**](http://udel.edu/~ghuang/papers/tr_cpi.pdf)

## Books
[**State Estimation for Robotics by Tim Barfoot**](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwjKuP7ZlZLtAhUFMqwKHRDrBYQQFjABegQIBRAC&url=http%3A%2F%2Fasrl.utias.utoronto.ca%2F~tdb%2Fbib%2Fbarfoot_ser17.pdf&usg=AOvVaw1R00Dsh9RrJoXznO9Y3gWg)

## Guides
[**Thoughts on Writing a Good (Robotics) Paper**](http://tokekar.com/docs/Tokekar-WritingPapers-Talk.pdf)
A very good introduction on How to write a good robotics paper. Everyone should read

[**The Missing Semester of Your CS Education**](https://missing.csail.mit.edu/)

**Notes** Good resource for getting some more background in linux terminals

[**ROS Docker Setup Stack for DARPA**](https://github.com/osrf/subt_hello_world/tree/master/posts)

**Notes:** A great set of posts that describe how to use ROS and setup the entire stack for the DARPA SubT challenge. Not only a good read but setting it up would be good to just learn ROS and setup a really good sim environment
