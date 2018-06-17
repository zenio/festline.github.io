---
layout: article
title: "Exploratory data analysis with Pandas"
image:
  teaser: 180522-teaser.png
---

<img align="center" src="https://habrastorage.org/files/10c/15f/f3d/10c15ff3dcb14abdbabdac53fed6d825.jpg"/>
<br>


### Plan of this article
 1. [About the course](http://localhost:8888/notebooks/jupyter_english/topic01/%5BENG%5D_topic1_habr_pandas.ipynb#1.-About-the-course)
 2. [Assignments](http://localhost:8888/notebooks/jupyter_english/topic01/%5BENG%5D_topic1_habr_pandas.ipynb#2.-Assignments)
 3. [Demonstration of main Pandas methods](http://localhost:8888/notebooks/jupyter_english/topic01/%5BENG%5D_topic1_habr_pandas.ipynb#3.-Demonstration-of-main-Pandas-methods)
 4. [First attempt on predicting telecom churn](http://localhost:8888/notebooks/jupyter_english/topic01/%5BENG%5D_topic1_habr_pandas.ipynb#4.-First-attempt-on-predicting-telecom-churn)
 5. [Assignment #1](http://localhost:8888/notebooks/jupyter_english/topic01/%5BENG%5D_topic1_habr_pandas.ipynb#5.-Assignment-#1)
 6. [Useful resources](http://localhost:8888/notebooks/jupyter_english/topic01/%5BENG%5D_topic1_habr_pandas.ipynb#6.-Useful-resources)


## 1. About the course

With this article, we, [OpenDataScience](https://www.linkedin.com/company/11241268/), launch an open Machine Learning course. This is not aimed at developing another *comprehensive* introductory course on machine learning or data analysis (so this is not a substitute for fundamental education or online/offline courses/specializations and books). The purpose of this series of articles is to quickly refresh your knowledge and help you find topics for further advancement. Our approach is similar to that of the authors of [Deep Learning book](http://www.deeplearningbook.org/), which starts off with a review of mathematics and basics of machine learning – short, concise, and with many references to other resources. 

The course is designed to perfectly balance theory and practice; therefore, each topic is followed by an **assignment** with a deadline in a week. You can also take part in several Kaggle Inclass **competitions** held during the course.

### Syllabus
1. Exploratory data analysis with Pandas
1. Visual data analysis with Python
1. Classification, Decision Trees, and k Nearest Neighbors
1. Linear Classification and Regression
1. Bagging and Random Forest
1. Feature engineering and feature selection
1. Unsupervised Learning: Principal Component Anslysis and Clustering
1. Vowpal Wabbit: Learning with gigabytes of data
1. Time series analysis with Python
1. Gradient Boosting

### Community

One of the most vivid advantages of our course is active community. If you join the OpenDataScience Slack team, you’ll find the authors of articles and assignments right there in the same channel (#eng_mlcourse_open) eager to help you. This can help very much when you make your first steps in any discipline. Fill in [this form](https://docs.google.com/forms/d/1lejiyldtlHxwwDpWiEqFmaUFUOVfkm9BMjoZurR895c/edit) to be invited. The form will ask you several questions about your background and skills, including a few easy math questions.

We chat informally, like humor and emoji. Not every MOOC can boast to have such an alive community. There is also a [subreddit](https://www.reddit.com/r/ods_ai/) designed for students participating in the course.

### Prereqiusites
The prerequisites are the following: basic concepts from calculus, linear algebra, probability theory and statistics, and Python programming skills. If you need to catch up, a good resource will be [Part I](http://www.deeplearningbook.org/contents/part_basics.html) from the "Deep Learning" book and various math and Python online courses (for Python, CodeAcademy will do). More info is available on the corresponding [Wiki page](https://github.com/Yorko/mlcourse_open/wiki/Prerequisites:-Python,-math-and-DevOps).

### What software you’ll need
As for now, you’ll only need [Anaconda](https://www.continuum.io/downloads) (built with Python 3.6) to reproduce the code in the course. Later in the course, you’ll have to install other libraries like Xgboost and Vowpal Wabbit.

You can also resort to the [Docker container](https://hub.docker.com/r/festline/mlcourse_open/) with all necessary software already installed. More info is available on the corresponding [Wiki page](https://github.com/Yorko/mlcourse_open/wiki/Software-requirements-and-Docker-container).


## 2. Assignments

- Each article comes with an assignment in the form of a [Jupyter](http://jupyter.org) notebook. The task will be to fill in the missing code snippets and to answer questions in a Google Quiz form;
- Each assignment is due in a week with a hard deadline;
- Please discuss the course content (articles and assignments) in the #eng_mlcourse_open cahnnel of the OpenDataScience Slack team or here in the comments to articles on Medium;
- The solutions to assignments will be sent to those who have submitted the corresponding Google form.

## 3. Demonstration of main Pandas methods 

Well.. There are dozens of cool tutorials on Pandas and visual data analysis. If you are familiar with these topics, just wait for the 3rd article in the series, where we get into machine learning.  

**[Pandas](http://pandas.pydata.org)** is a Python library that provides extensive means for data analysis. Data scientists often work with data stored in table formats like `.csv`, `.tsv`, or `.xlsx`. Pandas makes it very convenient to load, process, and analyze such tabular data using SQL-like queries. In conjunction with `Matplotlib` and `Seaborn`, `Pandas` provides a wide range of opportunities for visual analysis of tabular data.

The main data structures in `Pandas` are implemented with **Series** and **DataFrame** classes. The former is a one-dimensional indexed array of some fixed data type. The latter is a two-dimensional data structure - a table - where each column contains data of the same type. You can see it as a dictionary of `Series` instances. `DataFrames` are great for representing real data: rows correspond to instances (objects, observations, etc.), and columns correspond to features for each of the instances.



```python
import numpy as np
import pandas as pd
# we don't like warnings
# you can comment the following 2 lines if you'd like to
import warnings
warnings.filterwarnings('ignore')
```


We’ll demonstrate the main methods in action by analyzing a [dataset](https://bigml.com/user/francisco/gallery/dataset/5163ad540c0b5e5b22000383) on the churn rate of telecom operator clients. Let’s read the data (using `read_csv`), and take a look at the first 5 lines using the `head` method:



```python
df = pd.read_csv('../../data/telecom_churn.csv')
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>State</th>
      <th>Account length</th>
      <th>Area code</th>
      <th>International plan</th>
      <th>Voice mail plan</th>
      <th>Number vmail messages</th>
      <th>Total day minutes</th>
      <th>Total day calls</th>
      <th>Total day charge</th>
      <th>Total eve minutes</th>
      <th>Total eve calls</th>
      <th>Total eve charge</th>
      <th>Total night minutes</th>
      <th>Total night calls</th>
      <th>Total night charge</th>
      <th>Total intl minutes</th>
      <th>Total intl calls</th>
      <th>Total intl charge</th>
      <th>Customer service calls</th>
      <th>Churn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>KS</td>
      <td>128</td>
      <td>415</td>
      <td>No</td>
      <td>Yes</td>
      <td>25</td>
      <td>265.1</td>
      <td>110</td>
      <td>45.07</td>
      <td>197.4</td>
      <td>99</td>
      <td>16.78</td>
      <td>244.7</td>
      <td>91</td>
      <td>11.01</td>
      <td>10.0</td>
      <td>3</td>
      <td>2.70</td>
      <td>1</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>OH</td>
      <td>107</td>
      <td>415</td>
      <td>No</td>
      <td>Yes</td>
      <td>26</td>
      <td>161.6</td>
      <td>123</td>
      <td>27.47</td>
      <td>195.5</td>
      <td>103</td>
      <td>16.62</td>
      <td>254.4</td>
      <td>103</td>
      <td>11.45</td>
      <td>13.7</td>
      <td>3</td>
      <td>3.70</td>
      <td>1</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NJ</td>
      <td>137</td>
      <td>415</td>
      <td>No</td>
      <td>No</td>
      <td>0</td>
      <td>243.4</td>
      <td>114</td>
      <td>41.38</td>
      <td>121.2</td>
      <td>110</td>
      <td>10.30</td>
      <td>162.6</td>
      <td>104</td>
      <td>7.32</td>
      <td>12.2</td>
      <td>5</td>
      <td>3.29</td>
      <td>0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OH</td>
      <td>84</td>
      <td>408</td>
      <td>Yes</td>
      <td>No</td>
      <td>0</td>
      <td>299.4</td>
      <td>71</td>
      <td>50.90</td>
      <td>61.9</td>
      <td>88</td>
      <td>5.26</td>
      <td>196.9</td>
      <td>89</td>
      <td>8.86</td>
      <td>6.6</td>
      <td>7</td>
      <td>1.78</td>
      <td>2</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OK</td>
      <td>75</td>
      <td>415</td>
      <td>Yes</td>
      <td>No</td>
      <td>0</td>
      <td>166.7</td>
      <td>113</td>
      <td>28.34</td>
      <td>148.3</td>
      <td>122</td>
      <td>12.61</td>
      <td>186.9</td>
      <td>121</td>
      <td>8.41</td>
      <td>10.1</td>
      <td>3</td>
      <td>2.73</td>
      <td>3</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>



<details>
<summary>About printing DataFrames in Jupyter notebooks</summary>
<p>
In Jupyter notebooks, Pandas DataFrames are printed as these pretty tables seen above while `print(df.head())` looks worse.
By default, Pandas displays 20 columns and 60 rows, so, if your DataFrame is bigger, use the `set_option` function as shown in the example below:

```python
pd.set_option('display.max_columns', 100)
pd.set_option('display.max_rows', 100)
```
</p>
</details>

Recall that each row corresponds to one client, the **object** of our research, and columns are **features** of the object.

**Let’s have a look at data dimensionality, features names, and feature types.**


```python
print(df.shape)
```

    (3333, 20)


From the output, we can see that the table contains 3333 rows and 20 columns.

Now let’s try printing out the column names using `columns`:


```python
print(df.columns)
```

    Index(['State', 'Account length', 'Area code', 'International plan',
           'Voice mail plan', 'Number vmail messages', 'Total day minutes',
           'Total day calls', 'Total day charge', 'Total eve minutes',
           'Total eve calls', 'Total eve charge', 'Total night minutes',
           'Total night calls', 'Total night charge', 'Total intl minutes',
           'Total intl calls', 'Total intl charge', 'Customer service calls',
           'Churn'],
          dtype='object')


We can use the `info()` method to output some general information about the dataframe: 


```python
print(df.info())
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 3333 entries, 0 to 3332
    Data columns (total 20 columns):
    State                     3333 non-null object
    Account length            3333 non-null int64
    Area code                 3333 non-null int64
    International plan        3333 non-null object
    Voice mail plan           3333 non-null object
    Number vmail messages     3333 non-null int64
    Total day minutes         3333 non-null float64
    Total day calls           3333 non-null int64
    Total day charge          3333 non-null float64
    Total eve minutes         3333 non-null float64
    Total eve calls           3333 non-null int64
    Total eve charge          3333 non-null float64
    Total night minutes       3333 non-null float64
    Total night calls         3333 non-null int64
    Total night charge        3333 non-null float64
    Total intl minutes        3333 non-null float64
    Total intl calls          3333 non-null int64
    Total intl charge         3333 non-null float64
    Customer service calls    3333 non-null int64
    Churn                     3333 non-null bool
    dtypes: bool(1), float64(8), int64(8), object(3)
    memory usage: 498.1+ KB
    None



`bool`, `int64`, `float64` and `object` are the data types of our features. We see that one feature is logical (`bool`), 3 features are of type `object`, and 16 features are numeric. With this same method, we can easily see if there are any missing values. Here, there are none because each column contains 3333 observations, the same number of rows we saw before with `shape`.

We can **change the column type** with the `astype` method. Let’s apply this method to the `Churn` feature to convert it into `int64`:



```python
df['Churn'] = df['Churn'].astype('int64')
```


The `describe` method shows basic statistical characteristics of each numerical feature (`int64` and `float64` types): number of non-missing values, mean, standard deviation, range, median, 0.25 and 0.75 quartiles.


```python
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Account length</th>
      <th>Area code</th>
      <th>Number vmail messages</th>
      <th>Total day minutes</th>
      <th>Total day calls</th>
      <th>Total day charge</th>
      <th>Total eve minutes</th>
      <th>Total eve calls</th>
      <th>Total eve charge</th>
      <th>Total night minutes</th>
      <th>Total night calls</th>
      <th>Total night charge</th>
      <th>Total intl minutes</th>
      <th>Total intl calls</th>
      <th>Total intl charge</th>
      <th>Customer service calls</th>
      <th>Churn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
      <td>3333.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>101.064806</td>
      <td>437.182418</td>
      <td>8.099010</td>
      <td>179.775098</td>
      <td>100.435644</td>
      <td>30.562307</td>
      <td>200.980348</td>
      <td>100.114311</td>
      <td>17.083540</td>
      <td>200.872037</td>
      <td>100.107711</td>
      <td>9.039325</td>
      <td>10.237294</td>
      <td>4.479448</td>
      <td>2.764581</td>
      <td>1.562856</td>
      <td>0.144914</td>
    </tr>
    <tr>
      <th>std</th>
      <td>39.822106</td>
      <td>42.371290</td>
      <td>13.688365</td>
      <td>54.467389</td>
      <td>20.069084</td>
      <td>9.259435</td>
      <td>50.713844</td>
      <td>19.922625</td>
      <td>4.310668</td>
      <td>50.573847</td>
      <td>19.568609</td>
      <td>2.275873</td>
      <td>2.791840</td>
      <td>2.461214</td>
      <td>0.753773</td>
      <td>1.315491</td>
      <td>0.352067</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>408.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>23.200000</td>
      <td>33.000000</td>
      <td>1.040000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>74.000000</td>
      <td>408.000000</td>
      <td>0.000000</td>
      <td>143.700000</td>
      <td>87.000000</td>
      <td>24.430000</td>
      <td>166.600000</td>
      <td>87.000000</td>
      <td>14.160000</td>
      <td>167.000000</td>
      <td>87.000000</td>
      <td>7.520000</td>
      <td>8.500000</td>
      <td>3.000000</td>
      <td>2.300000</td>
      <td>1.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>101.000000</td>
      <td>415.000000</td>
      <td>0.000000</td>
      <td>179.400000</td>
      <td>101.000000</td>
      <td>30.500000</td>
      <td>201.400000</td>
      <td>100.000000</td>
      <td>17.120000</td>
      <td>201.200000</td>
      <td>100.000000</td>
      <td>9.050000</td>
      <td>10.300000</td>
      <td>4.000000</td>
      <td>2.780000</td>
      <td>1.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>127.000000</td>
      <td>510.000000</td>
      <td>20.000000</td>
      <td>216.400000</td>
      <td>114.000000</td>
      <td>36.790000</td>
      <td>235.300000</td>
      <td>114.000000</td>
      <td>20.000000</td>
      <td>235.300000</td>
      <td>113.000000</td>
      <td>10.590000</td>
      <td>12.100000</td>
      <td>6.000000</td>
      <td>3.270000</td>
      <td>2.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>243.000000</td>
      <td>510.000000</td>
      <td>51.000000</td>
      <td>350.800000</td>
      <td>165.000000</td>
      <td>59.640000</td>
      <td>363.700000</td>
      <td>170.000000</td>
      <td>30.910000</td>
      <td>395.000000</td>
      <td>175.000000</td>
      <td>17.770000</td>
      <td>20.000000</td>
      <td>20.000000</td>
      <td>5.400000</td>
      <td>9.000000</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>



In order to see statistics on non-numerical features, one has to explicitly indicate data types of interest in the `include` parameter.


```python
df.describe(include=['object', 'bool'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>State</th>
      <th>International plan</th>
      <th>Voice mail plan</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>3333</td>
      <td>3333</td>
      <td>3333</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>51</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>top</th>
      <td>WV</td>
      <td>No</td>
      <td>No</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>106</td>
      <td>3010</td>
      <td>2411</td>
    </tr>
  </tbody>
</table>
</div>



For categorical (type `object`) and boolean (type `bool`) features we can use the `value_counts` method. Let’s have a look at the distribution of `Churn`:


```python
df['Churn'].value_counts()
```




    0    2850
    1     483
    Name: Churn, dtype: int64



2850 users out of 3333 are loyal; their `Churn` value is `0`. To calculate the proportion, pass `normalize=True` to the `value_counts` function.


```python
df['Churn'].value_counts(normalize=True)
```




    0    0.855086
    1    0.144914
    Name: Churn, dtype: float64




### Sorting

A DataFrame can be sorted by the value of one of the variables (i.e columns). For example, we can sort by Total day charge (use `ascending=False` to sort in descending order):



```python
df.sort_values(by='Total day charge', ascending=False).head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>State</th>
      <th>Account length</th>
      <th>Area code</th>
      <th>International plan</th>
      <th>Voice mail plan</th>
      <th>Number vmail messages</th>
      <th>Total day minutes</th>
      <th>Total day calls</th>
      <th>Total day charge</th>
      <th>Total eve minutes</th>
      <th>Total eve calls</th>
      <th>Total eve charge</th>
      <th>Total night minutes</th>
      <th>Total night calls</th>
      <th>Total night charge</th>
      <th>Total intl minutes</th>
      <th>Total intl calls</th>
      <th>Total intl charge</th>
      <th>Customer service calls</th>
      <th>Churn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>365</th>
      <td>CO</td>
      <td>154</td>
      <td>415</td>
      <td>No</td>
      <td>No</td>
      <td>0</td>
      <td>350.8</td>
      <td>75</td>
      <td>59.64</td>
      <td>216.5</td>
      <td>94</td>
      <td>18.40</td>
      <td>253.9</td>
      <td>100</td>
      <td>11.43</td>
      <td>10.1</td>
      <td>9</td>
      <td>2.73</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>985</th>
      <td>NY</td>
      <td>64</td>
      <td>415</td>
      <td>Yes</td>
      <td>No</td>
      <td>0</td>
      <td>346.8</td>
      <td>55</td>
      <td>58.96</td>
      <td>249.5</td>
      <td>79</td>
      <td>21.21</td>
      <td>275.4</td>
      <td>102</td>
      <td>12.39</td>
      <td>13.3</td>
      <td>9</td>
      <td>3.59</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2594</th>
      <td>OH</td>
      <td>115</td>
      <td>510</td>
      <td>Yes</td>
      <td>No</td>
      <td>0</td>
      <td>345.3</td>
      <td>81</td>
      <td>58.70</td>
      <td>203.4</td>
      <td>106</td>
      <td>17.29</td>
      <td>217.5</td>
      <td>107</td>
      <td>9.79</td>
      <td>11.8</td>
      <td>8</td>
      <td>3.19</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>156</th>
      <td>OH</td>
      <td>83</td>
      <td>415</td>
      <td>No</td>
      <td>No</td>
      <td>0</td>
      <td>337.4</td>
      <td>120</td>
      <td>57.36</td>
      <td>227.4</td>
      <td>116</td>
      <td>19.33</td>
      <td>153.9</td>
      <td>114</td>
      <td>6.93</td>
      <td>15.8</td>
      <td>7</td>
      <td>4.27</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>605</th>
      <td>MO</td>
      <td>112</td>
      <td>415</td>
      <td>No</td>
      <td>No</td>
      <td>0</td>
      <td>335.5</td>
      <td>77</td>
      <td>57.04</td>
      <td>212.5</td>
      <td>109</td>
      <td>18.06</td>
      <td>265.0</td>
      <td>132</td>
      <td>11.93</td>
      <td>12.7</td>
      <td>8</td>
      <td>3.43</td>
      <td>2</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



Alternatively, we can also sort by multiple columns:


```python
df.sort_values(by=['Churn', 'Total day charge'],
        ascending=[True, False]).head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>State</th>
      <th>Account length</th>
      <th>Area code</th>
      <th>International plan</th>
      <th>Voice mail plan</th>
      <th>Number vmail messages</th>
      <th>Total day minutes</th>
      <th>Total day calls</th>
      <th>Total day charge</th>
      <th>Total eve minutes</th>
      <th>Total eve calls</th>
      <th>Total eve charge</th>
      <th>Total night minutes</th>
      <th>Total night calls</th>
      <th>Total night charge</th>
      <th>Total intl minutes</th>
      <th>Total intl calls</th>
      <th>Total intl charge</th>
      <th>Customer service calls</th>
      <th>Churn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>688</th>
      <td>MN</td>
      <td>13</td>
      <td>510</td>
      <td>No</td>
      <td>Yes</td>
      <td>21</td>
      <td>315.6</td>
      <td>105</td>
      <td>53.65</td>
      <td>208.9</td>
      <td>71</td>
      <td>17.76</td>
      <td>260.1</td>
      <td>123</td>
      <td>11.70</td>
      <td>12.1</td>
      <td>3</td>
      <td>3.27</td>
      <td>3</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2259</th>
      <td>NC</td>
      <td>210</td>
      <td>415</td>
      <td>No</td>
      <td>Yes</td>
      <td>31</td>
      <td>313.8</td>
      <td>87</td>
      <td>53.35</td>
      <td>147.7</td>
      <td>103</td>
      <td>12.55</td>
      <td>192.7</td>
      <td>97</td>
      <td>8.67</td>
      <td>10.1</td>
      <td>7</td>
      <td>2.73</td>
      <td>3</td>
      <td>0</td>
    </tr>
    <tr>
      <th>534</th>
      <td>LA</td>
      <td>67</td>
      <td>510</td>
      <td>No</td>
      <td>No</td>
      <td>0</td>
      <td>310.4</td>
      <td>97</td>
      <td>52.77</td>
      <td>66.5</td>
      <td>123</td>
      <td>5.65</td>
      <td>246.5</td>
      <td>99</td>
      <td>11.09</td>
      <td>9.2</td>
      <td>10</td>
      <td>2.48</td>
      <td>4</td>
      <td>0</td>
    </tr>
    <tr>
      <th>575</th>
      <td>SD</td>
      <td>114</td>
      <td>415</td>
      <td>No</td>
      <td>Yes</td>
      <td>36</td>
      <td>309.9</td>
      <td>90</td>
      <td>52.68</td>
      <td>200.3</td>
      <td>89</td>
      <td>17.03</td>
      <td>183.5</td>
      <td>105</td>
      <td>8.26</td>
      <td>14.2</td>
      <td>2</td>
      <td>3.83</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2858</th>
      <td>AL</td>
      <td>141</td>
      <td>510</td>
      <td>No</td>
      <td>Yes</td>
      <td>28</td>
      <td>308.0</td>
      <td>123</td>
      <td>52.36</td>
      <td>247.8</td>
      <td>128</td>
      <td>21.06</td>
      <td>152.9</td>
      <td>103</td>
      <td>6.88</td>
      <td>7.4</td>
      <td>3</td>
      <td>2.00</td>
      <td>1</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




### Indexing and retrieving data

DataFrame can be indexed in different ways. 

To get a single column, you can use a `DataFrame['Name']` construction. Let's use this to answer a question about that column alone: **what is the proportion of churned users in our dataframe?**




```python
df['Churn'].mean()
```




    0.14491449144914492




14.5% is actually quite bad for a company; such a churn rate can make the company go bankrupt.

**Boolean indexing** with one column is also very convenient. The syntax is `df[P(df['Name'])]`, where `P` is some logical condition that is checked for each element of the `Name` column. The result of such indexing is the DataFrame consisting only of rows that satisfy the `P` condition on the `Name` column. 

Let’s use it to answer the question:

**What are average values of numerical variables for churned users?**



```python
df[df['Churn'] == 1].mean()
```




    Account length            102.664596
    Area code                 437.817805
    Number vmail messages       5.115942
    Total day minutes         206.914079
    Total day calls           101.335404
    Total day charge           35.175921
    Total eve minutes         212.410145
    Total eve calls           100.561077
    Total eve charge           18.054969
    Total night minutes       205.231677
    Total night calls         100.399586
    Total night charge          9.235528
    Total intl minutes         10.700000
    Total intl calls            4.163561
    Total intl charge           2.889545
    Customer service calls      2.229814
    Churn                       1.000000
    dtype: float64



**How much time (on average) do churned users spend on phone during daytime?**


```python
df[df['Churn'] == 1]['Total day minutes'].mean()
```




    206.91407867494814




**What is the maximum length of international calls among loyal users (`Churn == 0`) who do not have an international plan?**




```python
df[(df['Churn'] == 0) & (df['International plan'] == 'No')]['Total intl minutes'].max()
```




    18.9




DataFrames can be indexed by column name (label) or row name (index) or by the serial number of a row. The `loc` method is used for **indexing by name**, while `iloc()` is used for **indexing by number**.

In the first case, we would say *"give us the values of the rows with index from 0 to 5 (inclusive) and columns labeled from State to Area code (inclusive)"*, and, in the second case, we would say *"give us the values of the first five rows in the first three columns (as in typical Python slice: the maximal value is not included)"*.



```python
df.loc[0:5, 'State':'Area code']
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>State</th>
      <th>Account length</th>
      <th>Area code</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>KS</td>
      <td>128</td>
      <td>415</td>
    </tr>
    <tr>
      <th>1</th>
      <td>OH</td>
      <td>107</td>
      <td>415</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NJ</td>
      <td>137</td>
      <td>415</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OH</td>
      <td>84</td>
      <td>408</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OK</td>
      <td>75</td>
      <td>415</td>
    </tr>
    <tr>
      <th>5</th>
      <td>AL</td>
      <td>118</td>
      <td>510</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[0:5, 0:3]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>State</th>
      <th>Account length</th>
      <th>Area code</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>KS</td>
      <td>128</td>
      <td>415</td>
    </tr>
    <tr>
      <th>1</th>
      <td>OH</td>
      <td>107</td>
      <td>415</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NJ</td>
      <td>137</td>
      <td>415</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OH</td>
      <td>84</td>
      <td>408</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OK</td>
      <td>75</td>
      <td>415</td>
    </tr>
  </tbody>
</table>
</div>



If we need the first or last line of the data frame, we can use the `df[:1]` or `df[-1:]` construct:




```python
df[-1:]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>State</th>
      <th>Account length</th>
      <th>Area code</th>
      <th>International plan</th>
      <th>Voice mail plan</th>
      <th>Number vmail messages</th>
      <th>Total day minutes</th>
      <th>Total day calls</th>
      <th>Total day charge</th>
      <th>Total eve minutes</th>
      <th>Total eve calls</th>
      <th>Total eve charge</th>
      <th>Total night minutes</th>
      <th>Total night calls</th>
      <th>Total night charge</th>
      <th>Total intl minutes</th>
      <th>Total intl calls</th>
      <th>Total intl charge</th>
      <th>Customer service calls</th>
      <th>Churn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3332</th>
      <td>TN</td>
      <td>74</td>
      <td>415</td>
      <td>No</td>
      <td>Yes</td>
      <td>25</td>
      <td>234.4</td>
      <td>113</td>
      <td>39.85</td>
      <td>265.9</td>
      <td>82</td>
      <td>22.6</td>
      <td>241.4</td>
      <td>77</td>
      <td>10.86</td>
      <td>13.7</td>
      <td>4</td>
      <td>3.7</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




### Applying Functions to Cells, Columns and Rows

**To apply functions to each column, use `apply()`:**



```python
df.apply(np.max) 
```




    State                        WY
    Account length              243
    Area code                   510
    International plan          Yes
    Voice mail plan             Yes
    Number vmail messages        51
    Total day minutes         350.8
    Total day calls             165
    Total day charge          59.64
    Total eve minutes         363.7
    Total eve calls             170
    Total eve charge          30.91
    Total night minutes         395
    Total night calls           175
    Total night charge        17.77
    Total intl minutes           20
    Total intl calls             20
    Total intl charge           5.4
    Customer service calls        9
    Churn                         1
    dtype: object



The `apply` method can also be used to apply a function to each line. To do this, specify `axis=1`. Lambda functions are very convenient in such scenarios. For example, if we need to select all states starting with W, we can do it like this:


```python
df[df['State'].apply(lambda state: state[0] == 'W')].head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>State</th>
      <th>Account length</th>
      <th>Area code</th>
      <th>International plan</th>
      <th>Voice mail plan</th>
      <th>Number vmail messages</th>
      <th>Total day minutes</th>
      <th>Total day calls</th>
      <th>Total day charge</th>
      <th>Total eve minutes</th>
      <th>Total eve calls</th>
      <th>Total eve charge</th>
      <th>Total night minutes</th>
      <th>Total night calls</th>
      <th>Total night charge</th>
      <th>Total intl minutes</th>
      <th>Total intl calls</th>
      <th>Total intl charge</th>
      <th>Customer service calls</th>
      <th>Churn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>9</th>
      <td>WV</td>
      <td>141</td>
      <td>415</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>37</td>
      <td>258.6</td>
      <td>84</td>
      <td>43.96</td>
      <td>222.0</td>
      <td>111</td>
      <td>18.87</td>
      <td>326.4</td>
      <td>97</td>
      <td>14.69</td>
      <td>11.2</td>
      <td>5</td>
      <td>3.02</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>26</th>
      <td>WY</td>
      <td>57</td>
      <td>408</td>
      <td>No</td>
      <td>Yes</td>
      <td>39</td>
      <td>213.0</td>
      <td>115</td>
      <td>36.21</td>
      <td>191.1</td>
      <td>112</td>
      <td>16.24</td>
      <td>182.7</td>
      <td>115</td>
      <td>8.22</td>
      <td>9.5</td>
      <td>3</td>
      <td>2.57</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>44</th>
      <td>WI</td>
      <td>64</td>
      <td>510</td>
      <td>No</td>
      <td>No</td>
      <td>0</td>
      <td>154.0</td>
      <td>67</td>
      <td>26.18</td>
      <td>225.8</td>
      <td>118</td>
      <td>19.19</td>
      <td>265.3</td>
      <td>86</td>
      <td>11.94</td>
      <td>3.5</td>
      <td>3</td>
      <td>0.95</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>49</th>
      <td>WY</td>
      <td>97</td>
      <td>415</td>
      <td>No</td>
      <td>Yes</td>
      <td>24</td>
      <td>133.2</td>
      <td>135</td>
      <td>22.64</td>
      <td>217.2</td>
      <td>58</td>
      <td>18.46</td>
      <td>70.6</td>
      <td>79</td>
      <td>3.18</td>
      <td>11.0</td>
      <td>3</td>
      <td>2.97</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>54</th>
      <td>WY</td>
      <td>87</td>
      <td>415</td>
      <td>No</td>
      <td>No</td>
      <td>0</td>
      <td>151.0</td>
      <td>83</td>
      <td>25.67</td>
      <td>219.7</td>
      <td>116</td>
      <td>18.67</td>
      <td>203.9</td>
      <td>127</td>
      <td>9.18</td>
      <td>9.7</td>
      <td>3</td>
      <td>2.62</td>
      <td>5</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



The `map` method can be used to **replace values in a column** by passing a dictionary of the form `{old_value: new_value}` as its argument:


```python
d = {'No' : False, 'Yes' : True}
df['International plan'] = df['International plan'].map(d)
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>State</th>
      <th>Account length</th>
      <th>Area code</th>
      <th>International plan</th>
      <th>Voice mail plan</th>
      <th>Number vmail messages</th>
      <th>Total day minutes</th>
      <th>Total day calls</th>
      <th>Total day charge</th>
      <th>Total eve minutes</th>
      <th>Total eve calls</th>
      <th>Total eve charge</th>
      <th>Total night minutes</th>
      <th>Total night calls</th>
      <th>Total night charge</th>
      <th>Total intl minutes</th>
      <th>Total intl calls</th>
      <th>Total intl charge</th>
      <th>Customer service calls</th>
      <th>Churn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>KS</td>
      <td>128</td>
      <td>415</td>
      <td>False</td>
      <td>Yes</td>
      <td>25</td>
      <td>265.1</td>
      <td>110</td>
      <td>45.07</td>
      <td>197.4</td>
      <td>99</td>
      <td>16.78</td>
      <td>244.7</td>
      <td>91</td>
      <td>11.01</td>
      <td>10.0</td>
      <td>3</td>
      <td>2.70</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>OH</td>
      <td>107</td>
      <td>415</td>
      <td>False</td>
      <td>Yes</td>
      <td>26</td>
      <td>161.6</td>
      <td>123</td>
      <td>27.47</td>
      <td>195.5</td>
      <td>103</td>
      <td>16.62</td>
      <td>254.4</td>
      <td>103</td>
      <td>11.45</td>
      <td>13.7</td>
      <td>3</td>
      <td>3.70</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NJ</td>
      <td>137</td>
      <td>415</td>
      <td>False</td>
      <td>No</td>
      <td>0</td>
      <td>243.4</td>
      <td>114</td>
      <td>41.38</td>
      <td>121.2</td>
      <td>110</td>
      <td>10.30</td>
      <td>162.6</td>
      <td>104</td>
      <td>7.32</td>
      <td>12.2</td>
      <td>5</td>
      <td>3.29</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OH</td>
      <td>84</td>
      <td>408</td>
      <td>True</td>
      <td>No</td>
      <td>0</td>
      <td>299.4</td>
      <td>71</td>
      <td>50.90</td>
      <td>61.9</td>
      <td>88</td>
      <td>5.26</td>
      <td>196.9</td>
      <td>89</td>
      <td>8.86</td>
      <td>6.6</td>
      <td>7</td>
      <td>1.78</td>
      <td>2</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OK</td>
      <td>75</td>
      <td>415</td>
      <td>True</td>
      <td>No</td>
      <td>0</td>
      <td>166.7</td>
      <td>113</td>
      <td>28.34</td>
      <td>148.3</td>
      <td>122</td>
      <td>12.61</td>
      <td>186.9</td>
      <td>121</td>
      <td>8.41</td>
      <td>10.1</td>
      <td>3</td>
      <td>2.73</td>
      <td>3</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



The same thing can be done with the `replace` method:


```python
df = df.replace({'Voice mail plan': d})
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>State</th>
      <th>Account length</th>
      <th>Area code</th>
      <th>International plan</th>
      <th>Voice mail plan</th>
      <th>Number vmail messages</th>
      <th>Total day minutes</th>
      <th>Total day calls</th>
      <th>Total day charge</th>
      <th>Total eve minutes</th>
      <th>Total eve calls</th>
      <th>Total eve charge</th>
      <th>Total night minutes</th>
      <th>Total night calls</th>
      <th>Total night charge</th>
      <th>Total intl minutes</th>
      <th>Total intl calls</th>
      <th>Total intl charge</th>
      <th>Customer service calls</th>
      <th>Churn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>KS</td>
      <td>128</td>
      <td>415</td>
      <td>False</td>
      <td>True</td>
      <td>25</td>
      <td>265.1</td>
      <td>110</td>
      <td>45.07</td>
      <td>197.4</td>
      <td>99</td>
      <td>16.78</td>
      <td>244.7</td>
      <td>91</td>
      <td>11.01</td>
      <td>10.0</td>
      <td>3</td>
      <td>2.70</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>OH</td>
      <td>107</td>
      <td>415</td>
      <td>False</td>
      <td>True</td>
      <td>26</td>
      <td>161.6</td>
      <td>123</td>
      <td>27.47</td>
      <td>195.5</td>
      <td>103</td>
      <td>16.62</td>
      <td>254.4</td>
      <td>103</td>
      <td>11.45</td>
      <td>13.7</td>
      <td>3</td>
      <td>3.70</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NJ</td>
      <td>137</td>
      <td>415</td>
      <td>False</td>
      <td>False</td>
      <td>0</td>
      <td>243.4</td>
      <td>114</td>
      <td>41.38</td>
      <td>121.2</td>
      <td>110</td>
      <td>10.30</td>
      <td>162.6</td>
      <td>104</td>
      <td>7.32</td>
      <td>12.2</td>
      <td>5</td>
      <td>3.29</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OH</td>
      <td>84</td>
      <td>408</td>
      <td>True</td>
      <td>False</td>
      <td>0</td>
      <td>299.4</td>
      <td>71</td>
      <td>50.90</td>
      <td>61.9</td>
      <td>88</td>
      <td>5.26</td>
      <td>196.9</td>
      <td>89</td>
      <td>8.86</td>
      <td>6.6</td>
      <td>7</td>
      <td>1.78</td>
      <td>2</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OK</td>
      <td>75</td>
      <td>415</td>
      <td>True</td>
      <td>False</td>
      <td>0</td>
      <td>166.7</td>
      <td>113</td>
      <td>28.34</td>
      <td>148.3</td>
      <td>122</td>
      <td>12.61</td>
      <td>186.9</td>
      <td>121</td>
      <td>8.41</td>
      <td>10.1</td>
      <td>3</td>
      <td>2.73</td>
      <td>3</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




### Grouping

In general, grouping data in Pandas goes as follows:



```python
df.groupby(by=grouping_columns)[columns_to_show].function()
```


1. First, the `groupby` method divides the `grouping_columns` by their values. They become a new index in the resulting dataframe.
2. Then, columns of interest are selected (`columns_to_show`). If `columns_to_show` is not included, all non groupby clauses will be included.
3. Finally, one or several functions are applied to the obtained groups per selected columns.

Here is an example where we group the data according to the values of the `Churn` variable and display statistics of three columns in each group:


```python
columns_to_show = ['Total day minutes', 'Total eve minutes', 
                   'Total night minutes']

df.groupby(['Churn'])[columns_to_show].describe(percentiles=[])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="6" halign="left">Total day minutes</th>
      <th colspan="6" halign="left">Total eve minutes</th>
      <th colspan="6" halign="left">Total night minutes</th>
    </tr>
    <tr>
      <th></th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>50%</th>
      <th>max</th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>50%</th>
      <th>max</th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>50%</th>
      <th>max</th>
    </tr>
    <tr>
      <th>Churn</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2850.0</td>
      <td>175.175754</td>
      <td>50.181655</td>
      <td>0.0</td>
      <td>177.2</td>
      <td>315.6</td>
      <td>2850.0</td>
      <td>199.043298</td>
      <td>50.292175</td>
      <td>0.0</td>
      <td>199.6</td>
      <td>361.8</td>
      <td>2850.0</td>
      <td>200.133193</td>
      <td>51.105032</td>
      <td>23.2</td>
      <td>200.25</td>
      <td>395.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>483.0</td>
      <td>206.914079</td>
      <td>68.997792</td>
      <td>0.0</td>
      <td>217.6</td>
      <td>350.8</td>
      <td>483.0</td>
      <td>212.410145</td>
      <td>51.728910</td>
      <td>70.9</td>
      <td>211.3</td>
      <td>363.7</td>
      <td>483.0</td>
      <td>205.231677</td>
      <td>47.132825</td>
      <td>47.4</td>
      <td>204.80</td>
      <td>354.9</td>
    </tr>
  </tbody>
</table>
</div>



Let’s do the same thing, but slightly differently by passing a list of functions to `agg()`:


```python
columns_to_show = ['Total day minutes', 'Total eve minutes', 
                   'Total night minutes']

df.groupby(['Churn'])[columns_to_show].agg([np.mean, np.std, np.min, 
                                            np.max])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="4" halign="left">Total day minutes</th>
      <th colspan="4" halign="left">Total eve minutes</th>
      <th colspan="4" halign="left">Total night minutes</th>
    </tr>
    <tr>
      <th></th>
      <th>mean</th>
      <th>std</th>
      <th>amin</th>
      <th>amax</th>
      <th>mean</th>
      <th>std</th>
      <th>amin</th>
      <th>amax</th>
      <th>mean</th>
      <th>std</th>
      <th>amin</th>
      <th>amax</th>
    </tr>
    <tr>
      <th>Churn</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>175.175754</td>
      <td>50.181655</td>
      <td>0.0</td>
      <td>315.6</td>
      <td>199.043298</td>
      <td>50.292175</td>
      <td>0.0</td>
      <td>361.8</td>
      <td>200.133193</td>
      <td>51.105032</td>
      <td>23.2</td>
      <td>395.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>206.914079</td>
      <td>68.997792</td>
      <td>0.0</td>
      <td>350.8</td>
      <td>212.410145</td>
      <td>51.728910</td>
      <td>70.9</td>
      <td>363.7</td>
      <td>205.231677</td>
      <td>47.132825</td>
      <td>47.4</td>
      <td>354.9</td>
    </tr>
  </tbody>
</table>
</div>




### Summary tables

Suppose we want to see how the observations in our sample are distributed in the context of two variables - `Churn` and `International plan`. To do so, we can build a **contingency table** using the `crosstab` method:




```python
pd.crosstab(df['Churn'], df['International plan'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>International plan</th>
      <th>False</th>
      <th>True</th>
    </tr>
    <tr>
      <th>Churn</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2664</td>
      <td>186</td>
    </tr>
    <tr>
      <th>1</th>
      <td>346</td>
      <td>137</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.crosstab(df['Churn'], df['Voice mail plan'], normalize=True)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Voice mail plan</th>
      <th>False</th>
      <th>True</th>
    </tr>
    <tr>
      <th>Churn</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.602460</td>
      <td>0.252625</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.120912</td>
      <td>0.024002</td>
    </tr>
  </tbody>
</table>
</div>



We can see that most of the users are loyal and do not use additional services (International Plan/Voice mail).

This will resemble **pivot tables** to those familiar with Excel. And, of course, pivot tables are implemented in Pandas: the `pivot_table` method takes the following parameters:

* `values` - a list of variables to calculate statistics for,
* `index` – a list of variables to group data by,
* `aggfunc` — what statistics we need to calculate for groups - e.g sum, mean, maximum, minimum or something else.

Let’s take a look at the average number of day, evening, and night calls by area code:


```python
df.pivot_table(['Total day calls', 'Total eve calls', 'Total night calls'],
               ['Area code'], aggfunc='mean')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total day calls</th>
      <th>Total eve calls</th>
      <th>Total night calls</th>
    </tr>
    <tr>
      <th>Area code</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>408</th>
      <td>100.496420</td>
      <td>99.788783</td>
      <td>99.039379</td>
    </tr>
    <tr>
      <th>415</th>
      <td>100.576435</td>
      <td>100.503927</td>
      <td>100.398187</td>
    </tr>
    <tr>
      <th>510</th>
      <td>100.097619</td>
      <td>99.671429</td>
      <td>100.601190</td>
    </tr>
  </tbody>
</table>
</div>




### DataFrame transformations

Like many other things in Pandas, adding columns to a DataFrame is doable in many ways.

For example, if we want to calculate the total number of calls for all users, let’s create the `total_calls` Series and paste it into the DataFrame:




```python
total_calls = df['Total day calls'] + df['Total eve calls'] + \
    df['Total night calls'] + df['Total intl calls']
df.insert(loc=len(df.columns), column='Total calls', value=total_calls) 
# loc parameter is the number of columns after which to insert the Series object
# we set it to len(df.columns) to paste it at the very end of the dataframe
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>State</th>
      <th>Account length</th>
      <th>Area code</th>
      <th>International plan</th>
      <th>Voice mail plan</th>
      <th>Number vmail messages</th>
      <th>Total day minutes</th>
      <th>Total day calls</th>
      <th>Total day charge</th>
      <th>Total eve minutes</th>
      <th>...</th>
      <th>Total eve charge</th>
      <th>Total night minutes</th>
      <th>Total night calls</th>
      <th>Total night charge</th>
      <th>Total intl minutes</th>
      <th>Total intl calls</th>
      <th>Total intl charge</th>
      <th>Customer service calls</th>
      <th>Churn</th>
      <th>Total calls</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>KS</td>
      <td>128</td>
      <td>415</td>
      <td>False</td>
      <td>True</td>
      <td>25</td>
      <td>265.1</td>
      <td>110</td>
      <td>45.07</td>
      <td>197.4</td>
      <td>...</td>
      <td>16.78</td>
      <td>244.7</td>
      <td>91</td>
      <td>11.01</td>
      <td>10.0</td>
      <td>3</td>
      <td>2.70</td>
      <td>1</td>
      <td>0</td>
      <td>303</td>
    </tr>
    <tr>
      <th>1</th>
      <td>OH</td>
      <td>107</td>
      <td>415</td>
      <td>False</td>
      <td>True</td>
      <td>26</td>
      <td>161.6</td>
      <td>123</td>
      <td>27.47</td>
      <td>195.5</td>
      <td>...</td>
      <td>16.62</td>
      <td>254.4</td>
      <td>103</td>
      <td>11.45</td>
      <td>13.7</td>
      <td>3</td>
      <td>3.70</td>
      <td>1</td>
      <td>0</td>
      <td>332</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NJ</td>
      <td>137</td>
      <td>415</td>
      <td>False</td>
      <td>False</td>
      <td>0</td>
      <td>243.4</td>
      <td>114</td>
      <td>41.38</td>
      <td>121.2</td>
      <td>...</td>
      <td>10.30</td>
      <td>162.6</td>
      <td>104</td>
      <td>7.32</td>
      <td>12.2</td>
      <td>5</td>
      <td>3.29</td>
      <td>0</td>
      <td>0</td>
      <td>333</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OH</td>
      <td>84</td>
      <td>408</td>
      <td>True</td>
      <td>False</td>
      <td>0</td>
      <td>299.4</td>
      <td>71</td>
      <td>50.90</td>
      <td>61.9</td>
      <td>...</td>
      <td>5.26</td>
      <td>196.9</td>
      <td>89</td>
      <td>8.86</td>
      <td>6.6</td>
      <td>7</td>
      <td>1.78</td>
      <td>2</td>
      <td>0</td>
      <td>255</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OK</td>
      <td>75</td>
      <td>415</td>
      <td>True</td>
      <td>False</td>
      <td>0</td>
      <td>166.7</td>
      <td>113</td>
      <td>28.34</td>
      <td>148.3</td>
      <td>...</td>
      <td>12.61</td>
      <td>186.9</td>
      <td>121</td>
      <td>8.41</td>
      <td>10.1</td>
      <td>3</td>
      <td>2.73</td>
      <td>3</td>
      <td>0</td>
      <td>359</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 21 columns</p>
</div>



It is possible to add a column more easily without creating an intermediate Series instance:


```python
df['Total charge'] = df['Total day charge'] + df['Total eve charge'] + \
    df['Total night charge'] + df['Total intl charge']

df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>State</th>
      <th>Account length</th>
      <th>Area code</th>
      <th>International plan</th>
      <th>Voice mail plan</th>
      <th>Number vmail messages</th>
      <th>Total day minutes</th>
      <th>Total day calls</th>
      <th>Total day charge</th>
      <th>Total eve minutes</th>
      <th>...</th>
      <th>Total night minutes</th>
      <th>Total night calls</th>
      <th>Total night charge</th>
      <th>Total intl minutes</th>
      <th>Total intl calls</th>
      <th>Total intl charge</th>
      <th>Customer service calls</th>
      <th>Churn</th>
      <th>Total calls</th>
      <th>Total charge</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>KS</td>
      <td>128</td>
      <td>415</td>
      <td>False</td>
      <td>True</td>
      <td>25</td>
      <td>265.1</td>
      <td>110</td>
      <td>45.07</td>
      <td>197.4</td>
      <td>...</td>
      <td>244.7</td>
      <td>91</td>
      <td>11.01</td>
      <td>10.0</td>
      <td>3</td>
      <td>2.70</td>
      <td>1</td>
      <td>0</td>
      <td>303</td>
      <td>75.56</td>
    </tr>
    <tr>
      <th>1</th>
      <td>OH</td>
      <td>107</td>
      <td>415</td>
      <td>False</td>
      <td>True</td>
      <td>26</td>
      <td>161.6</td>
      <td>123</td>
      <td>27.47</td>
      <td>195.5</td>
      <td>...</td>
      <td>254.4</td>
      <td>103</td>
      <td>11.45</td>
      <td>13.7</td>
      <td>3</td>
      <td>3.70</td>
      <td>1</td>
      <td>0</td>
      <td>332</td>
      <td>59.24</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NJ</td>
      <td>137</td>
      <td>415</td>
      <td>False</td>
      <td>False</td>
      <td>0</td>
      <td>243.4</td>
      <td>114</td>
      <td>41.38</td>
      <td>121.2</td>
      <td>...</td>
      <td>162.6</td>
      <td>104</td>
      <td>7.32</td>
      <td>12.2</td>
      <td>5</td>
      <td>3.29</td>
      <td>0</td>
      <td>0</td>
      <td>333</td>
      <td>62.29</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OH</td>
      <td>84</td>
      <td>408</td>
      <td>True</td>
      <td>False</td>
      <td>0</td>
      <td>299.4</td>
      <td>71</td>
      <td>50.90</td>
      <td>61.9</td>
      <td>...</td>
      <td>196.9</td>
      <td>89</td>
      <td>8.86</td>
      <td>6.6</td>
      <td>7</td>
      <td>1.78</td>
      <td>2</td>
      <td>0</td>
      <td>255</td>
      <td>66.80</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OK</td>
      <td>75</td>
      <td>415</td>
      <td>True</td>
      <td>False</td>
      <td>0</td>
      <td>166.7</td>
      <td>113</td>
      <td>28.34</td>
      <td>148.3</td>
      <td>...</td>
      <td>186.9</td>
      <td>121</td>
      <td>8.41</td>
      <td>10.1</td>
      <td>3</td>
      <td>2.73</td>
      <td>3</td>
      <td>0</td>
      <td>359</td>
      <td>52.09</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 22 columns</p>
</div>



To delete columns or rows, use the `drop` method, passing the required indexes and the `axis` parameter (`1` if you delete columns, and nothing or `0` if you delete rows). The `inplace` argument tells whether to change the original DataFrame. With `inplace=False`, the `drop` method doesn't change the existing DataFrame and returns a new one with dropped rows or columns. With `inplace=True`, it alters the DataFrame.


```python
# get rid of just created columns
df.drop(['Total charge', 'Total calls'], axis=1, inplace=True) 
# and here’s how you can delete rows
df.drop([1, 2]).head() 
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>State</th>
      <th>Account length</th>
      <th>Area code</th>
      <th>International plan</th>
      <th>Voice mail plan</th>
      <th>Number vmail messages</th>
      <th>Total day minutes</th>
      <th>Total day calls</th>
      <th>Total day charge</th>
      <th>Total eve minutes</th>
      <th>Total eve calls</th>
      <th>Total eve charge</th>
      <th>Total night minutes</th>
      <th>Total night calls</th>
      <th>Total night charge</th>
      <th>Total intl minutes</th>
      <th>Total intl calls</th>
      <th>Total intl charge</th>
      <th>Customer service calls</th>
      <th>Churn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>KS</td>
      <td>128</td>
      <td>415</td>
      <td>False</td>
      <td>True</td>
      <td>25</td>
      <td>265.1</td>
      <td>110</td>
      <td>45.07</td>
      <td>197.4</td>
      <td>99</td>
      <td>16.78</td>
      <td>244.7</td>
      <td>91</td>
      <td>11.01</td>
      <td>10.0</td>
      <td>3</td>
      <td>2.70</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OH</td>
      <td>84</td>
      <td>408</td>
      <td>True</td>
      <td>False</td>
      <td>0</td>
      <td>299.4</td>
      <td>71</td>
      <td>50.90</td>
      <td>61.9</td>
      <td>88</td>
      <td>5.26</td>
      <td>196.9</td>
      <td>89</td>
      <td>8.86</td>
      <td>6.6</td>
      <td>7</td>
      <td>1.78</td>
      <td>2</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OK</td>
      <td>75</td>
      <td>415</td>
      <td>True</td>
      <td>False</td>
      <td>0</td>
      <td>166.7</td>
      <td>113</td>
      <td>28.34</td>
      <td>148.3</td>
      <td>122</td>
      <td>12.61</td>
      <td>186.9</td>
      <td>121</td>
      <td>8.41</td>
      <td>10.1</td>
      <td>3</td>
      <td>2.73</td>
      <td>3</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>AL</td>
      <td>118</td>
      <td>510</td>
      <td>True</td>
      <td>False</td>
      <td>0</td>
      <td>223.4</td>
      <td>98</td>
      <td>37.98</td>
      <td>220.6</td>
      <td>101</td>
      <td>18.75</td>
      <td>203.9</td>
      <td>118</td>
      <td>9.18</td>
      <td>6.3</td>
      <td>6</td>
      <td>1.70</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>MA</td>
      <td>121</td>
      <td>510</td>
      <td>False</td>
      <td>True</td>
      <td>24</td>
      <td>218.2</td>
      <td>88</td>
      <td>37.09</td>
      <td>348.5</td>
      <td>108</td>
      <td>29.62</td>
      <td>212.6</td>
      <td>118</td>
      <td>9.57</td>
      <td>7.5</td>
      <td>7</td>
      <td>2.03</td>
      <td>3</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




## 4. First attempt on predicting telecom churn


Let's see how churn rate is related to the *International plan* variable. We’ll do this using a `crosstab` contingency table and also through visual analysis with `Seaborn` (however, visual analysis will be covered more thoroughly in the next article).



```python
pd.crosstab(df['Churn'], df['International plan'], margins=True)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>International plan</th>
      <th>False</th>
      <th>True</th>
      <th>All</th>
    </tr>
    <tr>
      <th>Churn</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2664</td>
      <td>186</td>
      <td>2850</td>
    </tr>
    <tr>
      <th>1</th>
      <td>346</td>
      <td>137</td>
      <td>483</td>
    </tr>
    <tr>
      <th>All</th>
      <td>3010</td>
      <td>323</td>
      <td>3333</td>
    </tr>
  </tbody>
</table>
</div>




```python
# some imports and "magic" commands to set up plotting 
%matplotlib inline 
import matplotlib.pyplot as plt
# pip install seaborn 
import seaborn as sns
plt.rcParams['image.cmap'] = 'viridis'
```


```python
sns.countplot(x='International plan', hue='Churn', data=df);
```


![png](output_69_0.png)



We see that, with *International Plan*, the churn rate is much higher, which is an interesting observation! Perhaps large and poorly controlled expenses with international calls are very conflict-prone and lead to dissatisfaction among the telecom operator's customers.

Next, let’s look at another important feature – *Customer service calls*. Let’s also make a summary table and a picture.


```python
pd.crosstab(df['Churn'], df['Customer service calls'], margins=True)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Customer service calls</th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
      <th>9</th>
      <th>All</th>
    </tr>
    <tr>
      <th>Churn</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>605</td>
      <td>1059</td>
      <td>672</td>
      <td>385</td>
      <td>90</td>
      <td>26</td>
      <td>8</td>
      <td>4</td>
      <td>1</td>
      <td>0</td>
      <td>2850</td>
    </tr>
    <tr>
      <th>1</th>
      <td>92</td>
      <td>122</td>
      <td>87</td>
      <td>44</td>
      <td>76</td>
      <td>40</td>
      <td>14</td>
      <td>5</td>
      <td>1</td>
      <td>2</td>
      <td>483</td>
    </tr>
    <tr>
      <th>All</th>
      <td>697</td>
      <td>1181</td>
      <td>759</td>
      <td>429</td>
      <td>166</td>
      <td>66</td>
      <td>22</td>
      <td>9</td>
      <td>2</td>
      <td>2</td>
      <td>3333</td>
    </tr>
  </tbody>
</table>
</div>




```python
sns.countplot(x='Customer service calls', hue='Churn', data=df);
```


![png](output_72_0.png)



Perhaps, it is not so obvious from the summary table, but the picture clearly states that the churn rate strongly increases starting from 4 calls to the service center. 

Let’s now add a binary attribute to our DataFrame – `Customer service calls > 3`. And once again, let's see how it relates to churn. 



```python
df['Many_service_calls'] = (df['Customer service calls'] > 3).astype('int')

pd.crosstab(df['Many_service_calls'], df['Churn'], margins=True)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Churn</th>
      <th>0</th>
      <th>1</th>
      <th>All</th>
    </tr>
    <tr>
      <th>Many_service_calls</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2721</td>
      <td>345</td>
      <td>3066</td>
    </tr>
    <tr>
      <th>1</th>
      <td>129</td>
      <td>138</td>
      <td>267</td>
    </tr>
    <tr>
      <th>All</th>
      <td>2850</td>
      <td>483</td>
      <td>3333</td>
    </tr>
  </tbody>
</table>
</div>




```python
sns.countplot(x='Many_service_calls', hue='Churn', data=df);
```


![png](output_75_0.png)



Let’s construct another contingency table that relates *Churn* with both *International plan* and freshly created *Many_service_calls*.




```python
pd.crosstab(df['Many_service_calls'] & df['International plan'] , df['Churn'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Churn</th>
      <th>0</th>
      <th>1</th>
    </tr>
    <tr>
      <th>row_0</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>False</th>
      <td>2841</td>
      <td>464</td>
    </tr>
    <tr>
      <th>True</th>
      <td>9</td>
      <td>19</td>
    </tr>
  </tbody>
</table>
</div>



Therefore, predicting that a customer is loyal (*Churn*=0) in the case when the number of calls to the service center is less than 4 and the *International Plan* is added (and predicting *Churn*=1 otherwise), we might expect an accuracy of 85.8% (we are mistaken only 464 + 9 times). This number, 85.8%, that we got with very simple reasoning serves as a good starting point (*baseline*) for the further machine learning models that we will build. 

As we move on in this course, recall that, before the advent of machine learning, the data analysis process looked something like this. Let's recap what we've covered:
    
- The share of loyal clients in the sample is 85.5%. The most naive model that always predicts a "loyal customer" on such data will guess right in about 85.5% of all cases. That is, the proportion of correct answers (*accuracy*) of subsequent models should be no less than this number, and will hopefully be significantly higher;
- With the help of a simple forecast that can be expressed by the following formula: "International plan = True & Customer Service calls > 3 => Churn = 1, else Churn = 0", we can expect a guessing rate of 85.8%, which is just above 85.5%. Subsequently, we'll talk about decision trees and figure out how to find such rules **automatically** based only on the input data;
- We got these two baselines without applying machine learning, and they’ll serve as the starting point for our subsequent models. If it turns out that with enormous efforts, we increase the share of correct answers by 0.5% per se, then perhaps we are doing something wrong, and it suffices to confine ourselves to a simple model with two conditions;
- Before training complex models, it is recommended to manipulate the data a bit, make some plots, and check simple assumptions. Moreover, in business applications of machine learning, they usually start with simple solutions and then experiment with more complex ones.


## 5. Assignment #1

In the first assignment, you'll analyze the UCI Adult data set containing demographic information about the US residents. We suggest that you complete the tasks in the [Jupyter notebook](http://nbviewer.jupyter.org/github/Yorko/mlcourse_open/blob/master/jupyter_english/topic01_pandas_data_analysis/assignment1_pandas_uci_adult.ipynb), and then answer 10 questions in the [Google form](https://docs.google.com/forms/d/1ws9mchvdVGRyva_y_cPjASED8ATZTOsQFKfimohNaFE). You can edit your responses even after submitting the form.

**Hard deadline**: February 12, 23:59 CET

## 6. Useful resources

* First of all, of course, the [official documentation of Pandas](http://pandas.pydata.org/pandas-docs/stable/index.html)
* Medium ["story"](https://medium.com/open-machine-learning-course/open-machine-learning-course-topic-1-exploratory-data-analysis-with-pandas-de57880f1a68) based on this notebook
* If you read Russian: an [article](https://habrahabr.ru/company/ods/blog/322626/) on Habrahabr with ~ the same material. And a [lecture](https://youtu.be/dEFxoyJhm3Y) on YouTube
* [10 minutes to pandas](http://pandas.pydata.org/pandas-docs/stable/10min.html)
* [Pandas cheatsheet PDF](https://github.com/pandas-dev/pandas/blob/master/doc/cheatsheet/Pandas_Cheat_Sheet.pdf)
* GitHub repos: [Pandas exercises](https://github.com/guipsamora/pandas_exercises/) and ["Effective Pandas"](https://github.com/TomAugspurger/effective-pandas)
* [scipy-lectures.org](http://www.scipy-lectures.org/index.html) — tutorials on pandas, numpy, matplotlib and scikit-learn
[![fig3][f3]][f3]  


[f1]: https://ikashnitsky.github.io/images/180522/layout-annotated.png
[f2]: https://ikashnitsky.github.io/images/180522/options.png
[f3]: https://ikashnitsky.github.io/images/180522/hotkeys.png


[ugo]: https://twitter.com/ugobas
