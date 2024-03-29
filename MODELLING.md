# Modelling

TODO: Coding samples of all the above

### Bayes Theorem

The theorem gives you the posterior probability of an event given the prior knowledge

`P(A|B) = P(B|A)*P(A) / P(B)`

### Naive Bayes

It assumes independence of features

### Probability vs. Likelihood

- Probability quantifies anticipation (of outcome).
- Likelihood quantifies trust (in model).

### Generative vs. Discriminative Models

- A generative algorithm models how the data was generated in order to categorize a signal. It asks the question: based on my generation assumptions, which category is most likely to generate this signal? 
- A discriminative algorithm does not care about how the data was generated, it simply categorizes a given signal.

### Supervised vs. Unsupervised 

- Supervised: Training data is labelled
- Unsupervised: Training data is not necessarily labelled

### Exploding Gradients

Exploding gradients are a problem where large error gradients accumulate and result in very large updates to neural network model weights during training.
This has the effect of your model being unstable and unable to learn from your training data.

### Learning Rate

This adjusts the rate at which the weights get updated.


## Ensemble Methods

- They typically reduce overfitting in models and make the model more robust (unlikely to be influenced by small changes in the training data).


### Voting Classifiers
- One of the easiest ways to get a better performing classifier is to use majority voting. E.g. many models vote, and the majority class wins
- They provide code of a voting classifier
- Apparently these can perform very well

### Bagging and Pasting

Bagging tries to implement similar learners on small sample populations and then takes a mean of all the predictions.

- Instead of using lots of different models on the same set of data you could instead using the same model but on several different subsets of the data
- If the data is sampled with replacement it is called bagging
- If the data is sample without replacement it is called pasting
- Generally, the net result is that the ensemble has a similar bias but a lower variance than a single predictor trained on the original training set.
- They again provide code for doing this with sklearn
- Note there are several quite important hyperparameters for scikit learn’s bagging methods


### Boosting

Boosting is an iterative technique which adjust the weight of an observation based on the last classification.

- Refers to any ensemble method that combines several weak learners into a strong learner
- The general idea of most boosting methods is to train predictors sequentially, each trying to correct its predecessor.
- By far the most popular boosting methods are AdaBoost and Gradient Boost
- AdaBoost
    - One way for a new predictor to correct its predecessor is to pay a bit more attention to the training instances that the predecessor underfitted. This results in new predictors focusing more and more on the hard cases. This is the technique used by AdaBoost.
- Gradient Boosting
    - Another very popular Boosting algorithm is Gradient Boosting.17 Just like AdaBoost, Gradient Boosting works by sequentially adding predictors to an ensemble, each one correcting its predecessor. However, instead of tweaking the instance weights at every iteration like AdaBoost does, this method tries to fit the new predictor to the residual errors made by the previous predictor.

Implementations:

- XGBoost 
    - An optimized distributed gradient boosting library designed to be highly efficient, flexible and portable. 
    - It implements machine learning algorithms under the Gradient Boosting framework. 
    - XGBoost provides a parallel tree boosting (also known as GBDT, GBM) that solve many data science problems in a fast and accurate way. 
- LightGBM https://lightgbm.readthedocs.io/en/latest/Features.html
    - LightGBM is a gradient boosting framework that uses tree based learning algorithms. It is designed to be distributed and efficient with the following advantages:
    - Faster training speed and higher efficiency.
        - Lower memory usage.
        - Better accuracy.
        - Support of parallel, distributed, and GPU learning.
        - Capable of handling large-scale data.

### Stacking
- It is based on a simple idea: instead of using trivial functions (such as hard voting) to aggregate the predictions of all predictors in an ensemble, why don’t we train a model to perform this aggregation?


## Overfitting

- Keep the model simple (fewer variables and parameters)
- Use cross-validation techniques
- Regularisation (LASSO penalises certain model parameters)
    - LASSO: 
        - Shrunks the coefficients to 0. 
        - Good for variable selection.
    - Ridge:
        - Makes the coefficients smaller
    - Elastic Net:
        - Tradeoff between variable selection and small coefficients

## Evaluating Models

- Split into train, validation and test sets
- F1 score, accuracy, confusion matrices
- Mean Square Error
- Root Mean Square Error
- Maximum Likelihood: The weight that is most likely is the weight that maximizes the probability of the observed training data

### Bias/Variance

Bias is that the model is too simple and is underfitting the training data
- If your model has high bias (which means it performs poorly even on your training data) then one thing to try is adding more features or making the model more complex.

Variance is that the model is too complex and is overfitting the training data
- If your model has high variance, then you can remove features, use regularisation or simplify the model.


### ROC Curve

It’s a graph of the true positive and false positive rates. It is used to show the trade-off between the sensitivity of the model vs. the fall-out or the probability it’ll trigger a false alarm

- Used for binary classifiers
- It is very similar to the precision/recall curve, but instead of plotting precision versus recall, the ROC curve plots the true positive rate (another name for recall) against the false positive rate.


### Precision, Recall and Specificity

- Recall (sensitivity): The number of positives your models claims compared to the actual number of positives
- Precision: A measure of the amount of accurate positives your model claims compared to the total number of positives it claims
- Specificity: Probability of, given a negative example, a negative test result.

### Early Stopping

Stop training when the validation accuracy plateuas or starts to increase

### F1 Score

- It is a weighted average of the precision and recall of the model. 1 is the best, 0 is the worst.
- You would use it in classification tests where true negatives don’t matter much


## Regularisation

Regularisation is the process of adding tunning parameter to a model to induce smoothness in order to prevent overfitting.
This constant is often the L1(Lasso) or L2(ridge).

- Regularisation discourages large coefficients
- Ridge regression, we add a penalty proportional to the sum of the squares of the beta_i



### L1 and L2 Regularisation

- L2 spreads the error among all the terms
- L1 is binary

## Stratified Sampling

Make sure your test set is done with stratified sampling (e.g. the distribution of the test set is the same as the train set)

