# Jobsheet 2 - Machine Learning

**Name:** Faiq Razzan Afifie  
**Student ID:** 244107020214  

---

### Lab Summary

* **Lab 1:** Checked data structure (`shape`, `info`, `describe`), missing values, and distribution plots (histograms, boxplots, correlation heatmap).
* **Lab 2:** Handled missing data on the Titanic dataset (mean imputation for `Age`, `"DECK"` string for `Cabin`, and mode for `Embarked`).
* **Lab 3:** Feature selection, label encoding on categorical variables (`Sex`, `Cabin`), and standardization on `Age` using `StandardScaler`.
* **Lab 4:** Basic image preprocessing with OpenCV (reading BGR to RGB, resizing to 128x128, and converting to grayscale).

---

### Assignment: Wisconsin Breast Cancer (WBC)

1. **Feature Selection:** Dropped `id` (identifier only) and `Unnamed: 32` (all NaN values). Kept the remaining 30 numerical features and the target column.
2. **Encoding:** Transformed the `diagnosis` column using `LabelEncoder` (`B` to 0, `M` to 1).
3. **Standardization:** Scaled all 30 numerical features using `StandardScaler` so that each has a mean of 0 and a standard deviation of 1.
