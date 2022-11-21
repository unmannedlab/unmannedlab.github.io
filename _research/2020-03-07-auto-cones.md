---
layout: post
title:  "Autonomous Cone Placement"
author: Jacob Hartzer
thumbnail: /assets/images/cone/ConeSetup.png
---

The Auto Cone project is an effort to develop cones that are capable of localizing and placing themselves to improve safety conditions for highway workers. These cones utilize RTK GPS and onboard localization filtering to produce decimeter-level accuracy in placing themselves in road conditions. Additionally, they are capable of transitioning through GPS-denied environments such as under bridges or overpasses. Pictured are two of the cones and the real-time kinematic (RTK) base station.

<img class="center" src="/assets/images/cone/ConeSetup.png" alt="Cone Setup">

# Problem:

The goal of this project is to develop a robotic platform capable of automatically placing cones in a defined wedge shape behind the work vehicle within the starting lane. Specifically the cones shall:
- Place three cones in 40 foot increments in a wedge
- Begin the wedge 80 feet from the end of the vehicle
- Operate on highway surfaces unaffected by small debris
- Remain within the lane despite road curvature
- Not rely on magnetic or road-embedded sensors
- Have a speed greater than 0.3 m/s
- Cost less than $1,500 per cone unit
- Be easy to use and require little training

# Kinematics:

The omnidirectional platform makes the system holonomic, which means that with only three motors, the system can smoothly and directly move between any two states. This allows orientation to be independently controlled from position, and makes the system unconstrained by initial conditions. This is very advantageous for pick and place when deploying. The image outlines the kinematics used to drive the cone's motion.

<img class="center" src="/assets/images/cone/Kinematics.png" alt="Kinematics">

# Sensor Fusion:

Using a system of RTK GPS and a ground base station, the cone's achieve a much lower position error than typical GPS for a relatively small increase in cost.

<img class="center" src="/assets/images/cone/RTK.png" alt="RTK GPS">

Fusing these corrected GPS measurements with the higher rate encoders on the wheel motors provides the system with a high rate localization estimate that is robust in handling drift and sensor noise.

# Results:

The results of this project were a functioning prototype system that is capable of deploying multiple cones without collision to a wedge shape formation while remaining within lane lines. The system is also capable of operating in GPS-denied environments.

# Videos

Deployment:
<div class="iframe-embed-wrapper iframe-embed-responsive-16by9" width="60%">
    <iframe class="iframe-embed" src="https://www.youtube.com/embed/0hgOc2csaWE"></iframe>
</div>

IV2020 Presentation:
<div class="iframe-embed-wrapper iframe-embed-responsive-16by9" width="60%">
    <iframe class="iframe-embed" src="https://www.youtube.com/embed/cbcMwYcLUmk"></iframe>
</div>

# Preprint

A preprint of the paper can be found [here](https://arxiv.org/abs/2104.14103).

# Citation:

```
@INPROCEEDINGS{AutoCone,
  author={Hartzer, Jacob and Saripalli, Srikanth},
  booktitle={2020 IEEE Intelligent Vehicles Symposium (IV)},
  title={AutoCone: An OmniDirectional Robot for Lane-Level Cone Placement},
  year={2020},
  pages={1663-1668},
  doi={10.1109/IV47402.2020.9304683}
}
```
