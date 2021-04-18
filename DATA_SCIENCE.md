# Data Science

## Collecting

Types of Biases you can encounter:
- Selection bias 
- Undercoverage bias 
- Survivorship bias


## Exploring

- 1 dimensional dataset
    - Smallest, largest, mean and standard deviation
    - Histograms
- 2 dimensional dataset
    - Plot both dimensions (with respect to x) on a scatter plot
    - Look at the correlation between the dimensions
- Multiple dimensions
    - Make lots of pairwise scatter plots. That show the correlation between all the different variables

## Cleaning

- Cleaning and munging
    - Data should all be the same type
    - Create functions (and maybe even classes) that parses the data correctly
    - Check for outliers
- Manipulating the data
    - Create functions that do some groupings, pull things from the JSON etc.
- Rescaling the data
    - We will sometimes rescale our data so that each dimension has mean 0 and standard deviation 1. They provide the code for how to do this
- Dimensionality Reduction
    - They provide information on how to perform Principal Component Analysis

Also:
- A Box cox transformation is a statistical technique to transform non-normal dependent variables into a normal shape.


### Missing Data

If the data set is large, we can just simply remove the rows with missing data values. It is the quickest way; we use the rest of the data to predict the values.
For smaller data sets, we can substitute missing values with the mean or average of the rest of the data using the pandas' data frame in python. There are different ways to do so, such as df.mean(), df.fillna(mean).

Ways of inputting missing values in dataset: K-means clustering, linear regression, K-NN, decision trees.

### Outliers

- Drop them.
- If you can’t drop them then try a different model, normalise the data or use algorithms that are less affected by outliers (e.g. random forests)


## Feature Selection

- Filter Methods
    - Linear discrimination analysis
    - ANOVA
    - Chi-Square
- Wrapper Methods
    - Forward Selection: We test one feature at a time and keep adding them until we get a good fit
    - Backward Selection: We test all the features and start removing them to see what works better 
    - Recursive Feature Elimination: Recursively looks through all the different features and how they pair together

## Evaluation

When you perform a hypothesis test in statistics, a p-value can help you determine the strength of your results. p-value is a number between 0 and 1.

P-value <= 0.05 indicates strong evidence against the null hypotheses. So you can reject it.

## Maintaining

The steps of maintaining a deployed model.
1. Monitor: constantly monitor the performance accuracy
2. Evaluate: Evaluation metrics of the current model are calculated to determine if a new algorithm is needed
3. Compare: The new models are compared to each other to determine which model performs the best
4. Rebuild: The best performing model is re-built on the current state of the data

You will want to update an algorithm when: 
- You want the model to evolve as data streams through infrastructure 
- The underlying data source is changing
- There is a case of non-stationarity
