# Practical Assignment - Regression & Support Vector Regression (SVR)

**Machine Learning Course**

**Name:** Faiq Razzan Afifie

**Student ID:** 244107020214

## Lab Summary

### Lab: Medical Cost Prediction (Insurance Dataset)

* **Objective:** Implement, evaluate, and compare Multiple Linear Regression and Support Vector Regression (SVR) on tabular data to forecast individual medical charges.

* **Preprocessing & Feature Engineering:**

  * Categorical features (`sex`, `smoker`, `region`) were converted into numerical representations using `OneHotEncoder(drop='first')`.

  * Continuous numerical features (`age`, `bmi`, `children`) and target values (`charges`) were normalized using `StandardScaler` to facilitate stable optimization and hyperplane margin calculation for SVR.

* **Hyperparameter Tuning:** Conducted a 5-fold cross-validated grid search (`GridSearchCV`) across parameter spaces ($C$, $\gamma$, $\epsilon$) using an RBF kernel.

* **Key Findings:** Non-linear interactions (notably the combined effect of smoking status and elevated BMI) caused Support Vector Regression to substantially outperform Multiple Linear Regression across all primary evaluation metrics.

## Lab Assignment: Medical Cost Personal Datasets (`insurance.csv`)

### Assignment Objectives

1. Identify predictor variables (independent features) and the target variable (`charges`).

2. Partition the dataset into training and testing subsets using an 80:20 split ratio.

3. Perform necessary feature scaling and categorical encoding.

4. Construct and train a Multiple Linear Regression benchmark model using Scikit-Learn.

5. Construct and optimize a Support Vector Regression (SVR) model using hyperparameter tuning.

6. Evaluate model performances using $R^2$, Mean Absolute Error (MAE), Mean Squared Error (MSE), and Root Mean Squared Error (RMSE).

7. Analyze and interpret empirical results and architectural trade-offs.

### Analysis & Implementation Results

#### 1. Variable Identification

* **Target Variable (**$y$**):**

  * `charges`: Continuous numerical value representing individual medical costs billed by health insurance.

* **Independent Variables (**$X$**):**

  * `age`: Age of the primary beneficiary (discrete numerical).

  * `sex`: Contractor gender (`female`, `male`).

  * `bmi`: Body Mass Index ($kg/m^2$), measuring body mass relative to height (continuous numerical).

  * `children`: Number of dependents covered under the insurance plan (discrete numerical).

  * `smoker`: Smoking status of the insured (`yes`, `no`).

  * `region`: US residential geographical region (`northeast`, `southeast`, `southwest`, `northwest`).

#### 2. Preprocessing & Experimental Setup

* **Dataset Splitting:** 80% train split ($N = 1,070$) and 20% test split ($N = 268$) with fixed random seed (`random_state=42`).

* **Linear Regression Pipeline:** One-Hot Encoding on categorical attributes; raw numerical features passed through without standardization.

* **SVR Pipeline:**

  * Numerical feature vectors standard-scaled ($\mu = 0, \sigma = 1$).

  * Target output scaled via `StandardScaler` during fitting and inverted back to raw dollar units during prediction.

  * 5-Fold cross-validation grid search applied over:

    * `C`: $[10, 50, 100, 200]$

    * `gamma`: `['scale', 'auto', 0.1, 0.01]`

    * `epsilon`: $[0.05, 0.1, 0.2]$

  * **Optimal Parameters Found:** `kernel='rbf'`, `C=10`, `gamma=0.1`, `epsilon=0.1`.

#### 3. Model Evaluation & Comparison Results

| **Metric** | **Multiple Linear Regression** | **Support Vector Regression (Tuned RBF)** | **Relative Change** | 
| $R^2$ **Score** | 0.7836 | **0.8691** | $+8.55\%$ | 
| **Mean Absolute Error (MAE)** | \$4,181.19 | **\$2,386.83** | $-\$1,794.36$ | 
| **Mean Squared Error (MSE)** | 33,596,915.85 | **20,319,848.31** | $-39.52\%$ | 
| **Root Mean Squared Error (RMSE)** | \$5,796.28 | **\$4,507.75** | $-\$1,288.53$ | 

#### 4. Analytical Findings

1. **Linear vs. Non-Linear Modeling:**

   * Exploratory data distributions indicate clear non-linear interaction thresholds: non-smokers experience low charges regardless of BMI, whereas smokers with $\text{BMI} \ge 30$ experience sudden, non-linear surges in charges.

   * Multiple Linear Regression relies on strictly additive linear relationships and fails to capture this threshold without engineered interaction terms.

   * SVR with an RBF kernel projects the feature space into higher dimensions, capturing these non-linear thresholds and increasing $R^2$ from **0.7836** to **0.8691**.

2. **Error Margin Reduction:**

   * SVR reduces the Mean Absolute Error by **\$1,794.36** per prediction compared to Ordinary Least Squares, demonstrating higher generalization robustness across noisy and skewed target values.

3. **Impact of Scaling:**

   * SVR optimization depends directly on Euclidean distances and support vector margins. Applying standardization to both features and the target variable prevented numerical divergence and ensured balanced gradient convergence.
