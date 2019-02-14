---
layout: archive
permalink: /
title: "Open Machine Learning Course mlcourse.ai"
image:
  teaser: ods_logo.jpg
comments: false
    
---

<img src='../images/ods_stickers.jpg' align='center'>

[mlcourse.ai](https://mlcourse.ai) is an open Machine Learning course by OpenDataScience. The course is designed to perfectly balance theory and practice. You can take part in several Kaggle Inclass competitions held during the course.

Current session: **February 11th - April 26th, 2019**. You can join at any point.

**How to start with the course:**
 - set up a local or cloud Jupyter environment (Anaconda, Kaggle Kernels, Google Colab etc): [mlcourse.ai/prerequisites](https://mlcourse.ai/prerequisites)
 - go to [mlcourse.ai/assignments](https://mlcourse.ai/assignments) and download a Jupyter notebook (click an nbviewer link -> download icon in the upper-right corner -> right click -> Save link as), further instructions are given therein (alternatively, you can pull changes from the course repo if you're familiar with git)
 - run the notebook with Jupyter, read instruction carefully, there'll be ample links to corresponding materials within our course (lectures, articles, demo assignments)
 - fill in the missing Python code, finally you'll be asked to fill in a Google quiz form. In some assignments, you'll be asked to make a submission in a Kaggle Inclass competition. You need to do it before the deadline

**How to join ODS Slack community:**
 - fill in [this form](https://docs.google.com/forms/d/1BMqcUc-hIQXa0HB_Q2Oa8vWBtGHXk8a6xo5gPnMKYKA/edit), you'll get an invitation (check your spam folder), you'll be able to login to [opendatascience.slack.com](https://opendatascience.slack.com/), check [FAQ](https://mlcourse.ai/faq) in case of problems
 - when in Slack, first check the **#mlcourse_ai_news** channel for latest announcement, then you can freely chat in the **#mlcourse_ai** channel 
 - stick to special threads (mentioned in assignments) for questions on assignments
 
 **Navigating this site:**
 - [articles](articles) - main course content, see icons below
 - [video](video) - video recordings of fall 2018 lectures 
 - [prerequisites](prerequisites) - what you need to join this course
 - [roadmap](roadmap) - plan for the ongoing course session
 - [assignments](assignments) - links to ccurrent assignments and demo version for practice
 - [tutorials](tutorials) - tutorials written be course participants
 - [resources](resources) - a list of all materials constituting the course
 - [rating](rating) - current rating and top-performers of previous sessions
 - [FAQ](faq) - Frequently Asked Questions
 - [contacts](contacts) - how to reach the course team
 - [contrib](contrib) - how you can help 
 
 **Articles**
 <br>
 
<div class="tiles">
{% for post in site.posts %}
	{% include post-grid.html %}
{% endfor %}
</div><!-- /.tiles -->
