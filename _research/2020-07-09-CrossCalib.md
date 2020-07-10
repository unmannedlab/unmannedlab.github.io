---
layout: post
title:  "Extrinsic Calibration of Multiple Sensors"
author: Subodh Mishra
thumbnail: /assets/images/crosscalib/warthog.png
---

Cross calibration of multiple sensors is a classic estimation problem in robotics and with the advent of multi-sensor perception and state estimation techniques, this problem has gained paramount importance. We at USL are working on both targetbased and targetless approaches of multi sensor calibration. Having already studied and implemented a few targetbased approaches we are currently exploring targetless aproaches which can be used when the robot is operating in real-time. The long term goal is to integrate a targetless motion based approach into a multi-sensor SLAM pipeline which allows tracking the calibration parameters online and detects changes which might occur during robot operation, thus ensuring robustness, miscalibration detection and recalibration.

![cone](/assets/images/crosscalib/calibresult.png)


**Related Papers**

* **Experimental Evaluation of 3D-LIDAR Camera Extrinsic Calibration**, S. Mishra, P. Osteen, G. Pandey and S. Saripalli, IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS, 2020), [pdf](https://arxiv.org/abs/2007.01959)

* **Extrinsic Calibration of a 3D-LIDAR and a Camera**, S. Mishra, G. Pandey and S. Saripalli, IEEE Intelligent Vehicles Symposium (IV, 2020) [pdf](https://arxiv.org/abs/2003.01213) 
