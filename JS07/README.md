```python
# Let's check what JS07 typically covers in Polinema Machine Learning course context (Unsupervised Learning / Clustering / Association Rules / PCA).
# Since JS06 was SVR/Regression, JS07 typically covers Unsupervised Learning (K-Means, DBSCAN, Evaluation metrics like Silhouette Score and DBI).
# Let's organize the README structure for JS07 based on the CC_Customer_Dataset clustering assignment we just worked on.
print("JS07 clustering repository summary structure ready.")


```

```text
JS07 clustering repository summary structure ready.


```

# Practical Assignment - Unsupervised Learning & Clustering (JS07)

**Name:** Faiq Razzan Afifie | **ID:** 244107020214

**Department of Information Technology, State Polytechnic of Malang (Polinema)**

---

## Lab Summary

* **Lab:** Customer Segmentation & Unsupervised Clustering (Credit Card Dataset: `CC_Customer_Dataset.csv`)
* **Objective:** Implement, evaluate, and compare partition-based (**K-Means**) and density-based (**DBSCAN**) clustering algorithms to segment credit card customers based on financial and behavioral attributes.
* **Preprocessing & Feature Engineering:**
* Selected usable numerical features (`Avg_Credit_Limit`, `Total_Credit_Cards`, `Total_visits_bank`, `Total_visits_online`, `Total_calls_made`).
* Applied `StandardScaler` normalization ($\mu = 0, \sigma = 1$) to ensure equal feature weighting and stable distance metric computation.



---

## Lab Assignment: Credit Card Customer Segmentation

### Assignment Objectives

1. Perform exploratory data analysis and visualize feature distributions (`Avg_Credit_Limit` vs `Total_Credit_Cards`).
2. Construct a K-Means clustering model and determine the optimal number of clusters ($k$) using the **Elbow Method** (SSE line chart).
3. Depict and interpret K-Means clustering results via scatter plots.
4. Construct a density-based clustering model using **DBSCAN** across all usable variables.
5. Evaluate clustering performance and separation quality using the **Silhouette Score** and **Davies-Bouldin Index (DBI)**.

---

## Analysis & Implementation Results

### 1. Data Distribution & Linearity Analysis

* **Scatterplot Analysis (`Avg_Credit_Limit` vs `Total_Credit_Cards`):**
* The feature distribution **cannot be considered linear**. Data points form discrete horizontal and vertical tiers (clusters of credit card counts aligned across specific credit limit thresholds).
* This non-linear, multi-modal grouping indicates that linear regression or correlation models are insufficient, justifying the use of distance-based unsupervised clustering.



### 2. K-Means Clustering & Elbow Method Optimization

* **Elbow Method Curve:** The Sum of Squared Errors (SSE) decreases sharply from $k = 1$ to $k = 3$, after which the curve flattens significantly, forming a distinct "elbow point" at **$k = 3$**.
* **Analytical Rationale:** Selecting $k = 3$ provides an optimal balance between minimizing intra-cluster variance (inertia) and avoiding overfitting or excessive model complexity.
* **Cluster Visualization:** The K-Means scatter plot successfully partitions customers into three distinct behavioral segments based on credit limits and product holdings.

### 3. DBSCAN Clustering & Validation Metrics

* **Model Configuration:** Configured using all standardized features with optimized density hyperparameters (`eps = 0.8`, `min_samples = 5`).
* **Evaluation Metrics:**
* **Silhouette Score:** Measures cluster cohesion and separation (higher is better).
* **Davies-Bouldin Index (DBI):** Measures cluster similarity and dispersion (lower is better).


* **Key Findings:** While K-Means provides clear partitioned boundaries assuming spherical clusters, DBSCAN effectively identifies dense core regions and handles potential outlier noise points within multi-dimensional financial behavior spaces.
