---
layout: post
title:  "Improving Occlusion Occupancy Prediction"
author: Garrison Neel
thumbnail: /assets/images/occlusion/SPOT.png
---

<img src="/assets/images/occlusion/SPOT.png" alt="SPOT example" style="float:right;width:400px"/>
Safe planning for autonomous vehicles requires accurate prediction of future vehicle motion.
For observable vehicles, future motion is limited by physical constraints as well as some logical (rules of the road) constraints.
For sensor occlusion, the assumption has been that a vehicle may exit at any time, at a speed up to and slightly exceeding the speed limit.
This approach does not consider the passage of time, or any spatial perception.
Our research focuses on how this prediction can be improved to more closely reflect the true possibility of a vehicle hidden inside the occlusion.

**Related Papers**

* **Improving Bounds on Occluded Vehicle States for use in Safe Motion Planning**, G. Neel and S. Saripalli, Submitted to 2020 IEEE International Symposium on Safety, Security, and Rescue Robotics (SSRR), pdf soon.