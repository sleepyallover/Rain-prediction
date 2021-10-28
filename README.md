# Rain-prediction : Overview
* Build model to predict whether or not rain will occur tomorrow
* Predicting whether or not rain will occur tomorrow. Dataset acquired from  [Rain in Australia | Kaggle](https://www.kaggle.com/jsphyg/weather-dataset-rattle-package?rvi=1) 
* Drop columns with high missing values percentage, and fill the rest of the missing values with median
* Replace outliers with upper and lower fence (IQR method)
* Sampled the data using 3 techniques: Undersampling, Oversampling, SMOTE Oversampling
* Trained model with 4 different algorithms and compared the result for each sampling technique
* No hyperparameter tuning (because the models performances did not improve significantly, and the original performances are already good enough)

## Problems
* Currently, weather forecasts are already widely done with more scientific methods which also requires a lot of data and computing power, which also means it probably takes a lot of time
* But sometimes, we don't really need to know all the details of the future weather. Sometimes we just want to know <b>whether or not tomorrow will rain</b>, because a lot of our activities tomorrow will depend on the weather
* Using today data, we want to create a simple model that can predict rain occurence tomorrow.

## Objective
Creating a simple model that can solve a <b> simple problem </b>: IS tomorrow going to rain?

## Early Glimpse on the Dataset
1. A lot of missing data<br>
![alt text](https://github.com/sleepyallover/Rain-prediction/blob/main/misval%20rain.png "Missing values in each columns")<br>
