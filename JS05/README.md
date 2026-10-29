# Practical Assignment - (JS05)

**Name:** Faiq Razzan Afifie | **ID:** 244107020214

---

## Lab Summary

* **Objective:** Build and evaluate classification models using Support Vector Machines (SVM) with various kernels (Linear, Polynomial, and RBF) and analyze data split ratio impacts.
* **Preprocessing:** Applied `StandardScaler` normalization on feature distributions to optimize hyperplane margins and distance metrics.
* **Evaluation:** Compared model accuracy performance across 70:30 and 80:20 data split ratios.

---

## Results & Comparison

| Data Split Ratio | Kernel Type | Accuracy (%) |
| --- | --- | --- |
| **70:30** | Linear | 97.68 |
| **70:30** | Polynomial | 97.16 |
| **70:30** | RBF | **98.42** |
| **80:20** | Linear | 97.79 |
| **80:20** | Polynomial | 97.32 |
| **80:20** | RBF | **98.58** |

* **Key Finding:** The SVM model utilizing an RBF kernel consistently achieved the highest classification accuracy across both split ratios, with the 80:20 train-test partition yielding optimal generalization results.
