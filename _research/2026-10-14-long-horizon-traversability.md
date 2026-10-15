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
<!-- TODO: replace "#" with the RA-L / arXiv link once available -->
<a href="#">[Paper]</a> <a href="https://huggingface.co/datasets/anony-008/offroad-global-nav">[Dataset]</a>
</p>

<style>
table.res-table { border-collapse: collapse; margin: 1em auto; font-size: 0.9em; }
table.res-table th, table.res-table td { border: 1px solid #ccc; padding: 4px 10px; text-align: center; white-space: nowrap; }
table.res-table thead th { background: #f3f3f3; }

.table-wrap { overflow-x: auto; }
</style>

## News
* **October 2026:** Accepted to IEEE Robotics and Automation Letters (RA-L).

## Overview
Autonomous navigation across large off-road environments remains a challenging problem. Onboard sensors perceive only the immediate surroundings, yet safe and efficient routes depend on terrain features that extend well beyond the sensor horizon. Geospatial data sources such as satellite imagery, aerial LiDAR, and vector maps can close this gap. Learning traversability from them is difficult because dense labels are unavailable at scale and existing methods rely on short-range sensing. We propose an efficient formulation that learns a **continuous traversability map** from overhead data, supervised directly by **human-driven GPS trajectories** and shaped by **geometric priors from aerial LiDAR**. Alongside the model, we release a dataset curated from public sources, consisting of **299 scenes** spanning **~1,244 km²** of diverse terrain, paired with **1,130 km** of human driving. In field trials on a Clearpath Warthog across seven routes at two sites, our method produces trajectories within **5.5%** of human path length and reduces operator interventions by **~85%** compared to local-planner-only autonomy.

<img src="/assets/images/offroad_global_nav/warthog_field.jpg" class="center">

## Dataset
Each scene combines four co-registered, geo-referenced modalities. Candidate sites were cross-referenced against the OpenStreetMap public GPS trace corpus, and only regions where all modalities were jointly available with sufficient trace coverage were retained. Traces were verified against satellite imagery and filtered by speed to remove stationary segments and non-vehicular activity such as walking. **67.5%** of the retained traversed distance lies more than 5 m from any mapped OSM road or trail, so the traces carry information beyond the vector map.

<div class="table-wrap"><table class="res-table">
<thead><tr><th>Modality</th><th>Source</th><th>Format</th><th>Description</th></tr></thead>
<tbody>
<tr><td>Satellite imagery</td><td><a href="https://www.arcgis.com/">ArcGIS World Imagery</a></td><td>GeoTIFF</td><td style="white-space:normal">30 cm/pixel RGB showing vegetation, trails, water bodies, and terrain</td></tr>
<tr><td>Aerial LiDAR</td><td><a href="https://www.usgs.gov/3d-elevation-program">USGS 3DEP</a></td><td>LAZ</td><td style="white-space:normal">5 to 27 points/m², 10 cm vertical accuracy, elevation, slope, and intensity</td></tr>
<tr><td>Vector map</td><td><a href="https://www.openstreetmap.org/">OpenStreetMap</a></td><td>OSM XML</td><td style="white-space:normal">Highways, trails, and waterways used as weak semantic priors</td></tr>
<tr><td>Human driving</td><td><a href="https://www.openstreetmap.org/traces">OSM GPS traces</a></td><td>KML</td><td style="white-space:normal">Driven trajectories used as implicit traversability supervision</td></tr>
</tbody></table></div>

### Statistics
* **Scenes:** 299 geographically diverse locations across the United States
* **Coverage:** ~1,244 km²
* **Human driving:** ~1,130 km of GPS trajectories
* **Terrain:** deserts, grasslands, evergreen forests, mountains, quarries, and mines
* **Seasonal variation:** acquisition spread across seasons to capture changes in vegetation and surface conditions

<img src="/assets/images/offroad_global_nav/dataset.png" class="center">

### Getting Started
```python
from datasets import load_dataset

dataset = load_dataset("anony-008/offroad-global-nav")
sample = dataset["train"][0]
```

## Method
The model is a dual-stream, multi-modal network. Satellite imagery is encoded by a frozen DINOv3-SAT ViT-L/16 and decoded by a Feature Pyramid Network. LiDAR-derived height, slope, and intensity rasters and an OSM channel are encoded by a CNN. The two streams are fused by spatially-varying FiLM, so satellite context at each cell decides how strongly the LiDAR feature is amplified, suppressed, or shifted. A goal-agnostic **traversability head** produces the map consumed by the planner. A separate **path-logits head** receives start and goal heatmaps and predicts a goal-conditioned route corridor.

<img src="/assets/images/offroad_global_nav/architecture.png" class="center">

### Training Signal
* **Path corridor loss.** Driven trajectories are supervised with a non-negative Positive-Unlabeled (nnPU) formulation. Traversed cells are positives and unvisited cells are unlabeled rather than lethal. No differentiable planner or manual annotation is required.
* **Auxiliary anchors.** OSM roads and trails and aggregated historical trajectories act as weak positive targets on the traversability map.
* **LiDAR priors.** Intensity, slope, and height-gradient priors penalize hazardous terrain such as steep slopes, ditches, and drop-offs.

Anchors and priors are weighted an order of magnitude below the corridor loss. They bias feature selection without forcing the map toward their mean where they disagree.

## Benchmark
A costmap is evaluated by how closely the paths it induces reproduce driven reference trajectories. For each costmap, Yen's algorithm generates four candidate A\* paths, and the candidate with the smallest discrete Fréchet distance *d<sub>F</sub>* to the driven path is retained. Results are over **356 trajectories** (average length 412 m) from **20 held-out scenes**, including TartanDrive 2.0.

<div class="table-wrap"><table class="res-table">
<thead><tr><th>Costmap</th><th><i>d<sub>F</sub></i> (m) &darr;</th><th><i>r<sub>c</sub></i> (&rarr; 1)</th><th><i>r<sub>d</sub></i> (&rarr; 1)</th></tr></thead>
<tbody>
<tr><td>Height map</td><td>108.4 &plusmn; 18.2</td><td>0.85 &plusmn; 0.11</td><td>0.91 &plusmn; 0.06</td></tr>
<tr><td><a href="https://arxiv.org/abs/2505.09739">Trailblazer</a></td><td>91.6 &plusmn; 22.7</td><td>0.71 &plusmn; 0.09</td><td>0.81 &plusmn; 0.08</td></tr>
<tr><td>OVerSeeC</td><td>77.5 &plusmn; 20.1</td><td>0.23 &plusmn; 0.14</td><td>0.92 &plusmn; 0.06</td></tr>
<tr><td>Geometric (tuned per site)</td><td>68.4 &plusmn; 17.8</td><td>0.78 &plusmn; 0.09</td><td>0.86 &plusmn; 0.09</td></tr>
<tr><td><b>Ours</b></td><td><b>61.3 &plusmn; 14.3</b></td><td>0.93 &plusmn; 0.05</td><td>0.89 &plusmn; 0.05</td></tr>
</tbody></table></div>

*r<sub>c</sub>* is the ratio of mean planned-path cost to mean driven-path cost, and *r<sub>d</sub>* is the ratio of path lengths. Both are computed within each costmap and serve as diagnostics. Only *d<sub>F</sub>* ranks methods across costmaps. Our map attains the lowest *d<sub>F</sub>*, 10% below the per-site tuned geometric baseline, and wins on 62.5% of individual trajectories (paired Wilcoxon, *p* < 10<sup>-3</sup>).

### Ablation
Path supervision alone leaves traversability near-uniform outside the corridor. LiDAR priors and the full loss recover terrain structure. A single-head variant expresses corridors weakly because corridor and geometric terms compete within one output.

<img src="/assets/images/offroad_global_nav/ablation.jpg" class="center">

## Field Experiments
### Recording Platform
* [Clearpath Robotics Warthog](https://clearpathrobotics.com/warthog-unmanned-ground-vehicle-robot/)

### Sensor Setup
* LiDAR: Ouster OS-128
* Stereo Camera: Stereolabs ZED 2i
* RGB Cameras: 2 × FLIR Blackfly
* Inertial Navigation System (GPS/IMU): [Vectornav VN-300 Dual Antenna GNSS/INS](https://www.vectornav.com/products/vn-300)

<img src="/assets/images/offroad_global_nav/sensor_setup.jpg" class="center" width="50%">

### Autonomy Stack
Our model serves as the **Long Range Planner (LRP)**. The traversability map is converted to a costmap, and Yen's K-shortest-paths search produces a global waypoint sequence from the robot's pose to a user-specified goal. Waypoints are streamed to ARL's Phoenix autonomy stack, which runs DLIO for state estimation and MPPI control as the **Short Range Planner (SRP)** over TerrainNet local costmaps.

### Test Sites
Experiments were run at a **Levee site** with a 250 m embankment, an adjacent lake, and a runway segment, and at a **9 km² off-road site** on the Texas A&M RELLIS Campus with grassland, quarries, trails, lakes, and deciduous forest. Neither site appears in the training data, and the same weights are used at both, so both deployments are zero-shot with respect to geography.

<img src="/assets/images/offroad_global_nav/test_sites.jpg" class="center">

### Results
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

SRP-only runs were not attempted on Routes 5 to 7 because of safety risk near quarry edges and over long horizons. On the four routes where both were run, LRP paths were **5.5%** longer than the human baseline versus **13.9%** for SRP only. LRP needed **85% fewer** interventions (2 vs. 14), about one per 876 m against one per 135 m for SRP. Across all seven routes, LRP overhead averaged 7.4%. The planner also produced distinct feasible routes for the same start and goal (Routes 1 & 2, Routes 6 & 7), and replanned around an unmapped sand heap on Route 6 without further intervention.

<img src="/assets/images/offroad_global_nav/route_comparison.jpg" class="center" width="70%">

<!-- Optional: add a field-trial video
<div class="iframe-embed-wrapper iframe-embed-responsive-16by9" width="60%">
    <iframe class="iframe-embed" src="https://www.youtube.com/embed/VIDEO_ID"></iframe>
</div>
-->

## Data Download
[Hugging Face Dataset](https://huggingface.co/datasets/anony-008/offroad-global-nav)

## Citation
```
@article{viswanath2026learning,
      title={Learning Traversability for Long Horizon Off-Road Navigation},
      author={Kasi Viswanath and Jason M. Gregory and Shaunak Kolhe and Srikanth Saripalli},
      journal={IEEE Robotics and Automation Letters},
      year={2026}
}
```

## Collaborator
<a href="https://www.arl.army.mil/"><img src="/assets/images/rellis_3d/arl_logo.png" alt="The DEVCOM Army Research Laboratory" class="center" width="20%"></a>

## Acknowledgments
This research was developed with funding from the Defense Advanced Research Projects Agency (DARPA) and DEVCOM Army Research Laboratory (ARL) and was accomplished under Cooperative Agreement Number W911NF-21-2-0064. The views, opinions and/or findings expressed are those of the authors and should not be interpreted as representing the official views or policies of DARPA, ARL or the U.S. Government. We thank Felix Sanchez, Phil Osteen, and Eli Lancaster for their help during field testing, and the Texas A&M RELLIS Campus administration for access to the test sites. The dataset builds on USGS 3DEP LiDAR, ArcGIS World Imagery, and OpenStreetMap.

## License
The dataset is released under the [Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/).

## Related Work
[Trailblazer: Learning Offroad Costmaps for Long Range Planning](https://arxiv.org/abs/2505.09739)

[GO: The Great Outdoors Multimodal Dataset](https://arxiv.org/abs/2501.19274)

[RELLIS-3D: A Multi-modal Dataset for Off-Road Robotics](https://unmannedlab.github.io/research/RELLIS-3D)
