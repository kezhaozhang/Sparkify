# Capstone Project: User Churn Data Analysis and Prediction using Spark

## Summary
This project uses Spark to process and analyze user data of Sparkify music service.  Machine learning models are created and optimized to predict user churn.

A subset of the dataset is used for exploratory data analysis and machine learning model evalution on a local computer. The full dataset is analyzed on an Amazon Elastic MapReduce (EMR) cluster.

Spark is used because the distributed computation system can better handle the large size of the full dataset. In addition, machine learning library is included in Spark for complex analysis.  

A report of the project can be found [here](https://kezhaozhang.github.io/SparkifyReport/).

## Files in the Repository

* **Readme.md**: this file
* **Sparkify_medium_data.ipython**:   iPython Notebook for analysis of medium sized subset (237MB) on local computer.
* **Sparkify_aws.ipynb**: iPython Notebook for analysis of the full dataset (12GB) on Amazon EMR.
* **plot.ipynb**: iPython Notebook to generate some of the plots in the project report.
* **SparkifyProjectReport.pdf**: Project report in pdf format.


## Computation Platform
The subset is analyzed with PySpark on a local computer running Python 3.7.

The full dataset is analyzed with PySpark and Hadoop on Amazon EMR cluster.

## Data Enignieering
In data cleaning, missing values in user firstname and lastname are removed. Both continuous and categorical features are created from the user transaction logs. Data pipleine is used to transform some features from string to index and encode them with one-hot encoding.

Two types of churn are defined, one for membership cancellation and the other for membership level downgrade.

## Machine Learning Model
Three classifiers are compared for the churn prediction: logistic regression, random forest, and gradient boosted trees (GBT). 

F1 score is used as prediction performance metric because the data is imbalanced. 

GBT shows the best performance and its setting is tuned using 3-fold cross validation. The best model is applied to the full dataset on Amazon EMR cluster.

## Result
The GBT classifier achieve F1 score of 0.53. The model provides the feature importance which helps to identify the most significant features that are associated to churn. The difference in feature value between users who have churned and those who haven't is analyzed.

Finally areas of improvements for future work are proposed.