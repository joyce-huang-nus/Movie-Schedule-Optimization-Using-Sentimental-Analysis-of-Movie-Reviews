# Movie-Schedule-Optimization-Using-Sentimental-Analysis-of-Movie-Reviews

# Introduction
The majority of cinema income is from screening new release films. A hit film results in high ticket income and high concession sales, and vice versa. Therefore, film arrangement is a significantly essential task for cinemas. Traditionally, theaters would predict a high box office for a movie with famous producers, popular cast and high budget and allocate more screenings to these kinds of movies. This is also how audiences made their decision in the past. However, with the spread of SNS and online critics commentaries, people tend to search for comments on the Internet before buying a ticket. As a result, people’s comments become more and more important to affect the revenue of a movie

# Problem Statement and Project Objective
Firstly, we would like to understand whether ranking on movie rating websites will affect potential audiences’ willingness to watch the movie. If a movie has a high rank, it will attract more audiences to go to the theaters to watch this movie. However, for newly released movies, the website should wait for days to conclude a rating, and cinemas
apparently could not wait. They need to conclude how the first batch of audiences react on SNS and use this information to arrange their screenings. Thus, the next step is to predict the rating. We decided to formulate a model to analyze audiences’sentiment by their text comments on the Internet. In this way, cinemas can easily gain a quick conclusion from people's comments and make decisions.

# Methodology
We firstly apply linear regression to gain the effects of Internet rating on movie revenue. Then we use TextBlob to explore the polarity and subjectivity of movie review comments. After that we evaluate the plain accuracy and confusion matrix of four models: Logistic Regression, SVM, Naive Bayes and K-nearest Neighbors Classifier, and choose Naive Bayes as our final model.
