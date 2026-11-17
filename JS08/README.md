# Practical Assignment - Hierarchical Clustering (JS08)

**Name:** Faiq Razzan Afifie | **ID:** 244107020214

This folder contains practical assignments and laboratory exercises for **Job Sheet 08: Hierarchical Clustering** in the Machine Learning course.

## Overview of Practice

This assignment focuses on implementing Hierarchical Clustering algorithms to group data without predefined labels using bottom-up (agglomerative) approaches. Preprocessing involved handling dataset features and computing distance matrices to analyze how data points merge hierarchically.

Key tasks included constructing dendrograms to determine optimal cluster counts and evaluating clustering performance using the Silhouette Coefficient.

## File Structure & Summary

| No. | File Name | Description |
| :--- | :--- | :--- |
| 1 | `JS08_01.ipynb` | Introduction and implementation of Agglomerative Hierarchical Clustering using `scikit-learn` and `scipy`. |
| 2 | `JS08_02.ipynb` | Further practice and experimentation on hierarchical clustering workflows. |
| 3 | `JS08_03.ipynb` | Advanced analysis and visualization of clusters across multiple dimensions. |
| 4 | `JS08_Assignment01.ipynb` | Practical assignment focusing on dataset application and dendrogram interpretation. |
| 5 | `JS08_Assignment02.ipynb` | Advanced practical assignment featuring custom linkage criteria and performance evaluation. |

## Key Topics Covered

* **Dendrogram Construction:** Utilizing `scipy.cluster.hierarchy` with Ward’s linkage method to visualize cluster merges and choose optimal cutoff thresholds.
* **Agglomerative Clustering:** Building bottom-up hierarchical clustering models with `sklearn.cluster.AgglomerativeClustering`.
* **Cluster Visualization:** Plotting cluster distributions using scatter plots across feature dimensions.
* **Model Evaluation:** Assessing cluster separation and quality using the **Silhouette Coefficient**.
