# Machine Learning Internship — Task 1: Data Cleaning & Preprocessing

## 📌 Project Overview
This repository contains the implementation of **Task 1: Data Cleaning & Preprocessing**, a foundational step in building robust Machine Learning pipelines. Raw datasets often contain noise, missing entries, disparate scales, and outliers that can severely degrade model performance. This project demonstrates systematic methodologies to transform raw data into a clean, model-ready format using the classic **Titanic Dataset**.

---

## 🛠️ Tech Stack & Tools Used
- **Language:** Python 3.x
- **Data Manipulation:** `pandas`, `numpy`
- **Data Visualization:** `matplotlib`, `seaborn`
- **Feature Engineering:** `scikit-learn` (StandardScaler)
- **Environment:** Google Colab / Jupyter Notebooks

---

## 🚀 Preprocessing Pipeline & Implementation Details

### 1. Data Exploration (`EDA`)
- Inspected structural integrity using `df.info()` and mapped missing value distributions with `df.isnull().sum()`.
- Identified critical gaps in features such as `age` and `embarked`.

### 2. Strategic Imputation (Handling Missing Values)
- **Continuous Features:** Filled missing values in the `age` column using the **median** rather than the mean, ensuring robustness against skewness and extreme values.
- **Categorical Features:** Imputed missing entries in the `embarked` column with the **mode** (most frequent occurrence).
- **Dimensionality Reduction:** Dropped high-sparsity structural features (e.g., `deck`) and redundant structural copies to minimize noise.

### 3. Categorical Feature Encoding
- Transformed binary text variables (like `sex`) into exact mathematical indicators (`0` and `1`).
- Implemented **One-Hot Encoding** using `pd.get_dummies()` for multi-class nominal variables (`embarked`, `class`) to eliminate implicit ordinal bias during future model training.

### 4. Outlier Detection & Mitigation
- Automated outlier detection using the **Interquartile Range (IQR)** method.
- Established rigorous operational boundaries:
  $$\text{Lower Bound} = Q_1 - 1.5 \times \text{IQR}$$
  $$\text{Upper Bound} = Q_3 + 1.5 \times \text{IQR}$$
- Trimmed extreme anomalies within the variance-heavy `fare` feature to prevent gradient distortion during convergence.

### 5. Feature Scaling & Normalization
- Applied **Z-score Standardization** via `StandardScaler` to bring numeric features (`age`, `fare`) onto a uniform scale with a mean ($\mu$) of `0` and standard deviation ($\sigma$) of `1`. This steps prevents distance-based algorithms from favoring large-magnitude dimensions arbitrarily.

---

## 📊 Key Takeaways & Learnings
- **Garbage In, Garbage Out:** A machine learning model is only as definitive as the data fed into it. 
- **Statistical Integrity:** Choosing median over mean protects data semantics from heavy-tailed skews.
- **Scale Uniformity:** Normalization is essential for ensuring fast, optimal convergence across gradient descent variants.

---
*Maintained as part of the Machine Learning Internship Engineering Log.*
