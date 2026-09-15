# Jobsheet 3 - Feature Extraction
**Machine Learning Course**

* **Name**: Faiq Razzan Afifie
* **Student ID**: 244107020214

---

## Lab Summary

### Lab 1: Feature Extraction in Tabular Data (Titanic Dataset)
* **Objective**: Extract, construct, select features, and evaluate performance using Scikit-Learn pipelines.
* **Preprocessing & Extraction**:
  * Imputed missing values using `SimpleImputer` (median for numerical features, most frequent for categorical features).
  * Encoded categorical attributes (`Pclass`, `Sex`, `Embarked`) using `OneHotEncoder`.
  * Scaled numerical variables using `StandardScaler`.
* **Feature Construction**: Created a composite feature `FamilySize = SibSp + Parch + 1`.
* **Feature Selection**: Applied univariate feature selection via `SelectKBest(score_func=f_classif, k=5)` using ANOVA F-value.
* **Modeling & Evaluation**: Built an end-to-end `Pipeline` with `LogisticRegression`. Key discriminative features identified included `Sex_female`, `Sex_male`, `Pclass_3`, `Pclass_1`, and `Fare`, achieving approximately 78% accuracy.

### Lab 2: Overview of TF-IDF Feature Extraction (Text Data)
* **Objective**: Transform unstructured text documents into structured numerical term-frequency vectors.
* **Method**: Employed `TfidfVectorizer(stop_words='english')` across an exemplar multi-sentence corpus.
* **Output**: Generated sparse matrix representations where document rows correspond to token index weights, effectively extracting distinctive vocabulary tokens while filtering out common English stopwords.

### Lab 3: Feature Extraction in Image Data
* **Objective**: Perform basic feature extraction on image data using image color space properties.
* **Method**: Utilized `Pillow` (`PIL.Image`) to load benchmark images, split color channels into Red, Green, and Blue (RGB), and extracted channel-level pixel distribution histograms (256 bins per channel) as feature vectors.

---

## Lab Assignment: Wisconsin Breast Cancer (WBC)

### Assignment Objectives
1. Differentiate between usable and non-usable variables.
2. Encode the target column (`diagnosis`).
3. Standardize all numerical feature columns.
4. Perform feature selection using `SelectKBest`.
5. Evaluate model performance using `LogisticRegression` within an end-to-end `Pipeline`.
6. Determine the optimal number of features ($k$) and identify which features are selected.

---

### Analysis & Implementation Results

#### 1. Usable vs. Non-Usable Variables
* **Non-usable Variables**:
  * `id`: Unique identifier carrying no diagnostic value.
  * `Unnamed: 32`: Empty trailing artifact column containing 100% missing values (`NaN`).
* **Usable Variables**: All 30 continuous numerical cell-nuclei measurements (`radius_mean`, `texture_mean`, ..., `fractal_dimension_worst`) and the target variable `diagnosis`.

#### 2. Target Encoding & Standardization
* The target column `diagnosis` was converted into binary numerical labels using `LabelEncoder`:
  * `B` (Benign) $\rightarrow$ `0`
  * `M` (Malignant) $\rightarrow$ `1`
* All 30 usable numerical predictor columns were scaled to zero mean and unit variance using `StandardScaler`.

#### 3. Optimal Features ($k$) & Evaluation
* A 5-fold cross-validation grid search over $k \in [1, 30]$ inside a `Pipeline` (`StandardScaler` $\rightarrow$ `SelectKBest(f_classif)` $\rightarrow$ `LogisticRegression`) determined that **19 features** yield the optimal validation performance.
* **Cross-Validation Accuracy**: **97.36%**
* **Test Set Accuracy (80:20 Stratified Split)**: **98.25%**

#### 4. Top 19 Selected Features (Ranked by ANOVA F-Score)
| Rank | Feature Name | ANOVA F-Score |
| :---: | :--- | :---: |
| 1 | `concave points_worst` | 733.72 |
| 2 | `perimeter_worst` | 717.25 |
| 3 | `radius_worst` | 692.86 |
| 4 | `concave points_mean` | 684.53 |
| 5 | `perimeter_mean` | 548.41 |
| 6 | `area_worst` | 522.19 |
| 7 | `radius_mean` | 511.27 |
| 8 | `area_mean` | 444.86 |
| 9 | `concavity_mean` | 397.59 |
| 10 | `concavity_worst` | 319.51 |
| 11 | `compactness_mean` | 263.56 |
| 12 | `compactness_worst` | 238.20 |
| 13 | `radius_se` | 205.43 |
| 14 | `perimeter_se` | 193.17 |
| 15 | `area_se` | 180.56 |
| 16 | `texture_worst` | 126.12 |
| 17 | `smoothness_worst` | 103.72 |
| 18 | `symmetry_worst` | 100.56 |
| 19 | `texture_mean` | 93.48 |
