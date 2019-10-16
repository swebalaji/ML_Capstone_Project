## Online News Popularity Prediction 

The Internet is an important tool for sharing messages. 
A recent survey has shown that teenagers and adults read online news in their daily life.
This percentage has increased a lot in the past few years.
For reasons that more and more people read online news and editors want their news to be popular it would be meaningful to build a system to predict whether a news will be popular or not.
Such system can  help editors find how they could improve their news but also can bring significant commercial value. Thus we chose the “online news popularity” data set for capstone project.

## Process Flow in Online News Industry 
Prior to step 2 in this below diagram its important to check if the article is going to be popular or not. 


![Process Flow](https://github.com/swebalaji/ML_Capstone_Project/blob/master/Process_Flow.png)

## Problem Statement
Due to the increase in competition among the online news portals, Mashable has been facing a decrease in the number of shares of  its articles on social media which in turn has affected the advertisements featuring on its page.

## Objective of this Project
- To predict the popularity of news articles published by Mashable.com
- To find which data channel gains more popularity.
- To find which day the articles are more popular.

## Dataset Description 
The dataset summarizes heterogeneous set of features about the articles published by Mashable between 2013 and 2015.
- Number of Records : 39,643
- Number of features : 61
- Target column : 1 

We drop url and timedelta for further analysis since they are non predictive in nature.

## Data Dictionary
Below is a brief desrciption of the most important features in the data set:
![Feature 1]( https://github.com/swebalaji/ML_Capstone_Project/blob/master/feature1.png)

![Feature 2]( https://github.com/swebalaji/ML_Capstone_Project/blob/master/feature2.png)

## Insights obtained from the DataSet
1. Keywords tends to attract many people towards reading the article. As the number of keywords in an article increases the shares as well increases.
2. People tend to share the articles which are having decent amount of words in the title. People don’t appreciate short titles.
3. Number of images as means of visualization plays a huge role in determining the shares an article since people don't have the      patience and time to watch a video and then share it to others.
4. People are tending to read articles under the world category since they have a perception they can read and know everything that is happening in the world.
5. People tend to read a lot of articles on Tuesday and Wednesday because as the weekend approaches, they wish to do some leisure activities and relax may be like watching a movie.
6. We can see that if the keywords in an article is good, we are getting high amount of shares also if the keywords are average in an article, we are getting average amount of shares and with worst keywords we are getting very less amount of shares.

## Dealing with Skewness and Outliers
### Skewness
- Most of the features are right skewed. 
- In order to deal with this,power transformation techniques imported from pre processing package was used.

  - Box Cox Transformation : This can be utlized only when we have values greater than 0 in our dataset. Since we had negative values in    our data set we tried adding constant to the value x in the column(x-1+min(value in that  column)) and later proceded with the box      cox transfrmation 
  - Yeo Johnson Transformation: This can be used for both positive and negative data.
   Since the accuracy of the base model was fairly the same for both the techniques we went ahead throught with Yeo Johnson Technique.
   
### Outliers
- Most of the features contained outliers.
- The Transformation technique takes care partially of the outlier treatment.
- Further we cap the lower limit and upper limit outliers with the 1st percentile and 99th percentile values respectively.
![Outliers](https://github.com/swebalaji/ML_Capstone_Project/blob/master/outliers.png)

## Splitting the dataset
- Based on the shares of our articles of we classify them into categories. 
  **This is the step for converting a regression problem into a classification problem**.
- Models have been built with 2 categories as well as with 3 categories of our data.
- The number of categories have been chosen using the K Means clustering technique.
- We divide our data into three categories using the q cut function and creates a new column with the categories.
   - The categories 0, 1 ,2 correspond to less popular, popular and most popular articles in an online news portal.
- For binary classification Setting the threshold value greater than 1400 (no. of shares). 
  - The category 0 corresponds to non popular articles and 1 corresponds to popular articles.
## Dimensionality Reduction Techniques
We tried using three dimensionality techniques for the above dataset to reduce overfitting.
- Principal Component Analysis
- ExtraTreeClassifier 
- Recurrsive Feature Elimination 

## Recommendations 
- People are tending to read articles under the world category.Hence the best channel is world category.
- People tend to read a lot of articles on Tuesday and Wednesday. Hence best day to publish an article is Tuesday and Wednesday.


## References
- http://cs229.stanford.edu/proj2015/328_report.pdf

- https://www.semanticscholar.org/paper/The-Pulse-of-News-in-Social-Media%3A-Forecasting-Bandari-Asur/984d1f4522443f0ad6571d342c1b3088420fb4ec

- https://www.semanticscholar.org/paper/From-popularity-prediction-to-ranking-online-news-Tatar-Antoniadis/1764b34574f36e8844a4c35bd387b4eb17cced4c






