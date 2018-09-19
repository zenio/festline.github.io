---
layout: article
permalink: /prerequisites
title: "Prerequisites"
comments: false
share: false
image:
  teaser: teaser-prereq.png
---

The course aims at a perfect balance between theory and practice. Therefore, prerequisites include:
 - Python
 - Math
 - Software
 - DevOps 

## Python
Basic skills are required: writing loops, functions, classes etc. Some interactive tutorial like DataQuest, DataCamp or even CodeAcademy will suffice. However, deeper dive into Python is only appreciated, there will be some tasks where you have to implement an ML algo from scratch.

## Math
Knowledge of basic concepts from calculus, linear algebra, probability theory and statistics is also required. If you need to catch up, a good resource will be Part I of the ["Deep Learning" book](http://www.deeplearningbook.org/) or ["Mathematics for Machine Learning"](https://mml-book.github.io/). For a deeper dive take a look at [MIT courses](https://ocw.mit.edu/courses/mathematics/).

## Software requirements
Generally, installing the latest [Anaconda 3](https://www.anaconda.com/download/) distribution is the best option (it contains `NumPy`, `Pandas`, `Sklearn`, `Jupyter` and lots of other libraries). However, some other packages are also used – `Xgboost` and/or `LightGBM` and/or `CatBoost` and `Vowpal Wabbit` to name a few. Installing some of them on Windows might be painful.

You've got several alternatives to set up your environment:
 - Kaggle Kernels & Azure ML
 - Pip & Anaconda
 - Docker

#### Kaggle kernels & Azure ML
The easiest way to start working with course materials is to visit Kaggle Dataset [mlcourse.ai](https://www.kaggle.com/kashnitsky/mlcourse) and fork some Kernels (please keep them private). All your Jupyter notebooks with Anaconda (including `NumPy`, `Pandas`, `Sklearn` etc) are live and running in your browser. However, uploading data sets might be tiresome.

#### Pip & Anaconda
Most python packages like  `NumPy`, `Pandas` or  `Sklearn` can be installed manually with `pip` – python installer. However, the preferred option is to use Anaconda. Additionally, you'll need `Xgboost`, `Vowpal Wabbit` and (maybe) `LightGBM` and `CatBoost` for competitions. 

#### Docker
All necessary software is already installed and distributed in a form of a [Docker container](https://hub.docker.com/r/festline/mlcourse_open/). Instruction:

 - install [Docker](https://docs.docker.com/engine/installation/)
 - in case of Windows you might need to [turn on virtualization](http://www.sysprobs.com/disable-enable-virtualization-technology-bios) in BIOS
 - clone and download the [mlcourse.ai](https://github.com/Yorko/mlcourse.ai) repository
 - cd in terminal into `mlcourse.ai`
 - execute `python run_docker_jupyter.py`. First time it might take 5-10 minutes
 - optionally, you can add some more installations to the [Dockerfile](https://github.com/Yorko/mlcourse_open/blob/master/Dockerfile) file, build locally the Docker image (`docker build -t <tag_name> .`) and run `python run_docker_jupyter.py -t <tag_name>`
 - go to `localhost:4545`
 - execute all cells in notebook [check_docker.ipynb](https://github.com/Yorko/mlcourse_open/blob/master/docker_files/check_docker.ipynb) to make sure all the libraries are installed and work fine

Typically, Docker containers need a lot of disk space
- *docker ps* – list all containers
- *docker stop $(docker ps -a -q)* – stop all containers
- *docker rm $(docker ps -a -q)* – remove all containers
- *docker images* - list all docker images
- *docker rmi \<image_id\>* – remove a docker image

Docker [documentation](https://docs.docker.com/engine/getstarted/) is full of concise and clear examples. 

#### Jupyter
Regardless of the environment (pip, Azure/Kaggle Kernels or Docker), you'll work with Jupyter notebooks. If new to this, take a look at [jupyter.org](http://jupyter.org/). In a nutshell, this is a way of mixing code, graphics, markdown, latex etc. in single development environment. Perfect for sharing your work/ideas, for prototyping and for working with educative materials. 

To start working with course materials (i.e. Jupyter notebooks), download/clone this repo and run `jupyter-notebook` from the downloaded directory mlcourse.ai.

## DevOps
Apart from installing the environemnt, it's highly recommended that you familirize yourself with GitHub and bash. 

