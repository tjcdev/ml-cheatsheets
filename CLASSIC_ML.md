# Models

- Advantage/Disadvantages https://leportella.com/cheatsheet/machine-learning/

## Classic Models

### Linear Regression

Require numerical features.

A common measure of success is the coefficient of determination (or R-squared), which measures the fraction of the total variation in the dependent variable that is captured by the model

Polynomial regression
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

Entropy and Information Gain
- Entropy: ID3 uses enteropy to check the homogeneity of a sample. If the sample is completely homogenious then entropy is zero and if the sample is an equally divided it has entropy of one.
- Information Gain: The Information Gain is based on the decrease in entropy after a dataset is split on an attribute. Constructing a decision tree is all about finding attributes that returns the highest information gain.

### Random Forest

- Multiple decision trees and then you left them vote on the answer
- Ensemble of decision trees, usually through bagging
- A great feature of random forests is that they can give “feature importance” metrics.

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

SVM stands for support vector machine, it is a supervised machine learning algorithm which can be used for both Regression and Classification. If you have n features in your training data set, SVM tries to plot it in n-dimensional space with the value of each feature being the value of a particular coordinate. SVM uses hyper planes to separate out different classes based on the provided kernel function.

They try to draw a hyper plane (in high dimensional spaces they use the kernel trick) to split the data and give classifications.

- Adding polynomial features is simple to implement and can work great with all sorts of Machine Learning algorithms (not just SVMs), but at a low polynomial degree it cannot deal with very complex datasets, and with a high polynomial degree it creates a huge number of features, making the model too slow.
- Fortunately, when using SVMs you can apply an almost miraculous mathematical technique called the kernel trick

SVM Kernel Functions:
- Linear Kernel 
- Polynomial kernel 
- Radial basis kernel 
- Sigmoid kernel


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


## Ranking

RankNet, LambdaRank and LambdaMART are all LTR algorithms.

## NLP

### Topic Modelling
- A technique called Latent Dirichlet Analysis (LDA) is commonly used to identify common topics in a set of documents.
- They say that LDA is similar to Naive Bayes Classifiers
- They list the assumptions made by LDA models
- They describe the algorithm that is being used when running these models
- This is a really good way of getting some words that are indicators of a topic. Use this.
