# Week 2 — Complete Exploratory Data Analysis (EDA) Notebook 📊

## Overview

This notebook combines every concept covered throughout Week 2 into one complete Exploratory Data Analysis project on the **Pima Indians Diabetes dataset** (`diabetes.csv`). The analysis includes descriptive statistics, univariate analysis, outlier detection, bivariate analysis, correlation analysis, and data storytelling.

The dataset contains medical information collected from female patients, with the objective of predicting whether a patient has diabetes based on diagnostic measurements such as glucose level, BMI, age, insulin level, and blood pressure.

---

## Learning Objectives 🎯

By completing this notebook, I learned how to:

- Load and inspect a real-world dataset.
- Perform descriptive statistical analysis.
- Explore numerical and categorical variables.
- Detect missing values and outliers.
- Perform univariate and bivariate analysis.
- Compute and visualize correlations.
- Summarize analytical findings through data storytelling.

---

## Structure

### 1. Dataset Overview

Loaded the dataset and inspected it with `head()`, `shape`, `columns`, `dtypes`, `info()`, and `describe()`.

### 2. Missing Values & Duplicates

Checked for missing values with `isnull().sum()` and duplicate rows with `duplicated().sum()`.

### 3. Descriptive Statistics

Computed mean, median, standard deviation, variance, and quartiles for all numeric features, each with a short interpretation of what it reveals.

### 4. Univariate Analysis

- Histogram (with KDE overlay) of Glucose
- KDE plot of Glucose
- Box plot of Insulin
- Count plot of Outcome

### 5. Outlier Detection

Applied the IQR method to the Insulin column, computed the lower/upper bounds, and extracted the outlier rows.

### 6. Bivariate Analysis

- Scatter plot: Glucose vs BMI (colored by Outcome)
- Grouped box plot: Glucose by Outcome

### 7. Correlation Analysis

- Full correlation matrix (`df.corr(numeric_only=True)`)
- Annotated correlation heatmap
- Correlation ≠ causation discussion

### 8. Pairplot

Full pairplot of the dataset colored by Outcome, to scan relationships and class separation across all numeric features at once.

### 9. EDA Findings

### 10. Data Storytelling

### 11. Reflection & Conclusion

### 12. GitHub Submission

---

## Key Findings 📌

- **Glucose is the strongest predictor** — it shows one of the strongest positive relationships with diabetes outcome, and patients with higher glucose levels are more likely to be diagnosed with diabetes.
- **BMI has a moderate relationship** with diabetes, though less distinct than glucose.
- **Insulin contains many outliers**, flagged by both the box plot and the IQR method, and should be investigated before deciding whether they're errors or genuine medical cases.
- **Most numerical variables are not perfectly normal** — several show skewed distributions.
- **Outcome classes are moderately imbalanced**, with slightly more non-diabetic than diabetic patients — worth considering during model evaluation.

---

## Data Storytelling 📖

The Pima Indians Diabetes dataset contains medical measurements collected from female patients to predict the presence of diabetes. The analysis began with descriptive statistics to understand the dataset's overall characteristics, then univariate analysis revealed the distribution of individual variables and highlighted potential outliers, particularly in Insulin. Bivariate analysis showed that glucose level has a noticeable relationship with diabetes outcome, while BMI also demonstrated a moderate association, and correlation analysis confirmed Glucose as one of the variables most strongly associated with the target. Overall, Glucose, BMI, and Age may provide valuable information for future predictive models, and these insights establish a strong foundation for feature selection, preprocessing, and machine learning model development.

---

## Tools Used 🛠️

Python • Jupyter Notebook • Pandas • NumPy • Seaborn • Matplotlib • Git & GitHub

---

## Reflection

This project strengthened my understanding of exploratory data analysis by combining statistical summaries with data visualization techniques. I learned that effective EDA is more than generating plots — it requires interpreting patterns, identifying potential issues, and communicating findings clearly. Working with a real-world dataset improved my ability to analyze data systematically and prepared me for the next stage of building machine learning models.

---

## Conclusion

This notebook presented a complete exploratory data analysis of the Pima Indians Diabetes dataset, combining descriptive statistics, univariate analysis, outlier detection, bivariate analysis, correlation analysis, and data storytelling to better understand the dataset before modeling. Performing EDA before machine learning is essential because it helps identify data quality issues, understand feature relationships, and make informed decisions during preprocessing and feature selection. The insights gained from this analysis provide a solid foundation for developing reliable and interpretable machine learning models, closing out Week 2 of the internship.

---

## GitHub Submission 🚀

The completed EDA notebook was committed and pushed to GitHub with a descriptive commit message. This notebook serves as the final Week 2 Hands-On Lab and demonstrates a complete exploratory data analysis workflow on a real-world dataset.
