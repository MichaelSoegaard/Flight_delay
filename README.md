# Flight delay prediction
![Flight_delay_img](img/flight_delay2.jpg)
## Overview
In this project we are going to make an explanatory analysis of a dataset consisting of data from flights in the US from January 2019 and 2020. After we have cleaned the data we are going to create various models to predict whether flights are likely to be delayed or not. So this is a binary classification task.
The question we are going to answer is:

 - Can we make a model to predict flight delays?
 - Are we more likely to experince delays at specific dates?
 - Are we more likely to experince delays at specific weekdays?
 - Is there a difference in the amount a delays based on the carrier?
 - Is there a difference in the amount a delays based on the departure airport?
 - Is there a difference in the amount a delays based on the arrival airport?
 - Is there a difference in the amount a delays based on length of flight?

### Conclusions
After some data cleaning it was possible to predict flight delays.
We tried three different models which got the following scores on validation sets:

 - Logistic Regression ROC AUC score: 90
 -  Xgboost ROC AUC score: 95
 - RandomForest ROC AUC score: 90
 
 I then choose Xgboost as my model and tested it on the test set, which achieved a ROC AUC score of XX
 
The best score is achieved by using an XGBoost model with a standard threshold of 50/50

### Dataset
 Data based on [this](https://www.kaggle.com/divyansh22/flight-delay-prediction) Kaggle dataset. 
The dataset cosists of app. 800,000 rows, 21 columns, of which 20  are features and 1 taget. Data has been collected for January 2019 and 2020, so the thought was to predict delays on a per month basis. In this dataset we have data for January and thus we would you it to predict delays for January 2021. To get more info about each feature please view the feature cookbook.

### Data cleaning

In this project there is a lot of work in preprocessing. 

 1. We needed to get rid of redundant columns which didn't add any info to the model, such as ID' for flights and carriers.
 2. We had to create new categorical features based numerical values of other columns.
 3. Target label was created by concatenating delayed flights with flights that were diverted or cancelled. This is clearly a subjective choice, but I choose to treat them all as if the flights were delayed.
 4. 

### Data pipeline
I created Scikit-Learn pipelines for all the models trained. All models used the same pipeline, which involved:

 - Transformer
 - One-hot encoding categorical features which were not ordinal
 - Ordinal encoding a couple of features
 - Scaling of numeric features
 - Dimensionality reduction by using SVD due to very large and sparse dataset.
 - Cross validated gridsearch over SVD components as well as model hyperparameters.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwMzMzNzA3MjUsLTE5ODM0NDQwNjksLT
E5ODk0MjUyMTcsMjA4NjM0OTEwOCw5OTY2MDIwNTQsMTg2NDg4
NjYxNSwtOTMxMDI5MTE1LC0yNjU5NjE0MzMsMTI0MDg1Njk1LC
0xNDQ5MTU4NTExLC0xNDMzNTI1NzgwXX0=
-->