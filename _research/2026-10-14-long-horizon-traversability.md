---
layout: post
title:  "Learning Traversability for Long Horizon Off-Road Navigation"
author: Kasi Viswanath
thumbnail: /assets/images/offroad_global_nav/warthog_field.jpg
---
<p align="center">
<a href="https://www.tamu.edu/"><img src="/assets/images/rellis_3d/tamu_logo.png" alt="Texas A&M University" height="90px" width="450px"></a>&emsp;&emsp;&emsp;&emsp;<a href="https://www.arl.army.mil/"><img src="/assets/images/rellis_3d/arl_logo.png" alt="DEVCOM Army Research Laboratory" height="90px" width="270px"></a></p>
<p align="center">
Kasi Viswanath<sup>1</sup>, Jason M. Gregory<sup>2</sup>, Shaunak Kolhe<sup>1</sup> and Srikanth Saripalli<sup>1</sup><br>
1. <a href="https://www.tamu.edu/">Texas A&M University; </a>&emsp;2. <a href="https://www.arl.army.mil/">DEVCOM Army Research Laboratory</a><br>
<a href="https://arxiv.org/abs/2607.23743">[Paper]</a> <a href="https://huggingface.co/datasets/anony-008/offroad-global-nav">[Dataset]</a>
</p>

