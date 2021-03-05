# Flight delay prediction
## Overview
In this project we are going to make an explanatory analysis of a dataset consisting of data from flights in the US from January 2019 and 2020. After we have cleaned the data we are going to create various models to predict whether flights are likely to be delayed or not. So this is a binary classification task.
### Dataset
 Data based on [this](https://www.kaggle.com/divyansh22/flight-delay-prediction) Kaggle dataset. 
The dataset cosists of 21 columns, 20 features and 1 taget. Data has been collected for January 2019 and 2020, so the thought was to predict delays on a per month basis. In this dataset we have data for January and thus we would you it  



We get data from January 2019 and 2020 and need to prdict flight delays. In this project there is a lot of work in preprocessing. A lot of missing values and different categorical features. First priority was to solve this and get a get the best ROC AUC score. I tried different boosting algorithms to compare as well as an ordinary Logistic regression to use as baseline.

I used Scikit-Learn a lot including Transform, Pipeline and GridSearchCV.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgzOTM4MDA5NywxMjQwODU2OTUsLTE0ND
kxNTg1MTEsLTE0MzM1MjU3ODBdfQ==
-->