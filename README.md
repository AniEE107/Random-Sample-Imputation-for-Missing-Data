# Random-Sample-Imputation-for-Missing-Data
This Jupyter Notebook demonstrates Random Sample Imputation for numerical missing data. Using a Titanic dataset, it shows how to replace missing values by sampling from existing non-missing data, and then analyzes the impact on feature distributions and variance.

#  Overview & Purpose
This Jupyter Notebook explores Random Sample Imputation, a method for handling missing data in numerical features. Unlike mean/median imputation which can distort the original distribution, random sample imputation replaces missing values with a random observation from the existing non-missing values of that feature. This technique aims to preserve the variability and statistical properties of the original data, making it a potentially more robust imputation strategy, especially when data is missing at random.

# This project uses a "titanic_toy (missing_Age_Fare).csv" dataset to demonstrate:
Identification of Missing Data: How to detect and quantify missing values in a DataFrame.
Application of Random Sample Imputation: Practical implementation of replacing missing numerical values by randomly sampling from the observed values.
Impact Analysis: Visualizing and comparing the distribution, variance, and covariance of the imputed data with the original data.

#  Key Concepts & Functionality
The notebook covers the following aspects of random sample imputation:

Data Loading and Initial Inspection:

Loads a CSV file (titanic_toy (missing_Age_Fare).csv), specifically selecting Age, Fare, and Survived columns.
Displays the head of the DataFrame to show initial data.
Calculates the percentage of missing values for each column using df.isnull().mean()*100.
Data Splitting: Splits the data into training and testing sets using train_test_split to ensure proper evaluation of the imputation strategy.
# Manual Random Sample Imputation:
Creates a new column (Age_imputed) to store the imputed 'Age' values.
For the missing values in Age_imputed, it randomly samples from the non-missing values of the original 'Age' column (X_train['Age'].dropna().sample(...)). The replace=True argument allows for sampling with replacement, which is crucial if the number of missing values is large.
Applies the same logic to the test set, ensuring that the random samples are drawn from the training set's non-missing values to avoid data leakage.
# Post-Imputation Analysis:
Verifies that no missing values remain in the Age_imputed column.
Distribution Comparison (KDE Plots): Uses seaborn.distplot (or seaborn.kdeplot for modern Seaborn versions) to plot the Kernel Density Estimate of the original 'Age' distribution against the 'Age_imputed' distribution. This is a key step to visually assess if the imputation preserved the original distribution shape.
Variance Comparison: Calculates and prints the variance of the original 'Age' and the imputed 'Age_imputed' to numerically check the impact on data spread. Random sample imputation aims to preserve variance better than mean/median imputation.
Covariance Analysis: Computes the covariance matrix for 'Fare', 'Age', and 'Age_imputed' to observe how the relationships between features are affected by the imputation.
Box Plots: Uses boxplot() to visually compare the distributions of 'Age' and 'Age_imputed', providing another perspective on how the imputation affects the data spread and outliers.
Random Seed for Reproducibility: Notes the use of random_state in sample() for reproducibility of the random imputation process.

#  Technologies Used
Python
Pandas (for data manipulation)
NumPy (for numerical operations)
Matplotlib (for plotting)
Seaborn (for enhanced data visualization, specifically KDE plots and box plots)
Scikit-learn (train_test_split)
Jupyter Notebook
