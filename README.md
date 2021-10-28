# Rain-prediction : Overview
* Build model to predict whether or not rain will occur tomorrow
* Predicting whether or not rain will occur tomorrow. Dataset acquired from  [Rain in Australia | Kaggle](https://www.kaggle.com/jsphyg/weather-dataset-rattle-package?rvi=1) 
* Drop columns with high missing values percentage, and fill the rest of the missing values with median
* Replace outliers with upper and lower fence (IQR method)
* Normalize features
* Feature Selection
* Sampled the data using 3 techniques: Undersampling, Oversampling, SMOTE Oversampling
* Trained model with 4 different algorithms and compared the result for each sampling technique
* No hyperparameter tuning (because the models performances did not improve significantly, and the original performances are already good enough)

## Problems
* Currently, weather forecasts are already widely done with more scientific methods which also requires a lot of data and computing power, which also means it probably takes a lot of time
* But sometimes, we don't really need to know all the details of the future weather. Sometimes we just want to know <b>whether or not tomorrow will rain</b>, because a lot of our activities tomorrow will depend on the weather
* Using today data, we want to create a simple model that can predict rain occurence tomorrow.

## Objective
Creating a simple model that can solve a <b> simple problem </b>: IS tomorrow going to rain?

## Glimpse on the Dataset
1. A lot of missing data<br>
![alt text](https://github.com/sleepyallover/Rain-prediction/blob/main/misval%20rain.png "Missing values in each columns")<br>
We have a lot of missing columns in Evaporation, Sunshine, Cloud9am, and Cloud3pm columns. The missing value percentages in these columns are too high, so these columns might not give us any useful information. We probably would have to drop them. The rest we're going to fill them with median.
2. Outliers<br>
![alt text](https://github.com/sleepyallover/Rain-prediction/blob/main/dist.png "outliers")<br>
Notice that we have significant outliers in the features. What we're gonna do is replace those outliers with its upper/lower fence using IQR method.
3. Feature Correlations <br>
![alt text](https://github.com/sleepyallover/Rain-prediction/blob/main/corr.png "corr")<br>
Features which correlation with the target column <0.1 will be dropped. We also need to drop highly correlated features to avoid multicollinearity.
4. Class Imbalance<br>
![alt text](https://github.com/sleepyallover/Rain-prediction/blob/main/target.png "target")<br>
We're going to compare 3 sampling techniques : Undersampling, Oversampling, SMOTE Oversampling.

We should also normalize data using MinMaxScaler()

## Modeling  & Evaluation

After the dataset is preprocessed, then it is ready to enter the modeling stage.
We use 4 algorithm : Logistic Regression, KNN, Random Forest, and XGBoost. The models are evaluated on AUC score.

| Model | Sampling | AUC Score |
| --- | --- | --- |
| **Logistic Regression** | **Undersampling**<br>**Oversampling**<br>**SMOTE** | **85%**<br>**85%**<br>**87%** |
| **KNN** | **Undersampling**<br>**Oversampling**<br>**SMOTE** | **81%**<br>**88%**<br>**91%** |
| **Random Forest** | **Undersampling**<br>**Oversampling**<br>**SMOTE** |  **86%**<br>**98%**<br>**95%** |
| **XGBoost** | **Undersampling**<br>**Oversampling**<br>**SMOTE** | **86%**<br>**89%**<br>**96%** |

## Conclusion
* The recommended model for this project is Random Forest with oversampling technique with <strong>AUC score of 98%</strong>.
* The performance of the model is good enough to predict rain occurence tomorrow, hence fulfilling our objective.
