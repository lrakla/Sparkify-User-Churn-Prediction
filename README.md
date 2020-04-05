# Sparkify-User-Churn-Prediction
A ML project which uses music streaming data to model users who will leave the platform(churn). The insights are available in a blog post.

## Table of Contents
1. [Project Motivation](#motivation)
2. [Software Requirements](#software-requirements)
3. [Files](#Files)
4. [Steps](#steps)
5. [Summary of Results](#summart-of-results)

### Motivation
This project aims to tackle one of the most important use cases of Big Data in business - Churn prediction which  is key to retaining customers. It does so by using [Apache Spark](https://spark.apache.org/) - the leading, developer-friendly platform for big data.
Being a Udacity Data Scientist Capstone Project, it deals with Sparkify is a fictional music streaming platform created by Udacity. For this project we are given log data of this platform in order to drive insights and create a machine learning pipeline to predict churn.
The data is available as 128Mb, 254Mb & full 12Gb(on AWS). This project utilizes the 128Mb data in Spark local mode which can be scaled up when using the full dataset.

### Software Requirements
* Spark (Read about installation [here](https://changhsinlee.com/install-pyspark-windows-jupyter/) )
* Anaconda 3
* Python 3.7
* Libraries - pyspark, pandas, seaborn, numpy

### Files
* sparkify-EDA.ipynb - A notebook with exploratory data analysis
* sparkify.ipynb - A notebook with feature engineering and modelling
* EDA - a folder containing visualisations of data

### Steps
The data is spread over two months and contains logs of user actions. 
1. **EDA**


### Summary of Results
As it is a classification problem(churn/not churn)-LogisticRegression,RandomForest and GradientBoost algorithms have been used.




