# Data Science Project

Dataset: [link][https://archive.ics.uci.edu/dataset/462/drug+review+dataset+drugs+com]

## Built-in features
- drugName (categorical): name of drug
- condition (categorical): name of condition
- review (text): patient review
- rating (numerical): 10-star patient rating
- date (date): date of review entry
- usefulCount (numerical): no. of users who found review useful

## Engineered Features
- sentimentPolarity (numerical): measured using NLTK
- usefulScore (numerical): normalised usefulCount*rating, essentially a weighted average of rating scaled down from 0 - 1 . ( usefulCount - weighted average of usefulCount per condition)
- review_score = 0.6*rating + 0.3*useful_count + 0.1*sentiment_score
## Metric : 
usefulScore was normalised  
if usefulScore  > 0.5 :  Recommendable Drug 
else if usefulScore  < 0.5 :  Not Recommendable Drug

### Training features : TF-IDF matrix, condition
### Output Binary Prediction : useful Score [ 0/1]


## Best Medicine for a given condition
- For each condition, it identifies the data point with the highest confidence score (distance from the decision boundary) [ using logistic regression ] ( output is in .[output][output.txt]

## Model: Best-K Review Scores

- We devised a composite score to gauge product/service performance based on textual reviews. The formula is as follows:

 review_score = 0.6*rating + 0.3*useful_count + 0.1*sentiment_score
