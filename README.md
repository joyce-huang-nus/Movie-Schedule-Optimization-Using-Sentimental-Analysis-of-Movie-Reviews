# Movie-Schedule-Optimization-Using-Sentimental-Analysis-of-Movie-Reviews

## Introduction
The majority of cinema income is from screening new release films. A hit film results in high ticket income and high concession sales, and vice versa. Therefore, film arrangement is a significantly essential task for cinemas. Traditionally, theaters would predict a high box office for a movie with famous producers, popular cast and high budget and allocate more screenings to these kinds of movies. This is also how audiences made their decision in the past. However, with the spread of SNS and online critics commentaries, people tend to search for comments on the Internet before buying a ticket. As a result, people’s comments become more and more important to affect the revenue of a movie

## Problem Statement and Project Objective
Firstly, we would like to understand whether ranking on movie rating websites will affect potential audiences’ willingness to watch the movie. If a movie has a high rank, it will attract more audiences to go to the theaters to watch this movie. However, for newly released movies, the website should wait for days to conclude a rating, and cinemas
apparently could not wait. They need to conclude how the first batch of audiences react on SNS and use this information to arrange their screenings. Thus, the next step is to predict the rating. We decided to formulate a model to analyze audiences’sentiment by their text comments on the Internet. In this way, cinemas can easily gain a quick conclusion from people's comments and make decisions.

## Methodology
We firstly apply linear regression to gain the effects of Internet rating on movie revenue. Then we use TextBlob to explore the polarity and subjectivity of movie review comments. After that we evaluate the plain accuracy and confusion matrix of four models: Logistic Regression, SVM, Naive Bayes and K-nearest Neighbors Classifier, and choose Naive Bayes as our final model.

### Relationship between Internet Rating and Movie Revenue
To confirm our hypothesis that Internet comments are affecting the revenue of movies, we did a simple linear regression.

#### OLS Regression Result
The coefficient of vote_average is 0.4747 and p value is 0, which means vote_average has a significant
positive correlation with movies’ revenue. The result matches our hypothesis and we can move to the next
step.

### Sentimental Analysis using TextBlob
We wanted to know whether the movie comments are consistent with the review scores, so we calculated the polarity scores to see if comments with positive scores are given higher review scores. Moreover, we calculated the subjectivity score to see if the subjectivity score is higher when the absolute value of the polarity score is high.

#### Sentimental Analysis Criteria
● Polarity ~ [-1,1], 0 is neutral, +1 is positive, -1 is negative.
● Subjectivity ~ [0,1], 0 is objective and 1 is subjective.

#### Feature engineering
<img width="476" alt="feature-engineering" src="https://user-images.githubusercontent.com/88580416/145959178-a20d9c09-6cbb-4cb2-a5a8-ad2a5dfb403d.PNG">

#### Data Encoding
Encode review_rank to numeric values
Encode review_type to dummy variables
<img width="469" alt="rotten_tomato-df" src="https://user-images.githubusercontent.com/88580416/145959326-54e9a999-5e7c-4e6b-b565-b198957981ee.PNG">

#### EDA and Preliminary Results
This scatter plot illustrates the polarity score distribution within each review score. As you can see, there are more data points that have a positive polarity score in higher review scores and there are less data points that have a positive polarity score in lower review scores. For example, At review score 12, which corresponds to review score A in the original dataset, we see there are comparatively less data points that have a negative polarity score.

<img width="278" alt="polarity-scatter" src="https://user-images.githubusercontent.com/88580416/145959538-4e436b4c-32a1-4852-9ebd-289305ca5622.PNG">

Furthermore, we compute the average polarity score in each review score range. Interestingly, the higher the review score, the higher the polarity score. We concluded that the polarity score, which is calculated from the review comments, and review score, which is ranked initially by commenters, have a positive correlation.

<img width="266" alt="average-lineplot" src="https://user-images.githubusercontent.com/88580416/145959690-8e54fdb5-e4b7-4b7f-9f84-855422cbdfdc.PNG">

We also wanted to know if the polarity score calculated from movie comments has a significant effect on review score, so we ran an OLS regression model. The polarity score has a positive coefficient and a 0.0000 p-value, meaning that the polarity score has a significant effect on the review score and they are positively correlated.

<img width="280" alt="regression" src="https://user-images.githubusercontent.com/88580416/145959816-2fde8dd3-af08-4e04-b8b7-20387afc8e02.PNG">

We also plot all the data points using their polarity score and subjectivity score calculated from the review comments. We concluded that more polar comments tend to be more subjective.

<img width="231" alt="scatter-01" src="https://user-images.githubusercontent.com/88580416/145960033-14b9544f-b2e6-4bce-a479-cbde73e96cda.PNG">

In this graph, we filtered out the comments that are too subjective (subjectivity score > 0.8) and the movies that have only one comment. Therefore, we have all the data points that have a subjectivity score <= 0.8 and have 2 or more review comments for each movie. Then, we calculated the polarity score of the review comments for each movie and plot against the review score. We saw a slightly positive correlation between the average polarity score for each movie and review scores.

<img width="248" alt="scatter-02" src="https://user-images.githubusercontent.com/88580416/145960093-18725a06-e0ae-4e0e-808c-9f191e2f3b60.PNG">

### Predict movie sentiments with classification models
