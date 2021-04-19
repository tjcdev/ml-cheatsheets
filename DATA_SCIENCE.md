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
- Investigating Relationships
    - Correlations
    - Regression

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

### Filter Methods

Explanations of data science methods: https://researchbasics.education.uconn.edu/anova_regression_and_chi-square/#

- T-test:
    - A t test can only compare the means of two groups (independent variable, e.g., gender) on a single dependent variable (e.g., reading score). You may wish to review the instructor notes for t tests.
    - One Independent Variable (With Two Levels (e.g. Male and Female)) and One Dependent Variable
    - When we wish to know whether the means of two groups (one independent variable (e.g., gender) with two levels (e.g., males and females) differ, a t test is appropriate. In order to calculate a t test, we need to know the mean, standard deviation, and number of subjects in each of the two groups. An example of a t test research question is “Is there a significant difference between the reading scores of boys and girls in sixth grade?” A sample answer might be, “Boys (M=5.67, SD=.45) and girls (M=5.76, SD=.50) score similarly in reading, t(23)=.54, p>.05.”
- One-way ANOVA:
    - One Independent Variable (With More Than Two Levels e.g. political party Democrat, Republican and Independet ) and One Dependent Variable. If we have one independent variable (with three or more groups/levels) and one dependent variable, we do a one-way ANOVA.
    - If the independent variable (e.g., political party affiliation) has more than two levels (e.g., Democrats, Republicans, and Independents) to compare and we wish to know if they differ on a dependent variable (e.g., attitude about a tax cut).
    - The one-way ANOVA has one independent variable (political party) with more than two groups/levels (Democrat, Republican, and Independent) and one dependent variable (attitude about a tax cut).
- Two-way ANOVA:
    - A two-way ANOVA has two independent variable (e.g. political party and gender), a three-way ANOVA has three independent variables (e.g., political party, gender, and education status), etc. These ANOVA still only have one dependent variable (e.g., attitude about a tax cut). 
    - A two-way ANOVA has three research questions: One for each of the two independent variables and one for the interaction of the two independent variables.
    - A two-way ANOVA has three null hypotheses, three alternative hypotheses and three answers to the research question. The answers to the research questions are similar to the answer provided for the one-way ANOVA, only there are three of them.
- MANOVA:
    - One or More Independent Variables (With Two or More Levels Each) and More Than One Dependent Variable
    - Sometimes we have several independent variables and several dependent variables. In this case we do a MANOVA (Multiple ANalysis Of VAriance). Suffices to say, multivariate statistics (of which MANOVA is a member) can be rather complicated.

### Wrapper Methods
- Forward Selection: We test one feature at a time and keep adding them until we get a good fit
- Backward Selection: We test all the features and start removing them to see what works better 
- Recursive Feature Elimination: Recursively looks through all the different features and how they pair together

### Non Parametric Data Analysis

- Chi-Square
    - We might count the incidents of something and compare what our actual data showed with what we would expect. Suppose we surveyed 27 people regarding whether they preferred red, blue, or yellow as a color. If there were no preference, we would expect that 9 would select red, 9 would select blue, and 9 would select yellow. We use a chi-square to compare what we observe (actual) with what we expect. 
    - Chi-square helps us make decisions about whether the observed outcome differs significantly from the expected outcome. 
    - Just as t-tests tell us how confident we can be about saying that there are differences between the means of two groups, the chi-square tells us how confident we can be about saying that our observed results differ from expected results.

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
