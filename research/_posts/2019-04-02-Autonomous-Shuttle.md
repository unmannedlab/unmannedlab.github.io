---
layout: post
title:  Autonomous Shuttle
author: 
thumbnail: /assets/images/auto_shuttle/shuttle0.jpg
---

![](/assets/images/auto_shuttle/shuttle0.jpg)

We have a drive-by-wire electric shuttle equipped with several basic sensors needed for autonomous operation. The shuttle is capable of following a predetermined GPS waypoint path at speeds of around 10 kph. Roof-mounted 3D LIDAR is used for obstacle detection, and a forward-facing camera is used for object classification. We believe that Autonomous Shuttles can solve the last mile problem effectively and cheaply. Towards this end, we plan on deploying the first shuttle on Texas A&M Campus in August.

Currently, we have a Velodyne VLP-16 Lidar, Novatel SPAN IGM-A1 GPS/IMU, and a Zed stereo camera. Sensor data is processed in ROS, allowing for easy interoperability and interchangability of control and analysis software. Basic implementations of obstacle detection and GPS waypoint following are complete, as well as a low-level speed and steering controller.

Our goal for this platform is to evaluate novel control technologies for self driving vehicles. Because of the interchangeability offered by ROS, we plan to implement several variations each of localization, obstacle avoidance, and path planning. We will compare these methods objectively through data collection and analysis, and subjectively to evaluate human interaction and perception.

![](/assets/images/auto_shuttle/shuttle1.jpg)

The shuttle is equipped with a Novatel SPAN GPS/IMU which is capable of positional accuracy of under 5 cm globally. This highly accurate GPS allows us to accurately evaluate new localization methods such as SLAM or various sensor fusion methods. Evaluating localization methods allows down-selection to cheaper yet tolerably-accurate solutions to be implemented on future vehicles.
campus map

![](/assets/images/auto_shuttle/shuttle2.jpg)


In order to test path planning, and obstacle detection and avoidance, we have permission to test on campus at Texas A&M. This allows for both closed-course testing and also testing in real-world scenarios. Our campus has predictable but large fluctuations in vehicular and pedestrian traffic, allowing for testing in a wide range of conditions. Nearby facilities have also partnered with our lab to allow testing and evaluation on-site. One example is the Stella Hotel in Bryan, TX where we will be providing shuttle service in July..

Path Planning and Obstacle detection

[![Path Planning and Obstacle Detection - Self Driving Shuttle](http://img.youtube.com/vi/Zb63iPoHZ_8/0.jpg)](https://youtu.be/Zb63iPoHZ_8 "Path Planning and Obstacle Detection - Self Driving Shuttle")


[![Self Driving Shuttle First Person View](http://img.youtube.com/vi/V-FjMMKsZMk/0.jpg)](https://youtu.be/V-FjMMKsZMk "Self Driving Shuttle First Person View")

