# Feature Engineering

## Categorical Predictors

| Technique | Details | Example |
| - | - | - |
| Nominal | Converting categorical variables into numbers | `[a, b, c]` -> `[0, 1, 2]` |
| One-Hot | Converting into 0 and 1s | `[a, b, c]` -> `[[1, 0, 0], [0, 1, 0], [0, 0, 1]]` |



## Numerical Predictors


### 1-to-1 Transformations

| Technique | Details | Example |
| - | - | - |
| Normalising | Convert the numbers to be between 0 and 1 | `[1, 5, 10]` -> `[0.1, 0.5, 1.0]` |
| Centering | Making the centre of the data 0 | `[0, 5, 10]` -> `[-5, 0, 5]` |
| Running Mean | For time or sequence data you could run a 5-point mean which would replace each data point with the average of itself and the two data points before and after it’s position | - |

### 1-to-Many Transformations

| Technique | Details | Example |
| - | - | - |
| Nonlinear Features | Square/Cube/etc. a feature | `[1, 2, 3]` -> `[1, 4, 9]` |
| Splines and Winsorizing | - | - |
| Discretizing Predictors | (last resort) Unsupervised: user-driven cutoffs or estimated percentiles. Using ROC curves to cut them off | - |


### Many-to-Many Transformations

Feature engineering,  PCA


| Technique | Details | Example |
| - | - | - |
| Removing collinear features | Find features that are proportional to each other | - |
| PCA | Find a certain number of principle components of features therefore reducing the number of features. | - |
| Kernel Principal Component | PCA is effective when the predictors are linearly correlated. However, kernel PCA can handle other scenarios. | - |
| Independent Component Analysis | - | - |
| Non-negative Matrix Factorization | - | - |
| Partial Least Squares | Partial least squares (PLS) is a supervised version of PCA that reduces dimension in a way that is optimally related to the response | - |
| Autoencoders | - | - |
| Spatial Sign | The spatial sign transformation takes a set of predictor variables and transforms them in a way that the new values have the same distance to the center of the distribution | - |
| Distance and Depth Features | In classification, it may be beneficial to make semi-supervised features from the data. In this context, this means that the outcome classes are used in the creation of the new predictors but not in the sense that the features are optimized for predictive accuracy. | - |



# Handling Class Imbalances

- Collect more data to even the imbalances (carefully)
- Resample the dataset to correct for imbalances
- Try a different algorithm altogether on your dataset

