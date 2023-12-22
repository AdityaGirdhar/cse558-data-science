# Data Science Project

- Dataset: [link](https://archive.ics.uci.edu/dataset/462/drug+review+dataset+drugs+com)  
- Access Full report : [report](https://github.com/AdityaGirdhar/cse558-data-science/blob/main/DSc%20Final%20Presentation.pdf)
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

## Hypothesis Testing:
- Conducted chi-square tests for rating independence.
- Performed t-tests to assess correlation between ratings and sentiment scores.
  
## Insights Gained:
- Identified key patterns and trends in patient reviews.
- Discovered correlations between review sentiment and drug ratings.
  
## Challenges Overcome:
- Addressed data quality issues including unformatted HTML codes and missing values.
- Managed complexities in data standardization and feature extraction.
# First Goal ( Predict Condition from Review  ) 
- Used LSTM - The architecture comprises an embedding layer using pre-trained word vectors, bidirectional LSTM for context, followed by a linear layer with ReLU activation. It employs average and max pooling, concatenation, and dropout (10%) for feature extraction, achieving 86.8% accuracy.

- Used Convolutional Neural Network - The architecture employs pre-trained embeddings, followed by convolutional layers for n-gram feature extraction, ReLU activation, max pooling, and dropout (10%). A fully connected layer processes flattened output, achieving 88.4% accuracy.

# Second Goal ( Recommend Medicines ) 
## Model 1 : ( Binary Prediction of any medicine )
- Metric : 
usefulScore was normalised  
if usefulScore  > 0.5 :  Recommendable Drug 
else if usefulScore  < 0.5 :  Not Recommendable Drug

### Training features : TF-IDF matrix, condition
### Output Binary Prediction : useful Score  ( 0 / 1 )

## Model 2 Best Medicine for a given condition
- For each condition, it identifies the data point with the highest confidence score (distance from the decision boundary) using logistic regression.  [output](output.txt)

## Model 3: Best-K Review Scores

- We devised a composite score to gauge product/service performance based on textual reviews. The formula is as follows:

 review_score = 0.6*rating + 0.3*useful_count + 0.1*sentiment_score
## Limitation

Due to oversampling, some of the condition no. are generated to balance out the dataset for recommendable and non- recommendable medicines and hence, don't have a corresponding name associated with the condition id in [link](output.txt)
