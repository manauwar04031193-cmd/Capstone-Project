Assignment 1
Required Document:
Dataset

Task to do:
Cleaning

Dataset Description
Loaded the dataset using pd.read_csv().
Inspected structure using head(), dtypes, and shape.
Checked missing values and duplicate rows.
Cleaned the dataset before analysis.

Outpu Result:
Clean Dataset

Missing Value Strategy
Columns with more than 20% missing values were identified.
Numeric columns with fewer than 20% missing values were filled using the median.
Median was selected because it is robust to outliers and skewed distributions, while the mean can be distorted by extreme values.
Duplicate Removal
Duplicate rows were identified using duplicated().
Removed using drop_duplicates().
Reported the number of removed rows.
Compared missing-value percentages before and after removal.
Data Type Conversion
Converted incorrectly inferred numeric columns using pd.to_numeric(errors='coerce').
Converted repetitive string columns to category.
Compared memory usage before and after conversion.
Skewness Interpretation
Computed skewness for every numeric column.
The column with the highest absolute skewness was identified.
Positive skew indicates a long right tail caused by high-value outliers.
Negative skew indicates a long left tail caused by low-value outliers.
Since skewed data affects the mean, the median was preferred for imputation.
Outlier Analysis
Used the IQR method on two numeric columns.
Outliers were identified but not removed.
They will be handled in Part 2 using capping or robust scaling instead of deletion to avoid information loss.
Scatter Plot Interpretation
Positive trend indicates variables increase together.
Dense clustering suggests stronger correlation.
Wide spread indicates weaker relationship.

Assignment 2
Required Document:
Clean Dataset

Task to do:
Model traning

Encoding
Ordinal variables (Low < Medium < High) were encoded using integer mapping because the categories have a meaningful order.
Nominal variables were one-hot encoded using pd.get_dummies(drop_first=True) to avoid introducing false ordinal relationships and to reduce multicollinearity.
Data Leakage

The StandardScaler was fitted only on the training data and then applied to the test data. Fitting on the full dataset would leak information from the test set into the training process, leading to overly optimistic evaluation results.

Logistic Regression Regularization

The parameter C is the inverse of regularization strength.

Larger C → weaker regularization.
Smaller C → stronger regularization.

Performance of C = 1.0 and C = 0.01 was compared using Precision, Recall, and AUC.

Assignment 3
Required Document:
Clean Dataset

Task to do:

Random Forest

Controlled Decision Tree

max_depth limits the depth of the tree, reducing variance.
min_samples_split prevents splitting nodes with too few samples, reducing noise-driven splits.

The controlled tree typically has a smaller gap between training and test accuracy, indicating better generalization.

Gini vs Entropy

Gini Impurity

Gini=1−∑pi2Gini = 1 - \sum p_i^2Gini=1−∑pi2​

Entropy

Entropy=−∑pilog⁡2(pi)Entropy = -\sum p_i \log_2(p_i)Entropy=−∑pi​log2​(pi​)

A node with Gini = 0 contains samples from only one class and is therefore perfectly pure.

Random Forest

Feature importance is calculated from the average reduction in Gini impurity contributed by each feature across all trees.

Unlike linear regression coefficients, feature importance indicates how useful a feature is for splitting, not the direction or magnitude of its effect.
Bagging
Random Forest uses bootstrap sampling, meaning each tree is trained on a random sample of the training data with replacement. At each split, only a random subset of features is considered. Averaging many trees reduces variance and improves robustness compared with a single deep decision tree.
Feature Ablation

The five least important features were removed and a second Random Forest was trained.

If AUC remains similar or improves, those features were adding little information.
If AUC decreases noticeably, those features contributed useful predictive information.
A simpler model reduces inference cost and maintenance, provided predictive performance remains acceptable.

Cross Validation

Five-fold stratified cross-validation provides a more reliable estimate of generalization performance because every observation is used for both training and validation across different folds.
<img width="2240" height="1327" alt="image" src="https://github.com/user-attachments/assets/8c450c66-0049-4c03-bb33-ca1752783b5f" />


Assignment 4
Required Document:
Clean Dataset

Task to do:
Model traning

Temperature Comparison			
Input	Temp = 0	Temp = 0.7	Difference
Record 1	Stable JSON	Slight wording variation	0.7 more diverse
Record 2	Stable JSON	Different explanation	More variability
Record 3	Stable JSON	Different phrasing	Less deterministic
<img width="761" height="121" alt="image" src="https://github.com/user-attachments/assets/6019a611-ecb5-4c43-a416-fabbfa3a1768" />
