# Day 4 — Exploratory Data Analysis (EDA) Part 1: Distributions & Outliers 📈

## Overview

This project focuses on Exploratory Data Analysis (EDA) — the process of examining and understanding a dataset before building any predictive model. Before training a model, it's essential to explore the dataset's structure, identify patterns, detect anomalies, and discover potential data quality issues.

In this notebook, the Pima Indians Diabetes dataset (`diabetes.csv`) is explored through univariate analysis, statistical visualization with Seaborn, and outlier detection using the Interquartile Range (IQR) method.

---

## Learning Objectives 🎯

By the end of this notebook, I learned how to:

- Explain the purpose of Exploratory Data Analysis (EDA) and why it should always be performed before modeling.
- Create statistical visualizations using Seaborn.
- Perform univariate analysis on numerical and categorical variables.
- Detect outliers using box plots and the IQR method.
- Interpret visualizations and summarize findings effectively.

---

## Topics Covered 📚

### 1. What Is EDA and Why It Matters

EDA is the process of examining a dataset before applying machine learning algorithms, combining descriptive statistics with visualizations to answer questions like: How are the values distributed? Are there missing values or unusual observations? Are the classes balanced? Skipping this step risks training a model on errors, missing values, or extreme observations that produce unreliable predictions.

### 2. Seaborn for Statistical Visualization

Seaborn is built on top of Matplotlib and specializes in statistical plots, offering simpler syntax and cleaner default styles while integrating directly with Pandas DataFrames.

### 3. Univariate Analysis

Examined each variable individually using:

| Plot | Purpose |
|------|---------|
| Histogram | Shows the distribution of numerical values |
| KDE Plot | Displays a smoothed estimate of the distribution |
| Box Plot | Detects spread and potential outliers |
| Count Plot | Shows the frequency of categorical values |

### 4. Outlier Detection with the IQR Method

A value is flagged as a potential outlier if it falls below Q1 - 1.5×IQR or above Q3 + 1.5×IQR. Outliers are never removed automatically — each one should be investigated to decide whether to keep, correct, cap, or remove it.

---

## Hands-On Lab 🧪

Performed a complete univariate EDA on the diabetes dataset:

### Step 1: Load and Explore the Dataset

Loaded `diabetes.csv` and inspected it with `df.head()`, `df.shape`, `df.info()`, and `df.describe()`.

### Step 2: Histogram Analysis

Plotted a histogram (with KDE overlay) for every numeric column to check for normality, skewness, and multiple peaks.

### Step 3: KDE Analysis

Plotted a KDE curve for every numeric column to get a smoother view of each distribution's shape.

### Step 4: Box Plot Analysis

Plotted a box plot for every numeric column to visually assess spread and flag potential outliers.

### Step 5: IQR Outlier Detection

Applied the IQR method to the **Insulin** column, calculated the lower/upper bounds, and extracted all rows falling outside them.

### Step 6: Count Plot Analysis

Plotted a count plot for the **Outcome** column to check for class imbalance.

---

## EDA Findings 📊

- Numerical variables showed different distribution shapes — some approximately normal, others skewed.
- Box plots highlighted several potential outliers.
- The IQR method confirmed observations outside the expected range for Insulin.
- The Outcome variable showed some class imbalance.

---

## Tools Used 🛠️

Python • Jupyter Notebook • Pandas • NumPy • Seaborn • Matplotlib

---

## Reflection

This notebook helped me understand the importance of Exploratory Data Analysis before building machine learning models. By examining distributions, identifying outliers, and analyzing categorical variables, I gained a clearer understanding of the dataset's characteristics and potential quality issues, and became more confident using Seaborn for statistical visualization and interpreting different plot types rather than simply creating them.

---

## Summary 📌

In this notebook, I performed a comprehensive univariate exploratory data analysis using Pandas, Seaborn, and Matplotlib — exploring numerical and categorical variables through histograms, KDE plots, box plots, and count plots, then applying the IQR method to detect potential outliers. EDA is a fundamental step in every data science project because it helps uncover data quality issues, understand feature distributions, and support informed modeling decisions, providing a strong foundation for the multivariate analysis and machine learning techniques covered in the following weeks.
