# Modelling


### Bias/Variance

- Bias is that the model is too simple and is underfitting the training data
- Variance is that the model is too complex and is overfitting the training data
- You need to balance these
- How vulnerable is your model to different training/validation/test sets
- High bias and low variance typically correspond to underfitting
- If your model has high bias (which means it performs poorly even on your training data) then one thing to try is adding more features.
- If your model has high variance, then you can similarly remove features



### Supervised vs. Unsupervised 

- Supervised: Training data is labelled
- Unsupervised: Training data is not necessarily labelled

### ROC Curve

It’s a graph of the true positive and false positive rates. It is used to show the trade-off between the sensitivity of the model vs. the fall-out or the probability it’ll trigger a false alarm

- Used for binary classifiers
- It is very similar to the precision/recall curve, but instead of plot‐ ting precision versus recall, the ROC curve plots the true positive rate (another name for recall) against the false positive rate.


### Precision and Recall

- Recall is the true positive rate. The number of positives your models claims compared to the actual number of positives
- Precision is a measure of the amount of accurate positives your model claims compared to the total number of positives it claims

### Bayes Theorem

The theorem gives you the posterior probability of an event given the prior knowledge

### Naive Bayes

It assumes independence of features

### L1 and L2 Regularisation

- L2 spreads the error among all the terms
- L1 is binary

### Probabilty vs. Likelihood

- Probability quantifies anticipation (of outcome).
- Likelihood quantifies trust (in model).

### Generative vs. Discriminative Models

- A generative algorithm models how the data was generated in order to categorize a signal. It asks the question: based on my generation assumptions, which category is most likely to generate this signal? 
- A discriminative algorithm does not care about how the data was generated, it simply categorizes a given signal.

### F1 Score

- It is a weighted average of the precision and recall of the model. 1 is the best, 0 is the worst.
- You would use it in classification tests where true negatives don’t matter much

## Ensemble Methods

- They typically reduce overfitting in models and make the model more robust (unlikely to be influenced by small changes in the training data).
- Bagging is when each model in the ensemble votes with equal weight
- Boosting involves incrementally building an ensemble by training each new model instance to emphasize the training instances that previous models mis-classified. Tends to over-fit the training data. Adaboost is the most common. The misclassified points from one model are assigned higher weights for the next model to work with

Voting Classifiers
- One of the easiest ways to get a better performing classifier is to use majority voting. E.g. many models vote, and the majority class wins
- They provide code of a voting classifier
- Apparently these can perform very well

Bagging and Pasting
- Instead of using lots of different models on the same set of data you could instead using the same model but on several different subsets of the data
- If the data is sampled with replacement it is called bagging
- If the data is sample without replacement it is called pasting
- Generally, the net result is that the ensemble has a similar bias but a lower variance than a single predictor trained on the original training set.
- They again provide code for doing this with sklearn
- Note there are several quite important hyperparameters for scikit learn’s bagging methods

Random Forests
- Ensemble of decision trees, usually through bagging
- A great feature of random forests is that they can give “feature importance” metrics. This could be create for images!

Boosting
- Refers to any ensemble method that combines several weak learners into a strong learner
- The general idea of most boosting methods is to train predictors sequentially, each trying to correct its predecessor.
- By far the most popular boosting methods are AdaBoost and Gradient Boost
- AdaBoost
    - One way for a new predictor to correct its predecessor is to pay a bit more attention to the training instances that the predecessor underfitted. This results in new predic‐ tors focusing more and more on the hard cases. This is the technique used by AdaBoost.
- Gradient Boosting
    - Another very popular Boosting algorithm is Gradient Boosting.17 Just like AdaBoost, Gradient Boosting works by sequentially adding predictors to an ensemble, each one correcting its predecessor. However, instead of tweaking the instance weights at every iteration like AdaBoost does, this method tries to fit the new predictor to the residual errors made by the previous predictor.

Stacking
- It is based on a simple idea: instead of using trivial functions (such as hard voting) to aggregate the predictions of all predictors in an ensemble, why don’t we train a model to perform this aggregation?


## Overfitting

- Keep the model simple (fewer variables and parameters)
- Use cross-validation techniques
- Regularisation (LASSO penalises certain model parameters)


## Evaluating Models

- Split into train, validation and test sets
- F1 score, accuracy, confusion matrices
- Mean Square Error
- Root Mean Square Error
- Maximum Likelihood: The weight that is most likely is the weight that maximizes the probability of the observed training data

## Regularisation

- Regularisation discourages large coefficients
- Ridge regression, we add a penalty proportional to the sum of the squares of the beta_i

## Stratified Sampling

Make sure your test set is done with stratified sampling (e.g. the distribution of the test set is the same as the train set)

