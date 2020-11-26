---
permalink: /semanticusl.html
layout: page
title: "SemanticUSL: A Dataset for LiDAR Semantic Segmentation Domain Adatpation"
---
<p align="center">
<img src="/assets/images/lidarnet/usl_scene.png">
</p>

SemanticUSL was collected on a Clearpath Warthog robotics with an Ouster OS1-64 Lidar. The data collection location includes the campus site and off-road research facility of Texas A& M University. The data include the traffic-road scene, walk-road scene, and off-road scene. Our dataset has 16578 unlabeled scans for domain adaptation training and 1200 labeled scans for evaluation. The data uses the same format and ontology as SemanticKITTI; therefore, it can be easily used for domain adaptation research between [SemanticKITTI](http://semantic-kitti.org/) and [SemanticPOSS](poss.pku.edu.cn/semanticposs.html).  

<p align="center">
<img  src="/assets/images/lidarnet/warthog.jpg">
</p>

### Download

**Example Data** [link](https://github.com/unmannedlab/LiDARNet)

**Full Data** [link](https://github.com/unmannedlab/LiDARNet)

## LiDARNet: A Boundary-Aware Domain Adaptation Model for Point Cloud Semantic Segmentation

We present a boundary-aware domain adaptation model for LiDAR scan full-scene semantic segmentation (LiDARNet). Our model can extract both the domain private features and the domain shared features with a two branch structure.  We embedded Gated-SCNN into the segmentor component of LiDARNet to learn boundary information while learning to predict full-scene semantic segmentation labels. Moreover, we further reduce the domain gap by inducing the model to learn a mapping between two domains using the domain shared and private features. Besides, we introduce a new dataset ([SemanticUSL](https://unmannedlab.github.io/research/SemanticUSL)). The dataset has the same data format and ontology as SemanticKITTI. We conducted experiments on real-world datasets [SemanticKITTI](http://semantic-kitti.org/), [SemanticPOSS](poss.pku.edu.cn/semanticposs.html), and SemanticUSL, which have differences in channel distributions, reflectivity distributions, diversity of scenes, and sensors setup. Using our approach, we can get a single projection-based LiDAR full-scene semantic segmentation model working on both domains. Our model can keep almost the same performance on the source domain after adaptation and get an 8%-22% mIoU performance increase in the target domain.

**The paper is released on [arXiv](https://arxiv.org/abs/2003.01174)**

**The code is released on [Github](https://github.com/unmannedlab/LiDARNet)**

## Approaches
Generally, we expect a model that can complete a task for data from similar domains. However, feature difference between two similar domains causes a model, which learns from one domain (called source domain \(S\)), can not perform well on another domain (called target domain \(T\)). Therefore, we expect a method that can adapt a model from one domain to another domain. If the target domain does not provide ground truth, the problem is called unsupervised domain adaptation. In this paper, the task is full-scene semantic segmentation for Lidar scan. In this problem, we use \(X_S\) denotes source data, \(Y_S\) denotes source labels, and \(X_T\) denotes target data, but target labels are not accessible.

Based on the intuition that two similar domains should contain shared information across the two domains and private information to each domain. And the adaptable information should be contained in shared information of two domains. Therefore, we designed an end-to end trainable model that splits input data into domain shared and private features. The model then utilizes the extracted shared features to perform semantic segmentation.
Fig.1 shows the components of the model and the information flow in the model. The model contains two extractors: a shared feature extractor \(f_P\)  and a private feature extractor \(f_D\).

To induce the two extractors to produce such split information, we add a loss function that encourages the independence of these parts, and connect the private feature extractor to a classifier \(f_C\) to differentiate the data from two domains. Besides, we feed the output of the domain shared extractor to a segmentor to complete the same task (predict semantic labels \(\hat{Y}\)).
To ensure that the private features are still useful and to further reduce the domain gap, we introduce the CycleGAN mechanism \cite{Zhu2017} to induce the models to learn two mappings between two domains. The domain private and shared features are fed into domain converters to convert the data from one domain to another domain: (\(f_{S\to T}\) converts source data into target domain, \(f_{T\to S}\) converts target data into source domain). The conversion is learning through an adversarial learning procedure. Therefore, the converted data are separately fed into domain discriminators (\(D_{T}\) and \(D_{S}\)).
Meanwhile, we add Gated-SCNN \cite{Takikawa2019} on the side of the segmentor to extract boundary maps \(B\)  while learning to predict semantic segmentation. We utilize the output boundaries to penalize the label predictions from the target domain. To further penalize the label output, we add a boundaries discriminator \(D_{B}\), and a labels discriminator \(D_{Y}\) to penalize the output label and boundary.

<br/><br/>
<p align="center">
<img src="/assets/images/lidarnet/approach.png">
</p>

## Results

**Experiment I: From SemanticKITTI to SemanticPOSS and SemanticUSL** 
<br/><br/>
<p align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/62C9cKzw3eY" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>
<br/><br/>

![LiDARNetkitti](/assets/images/lidarnet/LiDARNetkitti.png)


<br/><br/>

**Experiment II: From SemanticPOSS to SemanticKITTI and SemanticUSL**
<br/><br/>
 <div style="text-align:center"><iframe width="560" height="315" src="https://www.youtube.com/embed/jd-OaQ3jD5k" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>

<br/><br/>
![LiDARNetposs](/assets/images/lidarnet/LiDARNetposs.png)


<br/><br/>
**Experiment III: From SemanticUSL to SemanticPOSS and SemanticKTTI**
<br/><br/>
<p align="center">
 <iframe width="560" height="315" src="https://www.youtube.com/embed/eRk7VJbQsRM" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>

<br/><br/>
![LiDARNetusl](/assets/images/lidarnet/LiDARNetusl.png)

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
## Related Work

[LiDARNet: A Boundary-Aware Domain Adaptation Model for Lidar Point Cloud Semantic Segmentation](https://unmannedlab.github.io/research/LiDARNet)

[RELLIS-3D: A Multi-modal Dataset for Off-Road Robotics](https://unmannedlab.github.io/research/RELLS-3D)


