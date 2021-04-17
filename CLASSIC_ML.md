# Models

- Advantage/Disadvantages https://leportella.com/cheatsheet/machine-learning/

## Classic Models

### Linear Regression

Require numerical features.

A common measure of success is the coefficient of determination (or R-squared), which measures the fraction of the total variation in the dependent variable that is captured by the model

- Polynomial regression
 - A simple way to do this is to add powers of each feature as new features, then train a linear model on this extended set of features.
 - So they use the sklearn class from sklearn.preprocessing import PolynomialFeatures to basically square one of the input features, and then fit a linear regression model to this. 
 - The PolynomialFeatures library also adds combinations of input features up to the specified degree. 


### Logistic Regression

Logistic regression is a classification algorithm used to predict a binary outcome for a given set of independent variables.

| Advantages | Disadvantages |
| - | - |
| Simple; Don't have to worry about features being correlated | Deals bad with outliers; |


### Decision Trees

- They can handle numerical and categorical data
- We are looking to find splits that have low entropy (i.e. there low uncertainty about the class of the resulting groups)

| Advantages | Disadvantages |
| - | - |
| Easy to understand and interpret; Handles outliers well; Doesn't need normalisation or dummy variables | It can overfit; Unstable (small changes in data lead to very different trees); Doesn't support online learning |

Pruning:
- Branches with weak predictive power are removed
- Simplest algorithm is replace each node, if it doesn’t decrease the predictive accuracy then keep it pruned

### Random Forest

- Multiple decision trees and then you left them vote on the answer
- Bootstrap aggregating a.k.a. bagging: Rather than training each tree on all the inputs in the training set, we train each tree on the result of bootstrap_sample(inputs). Since each tree is built using different data, each tree will be different from every other tree.

**Ensemble Learning**: 

A second source of randomness involves changing the way we chose the best_attribute to split on. Rather than looking at all the remaining attributes, we first choose a random subset of them and then split on whichever of those is best.
This is an example of a broader technique called ensemble learning in which we combine several weak learners (typically high-bias, low-variance models) in order to produce an overall strong model.

Random forests are one of the most popular and versatile models around.



### K-Nearest Neighbours

| Advantages | Disadvantages |
| - | - |
| Little training time; Works well with multi-class datasets; Good for unusual data | You need to pick value of k; Neighbors-based methods are known as non-generalizing machine learning methods, since they simply “remember” all of its training data; Not good with highly dimensional data |

### Gaussian Naive Bayes

Suited to yes-or-no features.

| Advantages | Disadvantages |
| - | - |
| Highly scalabe; Not sensitive to irrelevant features; Returns a degree of certainty for the answers; | Cannot learn interactions between features |

### SVM

- Adding polynomial features is simple to implement and can work great with all sorts of Machine Learning algorithms (not just SVMs), but at a low polynomial degree it cannot deal with very complex datasets, and with a high polynomial degree it creates a huge number of features, making the model too slow.
- Fortunately, when using SVMs you can apply an almost miraculous mathematical technique called the kernel trick

| Advantages | Disadvantages |
| - | - |
| High accuracy; Theoretical gaurantess regarding overfitting; Popular in text classification; | Memory intensive; Hard to interpret; Complicated to run and tune; |

### K-Means

Unsupervised models

| Advantages | Disadvantages |
| - | - |
| Good when you know how many clusters you need; Scales well with lots of samples; | Doesn't handle missing values well; Can't find clusters that aren't circles or spherical |

### Hierarchical Clustering

| Advantages | Disadvantages |
| - | - |
| Resulting hierarchical representation can be very informative; Provides an additional ability to visualize;  | Sensitive to noise and outliers; Computationally intensive O(N^2); |

### Gaussian Mixture Model

| Advantages | Disadvantages |
| - | - |
| Soft-clustering (you can see percentages of cluster participation on each sample); Cluster shape flexibility; | Sensitive to initialization values; Possible to converge to a local optimum; Slow convergence rate; |


## NLP

### Topic Modelling
- A technique called Latent Dirichlet Analysis (LDA) is commonly used to identify common topics in a set of documents.
- They say that LDA is similar to Naive Bayes Classifiers
- They list the assumptions made by LDA models
- They describe the algorithm that is being used when running these models
- This is a really good way of getting some words that are indicators of a topic. Use this.