<style>
table.res-table { border-collapse: collapse; margin: 1em auto; font-size: 0.9em; }
table.res-table th, table.res-table td { border: 1px solid #ccc; padding: 4px 10px; text-align: center; white-space: nowrap; }
table.res-table thead th { background: #f3f3f3; }
.table-wrap { overflow-x: auto; }
</style>

## News
* **October 2026:** Accepted to IEEE Robotics and Automation Letters (RA-L).

<p align="center"><i>We learn kilometer-scale traversability maps from satellite imagery and aerial LiDAR, supervised only by where people have driven.</i></p>

<img src="/assets/images/offroad_global_nav/warthog_field.jpg" class="center">

## Overview
Onboard sensors see only the immediate surroundings, but safe off-road routes depend on terrain far beyond the sensor horizon. Overhead data can fill this gap, yet dense traversability labels do not exist at scale. We learn a continuous traversability map from satellite imagery, aerial LiDAR, and OpenStreetMap, supervised by human-driven GPS trajectories and shaped by LiDAR geometric priors. We also release a dataset of **299 scenes** covering **~1,244 km²** with **1,130 km** of human driving. On a Clearpath Warthog, our planner stays within **5.5%** of human path length and cuts operator interventions by **~85%** compared to local-planner-only autonomy.

## Dataset
<img src="/assets/images/offroad_global_nav/dataset.png" class="center">

Each scene pairs 30 cm satellite imagery, USGS aerial LiDAR, OpenStreetMap vectors, and filtered public GPS traces, all co-registered. Scenes span deserts, grasslands, forests, mountains, and quarries across the United States. Two thirds of the driven distance lies off mapped roads and trails.

```python
from datasets import load_dataset
dataset = load_dataset("anony-008/offroad-global-nav")
```

## Method
<img src="/assets/images/offroad_global_nav/architecture.png" class="center">

A frozen DINOv3-SAT encoder processes satellite imagery, and a CNN encodes LiDAR height, slope, intensity, and OSM rasters. Satellite features modulate LiDAR features cell by cell through FiLM. Driven trajectories supervise a goal-conditioned path head through a Positive-Unlabeled loss, so unvisited terrain is treated as unknown rather than lethal. A separate goal-agnostic head outputs the traversability map used for planning.

## Learned Traversability
<img src="/assets/images/offroad_global_nav/ablation.jpg" class="center">

Trajectory supervision alone leaves the map flat outside driven corridors. Adding LiDAR priors recovers terrain structure, and the full loss resolves both the trail network and the surrounding terrain.

## Benchmark
<div class="table-wrap"><table class="res-table">
<thead><tr><th>Costmap</th><th><i>d<sub>F</sub></i> (m) &darr;</th><th><i>r<sub>c</sub></i> (&rarr; 1)</th><th><i>r<sub>d</sub></i> (&rarr; 1)</th></tr></thead>
<tbody>
<tr><td>Height map</td><td>108.4 &plusmn; 18.2</td><td>0.85 &plusmn; 0.11</td><td>0.91 &plusmn; 0.06</td></tr>
<tr><td><a href="https://arxiv.org/abs/2505.09739">Trailblazer</a></td><td>91.6 &plusmn; 22.7</td><td>0.71 &plusmn; 0.09</td><td>0.81 &plusmn; 0.08</td></tr>
<tr><td>OVerSeeC</td><td>77.5 &plusmn; 20.1</td><td>0.23 &plusmn; 0.14</td><td>0.92 &plusmn; 0.06</td></tr>
<tr><td>Geometric (tuned per site)</td><td>68.4 &plusmn; 17.8</td><td>0.78 &plusmn; 0.09</td><td>0.86 &plusmn; 0.09</td></tr>
<tr><td><b>Ours</b></td><td><b>61.3 &plusmn; 14.3</b></td><td>0.93 &plusmn; 0.05</td><td>0.89 &plusmn; 0.05</td></tr>
</tbody></table></div>

We plan on each costmap and measure Fréchet distance *d<sub>F</sub>* to the human-driven path over 356 trajectories in 20 held-out scenes. Our map is 10% closer than the strongest baseline, which needs per-site tuning.

## Real-World Experiments
<img src="/assets/images/offroad_global_nav/test_sites.jpg" class="center">

We deployed on a Clearpath Warthog at a levee site and a 9 km² off-road site on the RELLIS Campus. Neither site was in training. The costmap avoids embankment slopes, water, and quarries, and finds corridors through dense vegetation.

<img src="/assets/images/offroad_global_nav/route_comparison.jpg" class="center" width="70%">

<div class="table-wrap"><table class="res-table">
<thead>
<tr><th rowspan="2">Route</th><th colspan="3">Distance (m)</th><th colspan="2">Interventions</th></tr>
<tr><th>Human</th><th>LRP</th><th>SRP only</th><th>LRP</th><th>SRP only</th></tr>
</thead>
<tbody>
<tr><td>1</td><td>320</td><td>335</td><td>360</td><td>0</td><td>3</td></tr>
<tr><td>2</td><td>379</td><td>386</td><td>392</td><td>1</td><td>2</td></tr>
<tr><td>3</td><td>765</td><td>810</td><td>901</td><td>1</td><td>8</td></tr>
<tr><td>4</td><td>195</td><td>220</td><td>236</td><td>0</td><td>1</td></tr>
<tr><td>5</td><td>393</td><td>425</td><td>&ndash;</td><td>2</td><td>&ndash;</td></tr>
<tr><td>6</td><td>1,680</td><td>1,714</td><td>&ndash;</td><td>3</td><td>&ndash;</td></tr>
<tr><td>7</td><td>1,680</td><td>1,956</td><td>&ndash;</td><td>1</td><td>&ndash;</td></tr>
</tbody></table></div>

Our long-range planner (LRP) stays close to the human route, while local-planner-only autonomy (SRP) drifts and needs more interventions. SRP was not run on Routes 5 to 7 for safety.

<!-- Optional: add a field-trial video
## Video
<div class="iframe-embed-wrapper iframe-embed-responsive-16by9" width="60%">
    <iframe class="iframe-embed" src="https://www.youtube.com/embed/VIDEO_ID"></iframe>
</div>
-->

## Citation
```
@article{viswanath2026learning,
      title={Learning Traversability for Long Horizon Off-Road Navigation},
      author={Kasi Viswanath and Jason M. Gregory and Shaunak Kolhe and Srikanth Saripalli},
      journal={IEEE Robotics and Automation Letters},
      year={2026}
}
```

## Acknowledgments
This research was developed with funding from the Defense Advanced Research Projects Agency (DARPA) and DEVCOM Army Research Laboratory (ARL) and was accomplished under Cooperative Agreement Number W911NF-21-2-0064. The views, opinions and/or findings expressed are those of the authors and should not be interpreted as representing the official views or policies of DARPA, ARL or the U.S. Government.

## License
The dataset is released under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/).

## Related Work
[Trailblazer: Learning Offroad Costmaps for Long Range Planning](https://arxiv.org/abs/2505.09739)

[GO: The Great Outdoors Multimodal Dataset](https://arxiv.org/abs/2501.19274)

[RELLIS-3D: A Multi-modal Dataset for Off-Road Robotics](https://unmannedlab.github.io/research/RELLIS-3D)
