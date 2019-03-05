---
layout: article
permalink: /roadmap
title: "Roadmap"
comments: false
share: false
image:
  teaser: teaser-roadmap.png
---

<img src='../images/teaser-roadmap.png'>

All activities accounted for in spring 2019 [rating](https://drive.google.com/open?id=1LAy1eK8vIONzIWgcCEaVmhKPSj579zK5lrECf_tQT60). 

# Plan
- Calendar and deadlines
- Assignments
- Kaggle Inclass Competition "Alice"
- Kaggle Inclass Competition "Medium"
- 2 more Kaggle competitions
- Tutorials

# Calendar and deadlines
[Google Calendar](https://calendar.google.com/calendar?cid=Z25pZ3EwZGxxb2I5cDZwMWptam5rdmY3NWtAZ3JvdXAuY2FsZW5kYXIuZ29vZ2xlLmNvbQ) with all deadlines.

Current deadlines (see also the [assignments](assignments) page):
 - February 24 - A1
 - March 10 - A2
 - March 17 - uploading solutions to Alice & Medium 

All deadlines are 20:59 UTC (London time). 

# Assignments
Assignments are announced in the **#mlcourse_ai** channel in [ODS Slack team](https://opendatascience.slack.com/) (pinned items). Also, links to fresh assignments are provided in the Readme file of the [course repository](https://github.com/Yorko/mlcourse.ai) and on [mlcourse.ai/assignments](assignments). Deadlines are typically on Sundays, 20:59 UTC. Apart from that, you can practice with demo [assignments](assignments), don't confuse them with "real" ones. Rough plan for spring 2019 assignments is the folowing:
 - A1. Pandas and exploratory data analysis
 - A2. Beating baselines in Alice & Medium competitions
 - A3. Decision trees, random forest, and gradient boosting. Beating baseline in one more competition
 - A4. Time series analysis with Python
 - A5. Vowpal Wabbit
 - A6. Beating baseline in one more competition
 
If stuck with assignments, check course [video lectures](video).

# Kaggle Inclass Competition "Alice"

In the [1st competition](https://www.kaggle.com/c/catch-me-if-you-can-intruder-detection-through-webpage-session-tracking2) you'll be solving a task of user identification using tracking of his/her visited websites. Let’s call this competition "Alice", because we'll be classifying whether a person is Alice (let's say, intruder) or somebody else (innocent users). The competition is held in cooperation with Yandex and MIPT specialization "Machine Learning and Data Analysis" (in Russian).

## Rules:

- Deadline for submissions 2019 March 10th
- You can make maximum 5 submissions a day, and the competition is individual (that is, 1 person per team, team merges are not allowed)
- In case you want to get credits, you need to rename your team (of 1 person) in full accordance with your name in the course [rating](https://drive.google.com/open?id=1LAy1eK8vIONzIWgcCEaVmhKPSj579zK5lrECf_tQT60)
- if you overfitted and plunged several positions down on the private LB - no offense, it's life. Only private LB is used to calculate final credits (that's not true for baselines in A2, check instructions therein)
- Till March 17th, those who managed to beat all benchmarks must upload their reproducible solutions in the .py format (python script) [here](https://www.dropbox.com/request/i4HUVdwQWTSUtfUEJndV), more details are provided in [this post](https://opendatascience.slack.com/archives/C39147V60/p1551744009070400) (dated March 5th) in the #mlcourse_ai_news channel
- The results of the competition and the final course rating will be published on 2019 April 26th.

## Scoring rules for competitions (Alice & Medium):

### Necessary conditions:
   - Beat all Yorko's baselines on the private LB
   - A reproducible solution must be submitted within the specified period
   - Team name must exactly correspond to the name in the course rating 

### Credits: 
   - 1 place – 40 credits
   - 2 place – 30 credits
   - 3 place – 25 credits
   - 4-10 place – 20 credits

# Kaggle Inclass Competition "Medium"

[Kaggle Inclass](https://www.kaggle.com/c/how-good-is-your-medium-article/). Here you are proposed to predict popularity (number of claps) of an article on Medium.com. Rules are the same as for "Alice" competition, only the webform for uploading solutions .py files is [different](https://www.dropbox.com/request/0iLhMirOekk2QV98Mj2B).

# 2 more Kaggle competitions
TBA

# Tutorials 

We propose to write and publish a tutorial on any ML/DS-related topic which is not fully covered in our course.

## Rules:

- Tutorials must be written in English. As for programming language, only Python is allowed
- It must be a tutorial (reproducible Jupyter notebook, ipynb file), i.e you should teach some skills, do not just express your ideas on some theoretical concept
- It is not just a translation of somebody else's material. You can borrow some stuff, but with fair links/citations
- The prerequisite for reading your tutorial should be basic ML as taught in [mlcourse.ai](https://mlcourse.ai). Do not write in-depth articles about neural nets, probabilistic programming, Bayesian approach, reinforcement learning etc. - topics like these need a thorough approach. That is, sure, you can write articles like that, but not in the format of [mlcourse.ai](https://mlcourse.ai) tutorials. On the other hand, it's hardly worth making a tutorial too simple (e.g., to pick some library and demonstrate only a couple of methods from it)
- A typical tutorial shall be 30-60 minutes to read and digest (however, here exceptions are possible) 
- Check out these lists of published tutorials from previous runs of this course: [English](tutorials), [Russian](https://github.com/Yorko/mlcourse.ai/wiki/Individual-projects-and-tutorials-(in-Russian)) . Yes, the second list is in Russian but still Google Translate can kind of give you an insight into the topics that are already covered. For those who already passed the course: definitely, translating somebody else's (or your own) tutorial into English is not going to work
- Tutorial submission is due on 2019 April 22nd

## How to publish a tutorial

1. First of all, choose a unique topic and registed it in the [Google doc](https://docs.google.com/spreadsheets/d/1oURFd4G--FyCP-mj8Dc5y0jAo_uJ3d3f5ljjcQDLZsc/edit?usp=sharing)
2. Create a Kaggle Kernel with your tutorial [here](https://inclass.kaggle.com/kashnitsky/mlcourse/kernels) (and of course do upvote all kernels that you find useful)
3. Make sure your Kernel runs normally and produces no errors
4. Then share the link to your Kernel in the #mlcourse_ai Slack channel with a short description of the tutorial. You also need to add the *#tutorial* tag, It's obligatory, otherwise, the tutorial will be ignored.

For discussions, please stick to [ODS Slack](https://opendatascience.slack.com), channel #mlcourse_ai, pinned thread **#tutorial.**

## Grading tutorials
Grading is solely done by other participants upvoting Kernels on Kaggle in the mlcourse.ai [Kaggle Dataset](https://inclass.kaggle.com/kashnitsky/mlcourse/kernels). Best tutorials will get up to 40 credits. The exact grading formula is to be provided later. Voting is finalised on 2019 April 26th.




