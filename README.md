# unmannedlab.github.io
### Warning, Live site! Any changes commited and pushed will deploy instantly. 

# Directory Structure

In general, you will be updating items in the following directories:
```
UNMANNEDLAB.GITHUB.IO
└───_data/
    └───news_list.yml
└───_people/
    └───YourName.md
    └───images/
        └───YourName.jpeg
└───_research/ 
    └───_posts/
        └───2020-01-01-Name-of-Research-Post1.md
        └───2020-01-01-Name-of-Research-Post2.md
└───assets/
    └───images/
        └───post_folder/
            └───ResearchImage1.png
            └───ResearchImage2.jpg
```

In general, you should only be editing the `_research` and `_people` folder. Both of these folders are markdown, which means you can edit it in and text editor easily. 

# Profile Page

## Update Photo
To edit your page/photo, navigate to the `_people` folder. If you'd like to add or change your image, upload a photo to the `_people/images` folder. It will be forced to be 200x200, so it looks best if that is the resolution. 

👮 If you did not have a photo already, be sure to edit the front matter in `_people/YourName.md`, where it says `image: none.jpeg` to `image: name.jpeg`. 

## About Me and Current Research 

Update your profile by editing `_people/YourName.md`. You can add links to your home page, girhub, google scholar, and linkedin.

EX: 

```yaml
---
layout: profile
title: Amir Darwesh
image: amir.jpeg
type: M.S. Student
show_profile: false
homepage: http://amirdarwesh.com
github: http://github.com/amirx96
g_scholar: 
linkedin: 
---

# About Me

Lorem ipsum

# Current Research

Lorem ipsum
```

👮  **Note** Your home page will not display until the `show_profile: false` flag is changed to true. Currently, everyone's is set to false because it's lorem ipsum filler text. ❗**Do not change this to true unless you have removed the lorem ipsum with your own stuff**❗ 


# Research

You probably don't have your research yet on the webpage. You can simply add it by following one of the current research's template.

## Guidelines

To add a research post, create a markdown file in `research/_posts/` following the convention `YYYY-MM-DD-Name-of-Post.md`. 

Add images to `assets/images/Your_Folder/Image_file.png`. You can use a thumbnail for your post in addition to other pictures within the markdown file of your post. 

👮 **Note** Your research can either be an excerpt, or a full post. If your research is more than 75 words, then it is automatically converted from a excerpt to a full post. 


## Markdown File
Example Template from above examples:

```yaml
---
layout: post
title:  "Sign Detection with LIDAR"
author: [Amir Darwesh, Jacob Hartzer]
thumbnail: /assets/images/lidar/sign_detection_leadin.png
---
```
```md
![lidar-sign-detect](/assets/images/lidar/sign_detection_leadin.png)

One required ability for autonomous vehicles is to correctly identify street signs. This project investigates the feasibility of using a LIDAR sensor to detect, and classify signs for autonomous vehicles. Current popular methods for sign detection are vision based, however, in case of low visibility, a LIDAR detection method can be used instead.
```

👮 **Note** You should at a minimum have a thumbnail, and an excerpt of your research. Multiple authors must be put in brackets.

# News List

In order to add to the site news feed, edit the `news_list.yml` in the `_data\` folder. The news posts are dated, with a headline and snippit using the following format. The date needs to be in YYYY-MM-DD format for the sorting to work automatically. 

```yaml
- date: 2020-02-01
  headline: "Paper in ICRA 2020"
  content: 
    - "Fast Local Planning and Mapping in Unknown Off-Road Terrain"
```

# Test the site with local host

You can build and serve a local version of the site using [jekyll](https://jekyllrb.com/docs/), [bundler](https://bundler.io/), and [ruby](https://www.ruby-lang.org/en/). If you're just changing people / research folders, than you should be ok to not do this.

With bundler and jekyll installed, run the following command to compile the static site
```bash
bundle exec jekyll build
```

Once built, run the following command to serve the site to a local host (most likely http://localhost:4000/). The `--watch` command allows the server to monitor for changes to the site files and will regenerate on save.
```bash
bundle exec jekyll serve --watch
```

## Test with Docker Image
It is also possible to build the website using the jekyll docker image. To do this, first build the docker image
```bash
docker build . -t unmanned_website
```

Then run jekyll build in the image after mounting the current directory
```shell
docker run --rm --volume="$PWD:/srv/jekyll" -it unmanned_website jekyll build
```

Finally, serve the website with the current directory mounted 
and the port mapped to [localhost:4000](http://localhost:4000/)
```shell
docker run --rm --volume="$PWD:/srv/jekyll" -p 4000:4000 -it unmanned_website jekyll serve --watch
```