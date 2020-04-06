# Sparkify-User-Churn-Prediction
A ML project which uses music streaming data to model users who will leave the platform(churn). The insights are available in a [blog post]().

## Table of Contents
1. [Project Motivation](#motivation)
2. [Software Requirements](#software-requirements)
3. [Files](#Files)
4. [Steps](#steps)
5. [Summary of Results](#summary-of-results)

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
- userId: unique identifier for each user
- firstName: demographic information of each user
- lastName: demographic information of each user
- location: demographic information of each user
- gender: demographic information of each user
- userAgent: device that the user used
- sessionId:unique identifier for each session
- itemInSession: unique identifier for each item in a same session
- page: the specific page of website that the user visited, used to identify churn
- song: if the page is 'NextSong', this field will show the name of the song, otherwise only show 'null'
- artist: if the page is 'NextSong', this field will show the name of the artist, otherwise only show 'null'
- level: categorical features that only has 2 values, free or paid
- registration: the timestamp of user registration
- ts: the timestamp of user action
- status : status code There are three HTTP status codes 307: Temporary Redirect, 404: Not Found, 200: OK
- auth : authentication (cancelled/logged in/logged out)
- method : PUT/GET
- length : length of item
1. **EDA** - 
Illustrated in [sparkify-EDA.ipynb](https://github.com/lrakla/Sparkify-User-Churn-Prediction/blob/master/Sparkify-EDA.ipynb), EDA involved taking care of missing values,understanding unique values in every column and how data 
is organised. There were 225 unique users out of which 53 churned (23.11% churn rate). EDA also involved analysing characteristics of churned users i.e gender,level(paid/free),total number of sessions, etc. Graphs are available [here] (https://github.com/lrakla/Sparkify-User-Churn-Prediction/tree/master/EDA)

2. **Feature Engineering** - 
By manipulating original fields,following aggregates are created :
- *Session Related Feature* :
number of visited session(sessionId), average visit time of each session, average gap days of sessions
- *Time Related Feature* :
registered days, days between last visit and the last day in the dataset
- *Page View Related Feature*:
total number of visited pages, % of different pages
- *Music Related Features* :
total number of unique songs & artists per user
- *User Information* :
gender, level(encoded as 0s and 1s)
- *Miscellaneous* :
Total items in session per user,total visit of each user, total length per user.

3. **Modelling**
As it is a classification problem(churn/not churn)-LogisticRegression,RandomForest and GradientBoost algorithms have been used.
Spark MLlib is used to build machine learning models with large datasets, far beyond what can be done with non-distributed technologies like scikit-learn. F1 score is used as metric as only 23% of users churned (meaning accuracy is not a reliable metric).

### Summary of Results
Random Forest Classifier required the least computational power, could handle data imbalance and has a high F1 score. Hence,the hyperparameters
were tuned.
| Model |F1 score |
| --- | --- |
| Logistic Regression( without tuning) | 82.77%|
| Gradient Boost (without tuning)| 83.77% |
| Randon Forest (without tuning)| 83% |
| Randon Forest (with tuning)| 89.40% |

The best parameters are maxDepth : 10 and numTrees : 70.
The most important features are :
1.	registered_days	0.090355
2.	avg_gap_time_days	0.080672
3.  Thumbs Down	0.056604
4.	count(DISTINCT artist)	0.044727
5.	Thumbs Up	0.040446
6.  NextSong	0.038806
7.	Downgrade	0.036481
8.	count(DISTINCT sessionId)	0.031141
9.	visit_count	0.028938
10.	Roll Advert	0.028307
11.	Add to Playlist	0.024286
12.	avg_session_duration_mins	0.019367
13.	Logout	0.019225
14.	Home	0.018391
15.	count(DISTINCT song)	0.017147
16.	avg_daily_items	0.016997
17.	Add Friend	0.016765
18.	Settings	0.014395
19.	Help	0.012654
20.	Save Settings	0.012421
21.	Upgrade	0.012353
22.	About	0.011977
23.	count	0.011706
24.	Error	0.011225
25.	total_length	0.009458
26.	gender	0.006470
27.	Submit Upgrade	0.003895
28.	Submit Downgrade	0.002772
29.	level	0.000566

### Points to be noted
The outputs are for a mini dataset and there may be a slight imbalance in the data. Therefore, the full 12Gb dataset needs to have its own statistical analysis. The features generated become very important. Area Under Curve (AUC) can also be used as a metric. 

### Acknowledgements
Thanks to [Udacity](www.udacity.com) for the data and project motivation.



