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
Original fields in the raw dataset:
userId: unique identifier for each user
firstName: demographic information of each user
lastName: demographic information of each user
location: demographic information of each user
gender: demographic information of each user
userAgent: device that the user used
sessionId:unique identifier for each session
itemInSession: unique identifier for each item in a same session
page: the specific page of website that the user visited, used to identify churn
song: if the page is 'NextSong', this field will show the name of the song, otherwise only show 'null'
artist: if the page is 'NextSong', this field will show the name of the artist, otherwise only show 'null'
level: categorical features that only has 2 values, free or paid
registration: the timestamp of user registration
ts: the timestamp of user action
status : status code There are three HTTP status codes 307: Temporary Redirect, 404: Not Found, 200: OK
auth : authentication (cancelled/logged in)
method : PUT/GET
length : length of item
1. **EDA**
Illustrated in sparkify-EDA.ipynb, EDA involved taking care of missing values,understanding unique values in every column and how data 
is organised. There were 225 unique users out of which 53 churned (23.11% churn rate). EDA also involved analysing characteristics of churned users i.e gender,level(paid/free),total number of sessions, etc.
2. **Feature Engineering**



### Summary of Results
As it is a classification problem(churn/not churn)-LogisticRegression,RandomForest and GradientBoost algorithms have been used. Random Forest Classifier required the least computational power, could handle data imbalance and has a high F1 score. Hence,the hyperparameters
were tuned.
| Model |F1 score |
| --- | --- |
| Logistic Regression( without tuning) | 81.03%|
| Gradient Boost (without tuning)| 83.77% |
| Randon Forest (without tuning)| 83% |
| Randon Forest (with tuning)| 87.38% |



