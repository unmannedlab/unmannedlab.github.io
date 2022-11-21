---
layout: post
title:  "SemanticUSL: A Dataset for LiDAR Semantic Segmentation Domain Adaptation"
author: Peng Jiang
thumbnail: /assets/images/lidarnet/usl_scene.png
---

<img src="/assets/images/lidarnet/usl_scene.png" class="center">

SemanticUSL was collected on a Clearpath Warthog robotics with an Ouster OS1-64 Lidar. The data collection location includes the campus site and off-road research facility of Texas A& M University. The data include the traffic-road scene, walk-road scene, and off-road scene. Our dataset has 16578 unlabeled scans for domain adaptation training and 1200 labeled scans for evaluation. The data uses the same format and ontology as SemanticKITTI; therefore, it can be easily used for domain adaptation research between [SemanticKITTI](http://semantic-kitti.org/) and [SemanticPOSS](poss.pku.edu.cn/semanticposs.html).

<img src="/assets/images/lidarnet/warthog.jpg" class="center">

### Download

**Example Data** [link](https://drive.google.com/file/d/1f2Yq5TNKWZgB4iVJzYzxkvyIa_X9zL7F/view?usp=sharing)

**Full Data** [link](https://drive.google.com/file/d/15-RqQXKoFPQGAjA1vG05cx6QTBuTfz38/view?usp=sharing)

## Related Work

[LiDARNet: A Boundary-Aware Domain Adaptation Model for Lidar Point Cloud Semantic Segmentation](https://unmannedlab.github.io/research/LiDARNet)

[RELLIS-3D: A Multi-modal Dataset for Off-Road Robotics](https://unmannedlab.github.io/research/RELLIS-3D)

## Citation
```
@misc{jiang2020lidarnet,
      title={LiDARNet: A Boundary-Aware Domain Adaptation Model for Lidar Point Cloud Semantic
      author={Peng Jiang and Srikanth Saripalli},
      year={2020},
      eprint={2003.01174},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```


