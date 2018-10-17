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
Assignments are announced in the **#mlcourse_ai** channel in [ODS Slack team](https://opendatascience.slack.com/). Also, links to fresh assignments are provided in the Readme file of the [course repository](https://github.com/Yorko/mlcourse.ai). Deadlines are typically on Sundays, 20:59 CET. Apart from that, you can practice with demo [assignments](assignments).

# Kaggle Inclass Competition "Alice"

In the [1st  competition](https://www.kaggle.com/c/catch-me-if-you-can-intruder-detection-through-webpage-session-tracking2) you'll be solving a task of user identification using tracking of his/her visited websites. Let’s call this competition "Alice", because we'll be classifying whether a person is Alice (intruder) or somebody else (innocent users). The competition is held in cooperation with Yandex and MIPT specialization "Machine Learning and Data Analysis" (in Russian).

## Rules:

- Deadline for submissions is December 14, 2018
- You can make maximum 5 submissions a day, and the competition is individual (that is, 1 person per team, team merges are not allowed)
- In case you want to get credits, you need to rename your team (of 1 person) in full accordance with your name in the course [rating](https://docs.google.com/spreadsheets/d/19AGEhUQUol6_kNLKSzBsjcGUU3qWy3BNUg8x8IFkO3Q/edit?usp=sharing)
- if you overfitted and plunged several positions down on the private LB -  no offense, it's life. Only private LB is used to calculate credits
- Until the end of December 18, those who managed to beat all benchmarks must upload their reproducible solutions in the .py format (python script) [here](https://www.dropbox.com/request/hhY96sNGMpphOf4oXC8r)
- The results of the competition and the final course rating will be published on December 21, 2018.

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

# Project  “Alice“

This is a 6-week long project with lots of instructions in a form of [Jupyter notebooks](https://github.com/Yorko/mlcourse.ai/tree/master/jupyter_english/project_alice). You'd better choose this one if you don't have cool ideas for an individual project.

The task is to identify a user on the Internet by analysing his/her websessions. This project is an extended version of the "Alice" competition. It's really extended - it includes data preparation, some statistical hypotheses testing, working with Vowpal Wabbit etc.
 
## Plan:

 - Week 1. Data preparation, [nbviewer](notebooks/blob/master/jupyter_english/project_alice/week1_prepare_dataset.ipynb). The first part of the project is devoted to preparing data for further descriptive analysis and building predictive models. It will be necessary to write some code for data preprocessing (web sites visits are labeled for each user in a separate data file) and training set generation. Also in this part we will introduce sparse data format (Scipy.sparse matrices), which is well suited for this task.
 - Week 2. Data preparation, analysis, and hypothesis testing,  [nbviewer](notebooks/blob/master/jupyter_english/project_alice/week2_analysis_hypotheses.ipynb). In the second week, we will go on with data preparation. Specifically, earlier we determined that a session is a sequence of 10 sites visited by a user, now we will make session length a parameter, to be further tuned. We will also get acquainted with the preprocessed data and statistically check first hypotheses related to our observations. This part will require a detour into statistics. 
 - Week 3. Visual data analysis, and feature engineering, [nbviewer](notebooks/blob/master/jupyter_english/project_alice/week3_visual_analysis_and_fe.ipynb). We'll create some nice features, then you'll engineer your own ones. 
 - Week 4. Model selection (notebook to appear in November). Here we will finally come to training of classification models. We'll perform cross-validation and choose best model along with its hyperparameters. Also, for the selected algorithm, we'll plot validation curves (how classification accuracy depends on hyperparameters of the algorithm) and learning curves (how classification accuracy depends on the training set size).
 - Week 5. Online learning with SGD (notebook to appear in November). Here we recall a concept of Stochastic Gradient Descent and try out Scikit-learn's SGDClassifier class, which works much faster on large dataset than the algorithms we tested in week 4. We will also beat a simple baseline in one more Kaggle Inclass competitions (the same as "Alice", but with multi-class).
 - Week 6. Vowpal Wabbit (notebook to appear in November). Here we'll try out this fascinating library in multi-class user identification task.

## Rules:

- You can choose between Project "Alice" or your own individual project (credits will be given for only one of them). It means that this project is mostly for those who'll prefer more guidance while working on a project  
- The project duration is 6 weeks, notebooks are [here](https://github.com/Yorko/mlcourse.ai/tree/master/jupyter_english/project_alice). You'll need to fill in webforms just as in our assignments.
- You'll get up to 30 credits for the whole project, i.e for 6 filled-in webforms. 
- No peer-review here, no solutions sharing
- Along with the project, you are supposed to take part in the "Alice" competition. You can get no more than 40 credits for both project and competition combined. The formula is simple: the sum of credits for project and competition capped at 40 when exceeded.
- Some of you may have taken this project as a Capstone in Yandex and MIPT Specialization. Please, don't take it once more. And yeah, we are not going to check this, up to you.

# Kaggle Inclass Competition "Medium"

[Kaggle Inclass](https://www.kaggle.com/c/how-good-is-your-medium-article/). Here you are proposed to predict popularity (number of claps) of an article on Medium.com. Rules are the same as for "Alice" competition, only the webform for uploading solutions .py files is [different](https://www.dropbox.com/request/FlY4ES4kS0NzfJrqkGUL).


# Individual Projects 

This is your chance to perform data analysis and predictive modeling for one of [Kaggle datasets](https://www.kaggle.com/datasets), datasets from the UCI repository or any other source. You can use your own data as long as it's not confidential. You have to choose between this project and project "Alice". Max. 40 credits is given for an individual project. Projects will be peer-reviewed. Criteria are listed below, more info on the peer-review process will appear in November. 

## How to publish a project
1. Register the topic of your project in this [Google Document](https://goo.gl/ZzNuUN)
2. Make a Pull Request (an [instruction](https://www.digitalocean.com/community/tutorials/how-to-create-a-pull-request-on-github)) with your tutorial in a form of a Jupyter notebook [here](https://github.com/Yorko/mlcourse.ai/tree/master/jupyter_english/projects_indiv). Respect the repo structure: put images to img, ipynb file to `jupyter_english/projects_indiv`. Do not commit data to our repo. Instead, upload your data somewhere, and share a link
3. If you don't cope with these simple rules, your project is not taken into account.
4. When your Pull Request is accepted, you need to make an [nbviewer](http://nbviewer.jupyter.org/) link for your ipynb file. If you'd like to, you can also share the link in the #mlcourse_ai Slack channel with a short description of your project. However, it's not necessary.
4. Evaluation process for individual projects is a peer-review, criteria are list below. More info on peer-review process will be provided later.

## Plan and evaluation criteria

**1. Feature and data explanation (2 points)**
- (+) The process of collecting data is described, a detailed explanation of the task is provided, its value is explained, target features are given;
- (+/-) The methods how to solve the task and how to prepare the data are explained, target features are mentioned;
- (-/+) It is said what task is being solved, data sources and target features are mentioned;
- (-) The description is not provided, only the name of the task is mentioned, for example "outflow prediction".

**2. Primary data analysis (4 points)**
- (+) The features, their interactions and influence on the target features are explained. The distribution of target feature is described (in case of regression task the results of statistical tests for normality and skewness of distribution should be added). It is explained how to work with the target feature, if necessary. The missing items in the data are examined.
- (+/-) The main part of the research with explanations is done
- (-/+) The majority of topics of the full research is not provided
- (-) Totally omitted

**3. Primary visual data analysis (4 points)**
- (+) Different visual charts (feature distribution, correlation matrix) are built with explanations how they are related to primary data analysis (2nd point); conclusions are drawn
- (+/-) Different visual charts (feature distribution, correlation matrix) are built with small mistakes in the conclusions;
- (-/+) Some important charts are missing or there are too many mistakes in conclusions;
- (-) Totally omitted

**4. Insights and found dependencies (4 points)**
- (+) The assumptions about various correlations/omissions/regularities from the previous paragraphs are found and put forward. There is an explanation why they are important for the task being solved;
- (+/-) The patterns with explanations are found and provided;
- (-/+) The patterns are found, but the importance of insights is not shown;
- (-) Totally omitted

**5. Metrics selection (3 points)**
- (+) There is a reasonable justification for the selection of the model quality metrics. The issues that affect the choice of quality metrics (solving problem, decision goal, number of classes, class imbalance, etc.) are described;
- (+/-) The description is provided, but it is incomplete or there is no connection between the justification and the decision made;
(-/+) The justification for selecting a metric is incorrect or has serious errors;
- (-) No justification of metrics selection.

**6. Model selection (3 points)**
- (+) A model selection is made. The process of selection and connection with the task being solved is described;
- (+/-) Some inaccuracies were made in the selection process, the explanation is given;
- (-/+) Serious mistakes were made during the selection process,  and/or no explanation is provided;
- (-) The model selection is not justified.

**7. Data preprocessing (4 points)**
- (+) Data for a particular model is preprocessed. If necessary, there is a description of scaling characteristics, filling in blanks, replacing strings with numbers, One-Hot Encoding, handling of outliers, selection of features with an explanation of the methods used for this. In general, the data is divided into training and hold-out sets;
- (+/-)  The description of some steps is omitted, although they appear in the code. For example, outliers are removed, but it is not commented or there are some small mistakes;
- (-/+) Some steps are omitted, for example, the scaling of features in the case of linear or metric models or highlighting of hold-out set. Or there are errors such as numeric coding (LabelEncoder) of categorical features where it is inappropriate. Even such actions may be justified, but no description is given;
- (-) Totally omitted

**8. Cross-validation and adjustment of model hyperparameters (4 points)**
- (+) Cross-validation is performed technically correct, without data leaks. The number of folds is reasonably selected and the split (Random/Stratified or otherwise) is fixed by a seed. An explanation is given. Hyperparameters of the model and the method of their selection are explained. The choice is based on some study of the model's hyperparameters for the task being solved;
- (+/-) There are small errors (for example, there is no fixed seed) or there is no explanation for cross-validation. But the hyperparameters of the model and the way they are selected are explained;
- (-/+) Cross-validation is performed with significant errors (for example, data conversion is performed on the entire sample, thus data leakage from the test part of the sample occurs and, accordingly, the result of cross-validation may be too optimistic). Hyperparameters of the model and the method of their selection are not explained;
- (-) Totally omitted

**9. Creation of new features and description of this process  (4 points)**
- (+) New features are created. Justification is given: logical (for example, birds have body temperature a few degrees higher than human, which means that virus XXX will not survive in environment like this), physical (for example, a rainbow means that the light source is located behind; calculation of the value according to physical law using these features) or another one (for example a feature is built after data visualization). Justification is reasonably described. The usefulness of new features is confirmed statistically or with the help of the corresponding model;
- (+/-) The created features are insignificant for the model used and/or there are errors in features formation. There is a justification for feature selection;
- (-/+) The created features worsen the model quality and/or there is no justification of them;
- (-) New features are not created.

**10. Plotting training and validation curves (4 points)**
- (+) Training and validation curves are built. The correct interpretation is provided;
- (+/-) Noticeable mistakes were made while building curves or the curves are not informative;
- (-/+) An incorrect interpretation is given or another serious mistakes can be found;
- (-) Training and validation curves are omitted.

**11. Prediction for test or hold-out samples (2 points)**
- (+) The results on the test sample or LB score are provided. The results on the test sample are comparable to the results on cross-validation. If the test sample was created by the author of the project, the creation mechanism should be unbiased and explained (a reasonable sampling mechanism was applied, in the simplest case - randomization);
- (+/-) The values of the metrics on the test sample do not differ enough from the values of the metrics on cross-validation and/or the test sample is biased, but there is a reasonable justification for this (example: the customer took a test sample from another distribution);
- (-/+) The values of the metrics on the test sample differ a lot from the values of the metrics on cross-validation and/or the test sample was biased;
- (-) No prediction for test or hold-out samples is provided.

**12. Conclusions (2 points)**
- (+) The value of the solution, possible cases for its application and further ways of developing and improving the solution are described;
- (+/-) The conclusions are similar to the formal description of the completed solution and there is a description of its value, along with further development plans and possible applications;
- (-/+) The conclusions are similar to the formal description of the completed solution;
- (-) The conclusions are omitted.


# Tutorials 

We propose to write and publish a tutorial on any ML/DS-related topic which is not fully covered in our course.

## Rules:

- Tutorials must be written in English. As for programming language, only Python is allowed
- It must be a tutorial (reproducible Jupyter notebook, ipynb file), i.e you should teach some skills, do not just express your ideas on some theoretical concept
- It is not just a translation of somebody else's material. You can borrow some stuff, but with fair links/citations
- The prerequisite for reading your tutorial should be basic ML as taught in [mlcourse.ai](https://mlcourse.ai). Do not write in-depth articles about neural nets, probabilistic programming, Bayesian approach, reinforcement learning etc. - topics like these need a thorough approach. That is, sure, you can write articles like that, but not in the format of [mlcourse.ai](https://mlcourse.ai) tutorials. On the other hand, it's hardly worth making a tutorial too simple (e.g., to pick some library and demonstrate only a couple of methods from it)
- A typical tutorial shall be 30-60 minutes to read and digest (however, here exceptions are possible) 
- Check out a  [list](https://github.com/Yorko/mlcourse.ai/wiki/Individual-projects-and-tutorials-(in-Russian)) of published tutorials from previous runs of this course (in Russian). Yes, it's in Russian but Google Translate can kind of give you an insight into the topics that are already covered. For those who already passed the course: definitely, translating somebody else's (or your own) tutorial into English is not going to work
- You are not allowed to pick the same topic for an individual project and a tutorial

## How to publish a tutorial

1. First of all, choose a unique topic and registed it in the [Google doc](https://docs.google.com/spreadsheets/d/15qao-tn6V7JXy2bWUasWy-yOXDm8xW8ZtPXfdJnO-v4/edit?usp=sharing)
2. Make a Pull Request (an [instruction](https://www.digitalocean.com/community/tutorials/how-to-create-a-pull-request-on-github)) with your tutorial in a form of a Jupyter notebook [here](https://github.com/Yorko/mlcourse.ai/tree/master/jupyter_english/tutorials). Respect the repo structure: put images to img, ipynb file to `jupyter_english/tutorials`. Do not commit data to our repo. Instead, upload your data somewhere, and share a link
3. If you don't cope with these simple rules, your tutorial is not taken into account.
4. When your Pull Request is accepted, you need to make an [nbviewer](http://nbviewer.jupyter.org/) link for your ipynb file and share the link in the #mlcourse_ai Slack channel with a short description of the tutorial. You also need to add the *#tutorial_contest* tag, It's obligatory, otherwise, the tutorial will be ignored.

*Tutorial submission is due on December 13th.* 

## Grading tutorials
Grading is solely done by other participants voting with :heavy_plus_sign: in Slack. Best tutorials will get up to 40 credits. The exact grading formula is to be provided later. *Voting is finalised on December 20th.*




