# unmannedlab.github.io
### Warning, Live site! Any changes commited and pushed will deploy instantly. 

# Directory Structure

In general, these are the directories you should only be changing items in the following directories:
```
UNMANNEDLAB.GITHUB.IO
_research
├───auto-cones
│   └───images
└───lidar-sign-detection
|   └───images
|
_people

```

# Editing 
In general, you should only be editing the `_research` and `_people` folder. Both of these folders are markdown, which means you can edit it in and text editor easily. 
## People

### Photo Update
To edit your page/photo, navigate to the `_people` folder. If you'd like to add or change your image, upload a ❗**200x200 px**❗ photo to the `_people/images` folder. 

👮 If you did not have a photo already, be sure to edit the front matter in `_people/YourName.md`, where it says `image: none.jpeg` to `image: name.jpeg`. 

### Profile page update 

Update your profile by editing `_people/YourName.md`. You can add links to your home page, girhub, google scholar, and linkedin.

EX: 

```yaml
---
layout: profile
title: Amir Darwesh
image: amir.jpeg
type: M.S.
show_profile: false
homepage: http://amirdarwesh.com
github : http://github.com/amirx96
g_scholar: 
linkedin: 
---


```


👮  **Note** Your home page will not display until the `show_profile: false` flag is changed to true. Currently, everyone's is set to false because it's lorem ipsum filler text. ❗**Do not change this to true unless you have removed the lorem ipsum with your own stuff**❗ 


## Research

You probably don't have your research yet on the webpage. You can simply add it by following one of the current research's template. 

### Guidelines


#### Folder Conventions
To add a research, create a folder in `_research` with the name of your research. E.g. `lidar-camera-calibration` would be an appropriately named folder. 

In that folder, you will need to create a markdown file named similarily to your research folder. E.g. `lidar-camera-calibration.md` is an appropriate name. 

To add images, create a images folder within your research folder. E.g. `_research/lidar-camera-calibration/images`.

❗**You should have a lead-in image that is exactly 315 x 155 px in dimensions**❗

### Markdown File
Example Template from above examples:

```html
---
title:  "LIDAR Camera Cross Calibration"
author: John Researcher
excerpt_only: true
---
<img class="research-post-lead-in-img" src="/research/lidar-camera-calibration/images/calibration_leadin.png">
One required ability for autonomous vehicles is to correctly identify street signs. This project investigates the feasibility of using a LIDAR sensor to detect, and classify signs for autonomous vehicles. Current popular methods for sign detection are vision based, however, in case of low visibility, a LIDAR detection method can be used instead.
<!--more-->


```
You should at a minimum have a lead-in image, and an excerpt of your research. If you'd like to, you can add more after `<!--more-->` tag to discuss your research. Be sure to also change the `excerpt_only` flag to flase, and this will display a link to to your full research post. 


## Checks before commiting

You can download jekyll and build the site using `jekyll` serve before commiting to view the changes locally. If you're just changing people / research folders, than you should be ok. 


