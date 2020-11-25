---
layout: post
title:  "SemanticUSL: A Dataset for LiDAR Semantic Segmentation"
author: Peng Jiang
thumbnail: /assets/images/lidarnet/lidarnet.png
---
SemanticUSL was collected on a Clearpath Warthog robotics with an Ouster OS1-64 Lidar. The data collection location includes the campus site and off-road research facility of Texas A& M University. The data include the traffic-road scene, walk-road scene, and off-road scene. Our dataset has 16578 unlabeled scans for domain adaptation training and 1200 labeled scans for evaluation. The data uses the same format and ontology as SemanticKITTI; therefore, it can be easily used for domain adaptation research between [SemanticKITTI](http://semantic-kitti.org/) and [SemanticPOSS](poss.pku.edu.cn/semanticposs.html).  

![SemenaticUSL](/assets/images/lidarnet/usl_scene.png)

![warthog](/assets/images/lidarnet/warthog.jpg)

### Download

**Example Data** [link](https://github.com/unmannedlab/LiDARNet)

**Full Data** [link](https://github.com/unmannedlab/LiDARNet)

## Related Work

[LiDARNet: A Boundary-Aware Domain Adaptation Model for Lidar Point Cloud Semantic Segmentation](https://unmannedlab.github.io/research/LiDARNet)

## Citation
'''
@misc{jiang2020lidarnet,
      title={LiDARNet: A Boundary-Aware Domain Adaptation Model for Lidar Point Cloud Semantic 
      author={Peng Jiang and Srikanth Saripalli},
      year={2020},
      eprint={2003.01174},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
'''


