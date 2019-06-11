# Recommendation Systems: Cold Start Problem Case Study

## Business Problem
We want to make recommendations on which movies users would like to see. We have a file called requests.json which has users that we want to make predictions for. We will make predictions using a combination of two models, a collaborative start model ( ALS) and a regressor classifier like linear regression or random forest. We want to use a combination because some users will have a lot of data on reviews and other users will not have many reviews. We want a model that will be able to predict for both types of users.  

## Data Understanding 
We started with and understanding of ALS and established that our Ratings.json was our training set for ALS (issue: user in ratings, not in requests) and our Request.json was our test set for ALS/ cold start. We figured out where to start our cold start. We supplement with random forest based on the additional metadata: 
Features users.dat: ID, sex, age, occupation, zip code  
Features meta.csv: see below (includes movies.dat data)  

We took into account our timestamp data. If a movie was rated a long time ago it might not reflect current opinion. To solve for this issue we split the data using sklearn time series split. 

## Data Preparation 
We joined the movies.dat table with the metadata table. We did a left outer join on our movies.dat table and our metadata.csv. We used a multilabelbinarizer on our movie categories. Then we made decisions on NaNs for ratings and determined which features to include. 

## Modeling 
Our model results are saved as a predictions.json file. 

## Model Evaluation & Next Steps 
In the next iteration, we would like to one hot encoding user data.  We would also want predictor values to return movie titles in addition to movie ID. 











## Assignment

Each user is potentially interested in watching one or more of the movies specified in `requests.json`. Our job is to decide which movie or movies to recommend to these users.

Use a combination of matrix factorization model (ALS) and a cold start model (using user and movie metadata) to fill in the NaN values and predict ratings for these movies.

Your predictions will be scored as follows:

1. Each user may watch movies from your list, starting with the highest predicted rating.
2. Your model will be scored based on how well the users liked the movies they watched.

Minimal requirements:

1. You must replace each NA value with a prediction.
2. You must create both a matrix factorization and a cold start model.
3. You team must document its work in a GitHub repo.
4. Your repo must include multiple commits from each team member.


