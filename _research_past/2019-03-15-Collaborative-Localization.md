---
layout: post
title:  Vision Based Collaborative Localization for UAVs
author: Sai Vemprala 
thumbnail: /assets/images/other/collab_localization.png
---

The main aim of this project is to create a framework that can perform collaborative localization between groups of micro aerial vehicle (multirotor vehicles) using monocular cameras as the only sensors.

Especially in the context of UAV swarms, which is rapidly becoming a popular idea in robotics, the focus is usually on small platforms with limited sensory payload and computational capacity. In the context of such groups, having each vehicle run its own version of localization algorithms such as SLAM can be computationally intensive. Although monocular cameras are ubiquitous in current day MAV platforms, monocular cameras are unable to resolve scale on their own, which necessitates further sensor fusion. Given these challenges, the idea of collaboration can be desirable as it has the potential to reduce computation as well as improve localization accuracy: relative measurements can be fused with individual measurements to reduce estimation error over a group. Collaboration also allows for localizing all vehicles in one frame of reference, which is advantageous for applications such as formation control.

In this algorithm, we initially detect features from all cameras and extract common features through matching. The matches are then propagated through an adaptive RANSAC technique [ref] which results in the creation of a map. Once created, this map is then accessible from all vehicles, allowing each vehicle to perform its own localization through feature tracking and 3D-2D correspondences. We assume that the metric distance and heading between at least two vehicles is known before initializing the algorithm in order to have an estimate of the scale. As the vehicles move around, if the number of tracked features falls below a certain threshold, the vehicles ‘collaborate’ once more to match common features and update the global map. Thus, continuous communication between vehicles is not necessary. The frequency at which the map update happens depends on factors such as how fast the movement of the UAVs is, how quickly the environment can change etc. We are currently also looking into techniques such as covariance intersection so that two vehicles can use relative measurements between each other if needed, without having to perform a full map update.

<iframe width="560" height="315" src="https://www.youtube.com/embed/z5NQv5I1t7U" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Recently, we have tested this algorithm using Microsoft AirSim, the UAV simulator which was modified in order to simulate multiple vehicles. AirSim uses Unreal Engine as its base, a high fidelity videogame enigne with features such as high resolution textures, realistic shadows, post processing and visual effects. A sample video of localization being performed using AirSim images can be seen below.

<iframe width="560" height="315" src="https://www.youtube.com/embed/feL5Exfm3xQ" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

