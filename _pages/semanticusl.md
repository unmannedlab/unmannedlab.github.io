---
permalink: /semanticusl.html
layout: page
title: SemanticUSL
---
## <a name="semanticusl"></a>SemanticUSL: A Dataset for Semantic Segmentation Domain Adatpation
![SemenaticUSL](/assets/images/da_seg/usl_scene.png)

SemanticUSL was collected on a Clearpath Warthog robotics with an Ouster OS1-64 Lidar. The data collection location includes the campus site and off-road research facility of Texas A& M University. The data include the traffic-road scene, walk-road scene, and off-road scene. Our dataset has 16578 unlabeled scans for domain adaptation training and 1200 labeled scans for evaluation. The data uses the same format and ontology as SemanticKITTI; therefore, it can be easily used for domain adaptation research between SemanticKITTI and SemanticPOSS.  

![warthog](/assets/images/da_seg/warthog.jpg)

### Download

**Example Data** [link](https://github.com/unmannedlab/LiDARNet)

**Full Data** [link](https://github.com/unmannedlab/LiDARNet)

## LiDARNet: A Boundary-Aware Domain Adaptation Model for Point Cloud Semantic Segmentation

![LiDARNet](/assets/images/da_seg/data_flow.png)

We present a boundary-aware domain adaptation model for LiDAR scan full-scene semantic segmentation (LiDARNet). Our model can extract both the domain private features and the domain shared features with a two branch structure.  We embedded Gated-SCNN into the segmentor component of LiDARNet to learn boundary information while learning to predict full-scene semantic segmentation labels. Moreover, we further reduce the domain gap by inducing the model to learn a mapping between two domains using the domain shared and private features. Besides, we introduce a new dataset ([SemanticUSL](#abcd)). The dataset has the same data format and ontology as SemanticKITTI. We conducted experiments on real-world datasets [SemanticKITTI](http://semantic-kitti.org/), [SemanticPOSS](poss.pku.edu.cn/semanticposs.html), and SemanticUSL, which have differences in channel distributions, reflectivity distributions, diversity of scenes, and sensors setup. Using our approach, we can get a single projection-based LiDAR full-scene semantic segmentation model working on both domains. Our model can keep almost the same performance on the source domain after adaptation and get an 8\%-22\% mIoU performance increase in the target domain.


**The code is released on [Github](https://github.com/unmannedlab/LiDARNet)**

## Results

### Domain Adapation from SemanticKITTI to SemanticPOSS and SemanticUSL

![LiDARNetkitti](/assets/images/da_seg/LiDARNetkitti.png)

<iframe width="560" height="315" src="https://www.youtube.com/embed/62C9cKzw3eY" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Domain Adapation from SemanticPOSS to SemanticKITTI and SemanticUSL

![LiDARNetposs](/assets/images/da_seg/LiDARNetposs.png)

<iframe width="560" height="315" src="https://www.youtube.com/embed/jd-OaQ3jD5k" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Domain Adapation from SemanticUSL to SemanticPOSS and SemanticKTTI

![LiDARNetusl](/assets/images/da_seg/LiDARNetusl.png)

<iframe width="560" height="315" src="https://www.youtube.com/embed/eRk7VJbQsRM" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>






