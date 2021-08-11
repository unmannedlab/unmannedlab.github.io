---
layout: post
title:  "Roadside LiDAR Dataset"
author: Amir Darwesh
thumbnail: /assets/images/roadside_lidar/roadside-photo.png
---
<p align="center">
<img src="/assets/images/roadside_lidar/roadside-photo.png" alt="Roadside LiDAR Photo" height="450">
</p>
A roadside LiDAR dataset both in urban and in highway environments with annotated vehicles. This dataset corresponds to the dataset described in "Building a Smart Work Zone Using Roadside LiDAR". Our dataset contains two ~10 minute segments on a urban (45 mph) and highway segment (75 mph), consisting of >1000 frames labeled of measurements taken with a Velodyne VLP-16. The dataset format is as follows:

- Raw (unprocessed ROI filtering) rosbags 
- Bird's Eye View projection images of LiDAR data
- Labels in `.csv` format for each image

[Full Dataset Link](https://drive.google.com/drive/folders/1F1WF5ZeknfVPcblgGkatQCpKXps6rf5T?usp=sharing)

The table below summarizes the dataset:

<p align="center">
<img src="/assets/images/roadside_lidar/dataset_table.png" alt="Dataset Table Summary" style="max-height: 200px;">
</p>


## Citation:

```
@misc{darwesh2021SWZ,
      title={Building a Smart Work Zone Using Roadside LiDAR
      author={Darwesh, Amir and Wu, Dayoung and Le, Minh and Saripalli, Srikanth},
      year={2021},
      journal={IEEE Transactions on Intelligent Transportation Systems},
      publisher={IEEE}
}
```