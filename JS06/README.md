Practical Assignment - Support Vector Regression (JS06)

Name: Faiq Razzan Afifie | ID: 244107020214
Lab Summary

    Objective: Predict medical charges (insurance.csv) using Multiple Linear Regression vs. Support Vector Regression (SVR).

    Preprocessing: One-Hot Encoding for categorical features (sex, smoker, region); StandardScaler normalization for continuous features and target variable.

    Hyperparameter Tuning: 5-fold GridSearchCV on an RBF kernel (C, gamma, epsilon).

Results & Comparison
Metric	Multiple Linear Regression	Tuned SVR (RBF)
R2 Score	0.7836	0.8691
MAE	$4,181.19	$2,386.83
RMSE	$5,796.28	$4,507.75

    Key Finding: SVR with an RBF kernel significantly outperformed Linear Regression by effectively capturing non-linear interactions (e.g., sudden medical cost surges for smokers with BMI≥30).
