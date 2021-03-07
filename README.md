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
 -  Xgboost ROC AUC score: 94
 - RandomForest ROC AUC score: 90
 
 I then choose Xgboost as my final model and tested it on the test set, which achieved a __ROC AUC score of 93__
 
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

### Data analysis
***Are we more likely to experince delays at specific dates?***
When we look at delays in relation to day of month, there isn't a very clear trend. The 18th is the day with most delays, as **25%** of it's flight get delayed, while the day with fewest delays is the 9th, with **10%** of it's flights getting delayed. The percentage is relative to the days amount of flights. 
![Date_delays](/img/day_of_month_delays.png)

***Are we more likely to experince delays at specific weekdays?***
When we plot the different weekdays, we don't see much variation in the amount of delays realtive to each other. Tuesdays is the lowest with 12,3% of it's flight getting delayed and Thrusday is the higheste with 17,8 % of its' flights getting delayed.
![weekday delays](/img/weekday_delays.png)</p>

***Is there a difference in the amount a delays based on the carrier?***
Carrier is equivalant to airline and even though there is quite a difference in the airlines sizes and the amount of flights they each handle, that isn't something that's reflected in the amount of delays they each have. 
![enter image description here](/img/dcarrier_delays.png)

There's quite a difference between the higheste at 26.5% of all flights delayed and the airline with the loweste rate of delays at 11.4 %. The mean delay percentage is 17.9%. Even though the data only is based on two months of data, each airline have a lot of flights which makes these calculations more reliable.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjQzNzIwNTY1LC0xMjg4NTk5NjM0LDIwOT
kwMDM0ODAsMzE0MTI1MDA1LC0xNjU0NTA2NDQ1LDUzMDQwNjA4
NiwzMjQ5NDM5NDEsLTYxMTcyNjk2NCwtMTU2MTM2NzQ3LC0xNT
M3NjUzNDU0LC0xMDQ3MzE1OTQ5LDE0NzkyODMwNDQsLTEwMzMz
NzA3MjUsLTE5ODM0NDQwNjksLTE5ODk0MjUyMTcsMjA4NjM0OT
EwOCw5OTY2MDIwNTQsMTg2NDg4NjYxNSwtOTMxMDI5MTE1LC0y
NjU5NjE0MzNdfQ==
-->