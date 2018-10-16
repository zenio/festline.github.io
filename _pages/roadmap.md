---
layout: article
permalink: /roadmap
title: "Roadmap"
comments: false
share: false
image:
  teaser: teaser-roadmap.png
---
Here you can find all activities for which you can get credits in 2018 fall session of [mlcourse.ai](https://mlcourse.ai). Current student rating is [here](https://docs.google.com/spreadsheets/d/19AGEhUQUol6_kNLKSzBsjcGUU3qWy3BNUg8x8IFkO3Q/edit?usp=sharing). Google [calendar](https://calendar.google.com/calendar?cid=Z25pZ3EwZGxxb2I5cDZwMWptam5rdmY3NWtAZ3JvdXAuY2FsZW5kYXIuZ29vZ2xlLmNvbQ) with all deadlines, static .ics [file](https://drive.google.com/open?id=1xRRt7Saz1Rxc3zVKbovuT_6ibQr9lMVJ).

# Plan
- Assignments
- Kaggle Inclass Competition "Alice"
- Project "Alice"
- Kaggle Inclass Competition "Medium"
- Individual Projects
- Tutorials

# Assignments
Are announced in the**#mlcourse_ai** channel in [ODS Slack team](https://opendatascience.slack.com/). Also, links to fresh assignments are provided in the Readme file of the [course repository](https://github.com/Yorko/mlcourse.ai). Deadlines are typically on Sundays, 20:59 CET. Apart from that, you can practice with demo assignments. See tab [assignments](assignments).

# Kaggle Inclass Competition "Alice"

In the 1st  [competition](https://www.kaggle.com/c/catch-me-if-you-can-intruder-detection-through-webpage-session-tracking2) you'll be solving the task of user identification tracking his/her sequence of visited websites. Lets call it "Alice", because we'll be classifying whether a person is some Alice or somebody else. The competition is held in cooperation with Yandex and MIPT specialization "Machine Learning and Data Analysis" (in Russian).

Rules:
- Deadline for submissions is December 14, 2018
- You can make maximum 5 submissions a day, and the competition is individual (that is, 1 person per team, team merges are not allowed)
- In case you want to get credits, you need to rename your team (of 1 person) in full accordance with your name in course [rating](https://docs.google.com/spreadsheets/d/19AGEhUQUol6_kNLKSzBsjcGUU3qWy3BNUg8x8IFkO3Q/edit?usp=sharing)
- if you overfitted and dropped several positions down on private LB, no offense, it's life, only private LB is used to calculate credits
- Up to December 18, those who managed to beat all benchmarks should upload their reproducible solutions in the .py format (python script) [here](https://www.dropbox.com/request/hhY96sNGMpphOf4oXC8r)
- The results of the competition and the final course rating will be published on December 21, 2018.

Scoring rules for competitions (Alice & Medium):
1. Necessary conditions:
   - Beat all Yorko's baselines on private LB
   - A reproducible solution should be submitted in a specified period
   - Team name exactly corresponding to some entry in the course rating 
2. - 1 place – 40 credits
   - 2 place – 30 credits
   - 3 place – 25 credits
   - 4-10 place – 20 credits

# Project  “Alice“
This is a 6-week long project with lots of instructions in a form of [Jupyter notebooks](https://github.com/Yorko/mlcourse.ai/tree/master/jupyter_english/project_alice), you'd better choose this one if you don't have cool ideas for an individual project.

The task is to identify a user on the Internet by tracking his/her websessions. This project is an extended version of competition "Alice". It's really extended - it includes data preparation, some statistical hypotheses testing, working with Vowpal Wabbit etc.
 
Plan:
 - Week 1. Data preparation, [nbviewer](notebooks/blob/master/jupyter_english/project_alice/week1_prepare_dataset.ipynb). The first part of the project is devoted to preparing data for further descriptive analysis and building predictive models. It will be necessary to write code for data preprocessing (the initially visited web sites are indicated for each user in a separate file) and training set generation. Also in this part we will introduce the sparse data format (Scipy.sparse matrices), which is well suited for this task.
 - Week 2. Data preparation, analysis, and hypothesis testing, [nbviewer](notebooks/blob/master/jupyter_english/project_alice/week2_analysis_hypotheses.ipynb). In the second week, we will go on with data preparation. Specifically, earlier we determined that the session is a sequence of 10 sites visited by the user, now we will make the session length a parameter, and to be further tuned. We will also get acquainted with the preprocessed data and statistically check the first hypotheses related to our observations. This part will require a detour into statistics. 
 - Week 3. Visual data analysis, and feature engineering, [nbviewer](notebooks/blob/master/jupyter_english/project_alice/week3_visual_analysis_and_fe.ipynb). We'll create some nice features, then you'll engineer your own ones. 
 - Week 4. Model selection (notebook to appear in November). Here we will finally come to training of classification models.We'll perform cross-validation and choose best model along with its hyperparameters. Also, for the selected algorithm, we'll build validation curves (how classification accuracy depends on hyperparameters of the algorithm) and learning curves (how classification accuracy depends on the training set size).
 - Week 5. Online learning with SGD (notebook to appear in November). Here we recall the concept of stochastic gradient descent and try out Scikit-learn's SGDClassifier classifier, which works much faster on large dataset than the algorithms we tested in week 4. We will also beat a simple baseline in one more Kaggle Inclass competitions (the same as "Alice", but with multi-class).
 - Week 6. Vowpal Wabbit (notebook to appear in November). Here we'll try out this fascinating library in multi-class user indentification task.

Rules:
- You can choose between Project "Alice" or your own indiviual project (credits will be given for only one of them). It means that this project is mostly for those who'll prefer more guidence while working on a project  
- The project duration is 6 weeks, notebooks are found [here](https://github.com/Yorko/mlcourse.ai/tree/master/jupyter_english/project_alice), you'll need to fill in webforms just as in our assignments.  
- You'll get up to 30 credits for the whole project, i.e for 6 filled-in webforms. 
- No peer-review here, no solutions shared
- Along with the project, you are supposed to take part in the "Alice" competition. You can get no more than 40 credits for project and competition. The formula is simple: minimum of 40 and the sum of credits for project and competition. 
- Some of you may have taken this project as a Capstone in Yandex and MIPT Specialization. Please, don't take it once more. And yeah, we are not going to check this, up to you.

# Kaggle Inclass Competition "Medium"
[Kaggle Inclass](https://www.kaggle.com/c/how-good-is-your-medium-article/). Here you are proposed to predict popularity (number of claps) of an article on Medium. Rules are the same as for Competition "Alice", only the webform for solution .py files is [another one](https://www.dropbox.com/request/FlY4ES4kS0NzfJrqkGUL).


# Individual Projects 

Your own project for the whole run of the course. Clear instructions, peer review in the end. Up to 40 credits. More info to appear soon.


# Tutorials 

You can write your own tutorial practically on any topic around ML & DS. Up to 40 credits. More info to appear soon.
