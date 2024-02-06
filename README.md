# cs5780_kaggle_competition
https://www.kaggle.com/competitions/movie-review-preference-analysis

Together with @Suphakrit Lertkitcharoenvong.

Sentiment analysis is a fascinating field in natural language processing (NLP) that deals with understanding the emotions conveyed in written text. As a natural extension to this established problem, in this competition, a model is built to automatically detects the more positive review in any pairs of movie reviews.

Specifically, for every pair of reviews (r0, r1), we are given the feature vectors (E(r0), E(r1)) encoded by a language model. The goal is to build a model that can predict y, the binary label representing the "preference" between these two reviews. We predict 1 if r0 is more positive than r1 and 0 otherwise. We use the Accuracy of the test data as the evaluation metric.

The best strategy:
We used sklearn.svm.SVC with a rbf kernel. For data preparation we combined emb1 and emb2 and the corresponding labels. We used cross validation set to 5 instead of splitting into training/validation sets. Performed several GridSearchCV to narrow down the best parameters and settled on 'C'=2.5 and 'gamma'=2.25. During the training we also enabled predict_proba, this allowed us to resolve conflicts when emb1 and emb2 had the same prediction - we would go with whichever movie review had the higher confidence.