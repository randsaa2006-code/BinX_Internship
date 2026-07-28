# Week 2 — Math Foundations & EDA 🚀

## Overview

Week 2 of the **BinX Tech AI & Machine Learning Internship Program** marks the transition from Phase 1 (Python foundations) into Phase 2 — the mathematical foundations every machine learning model rests on.

During this week, I'm learning descriptive statistics, probability and distributions, and linear algebra, then applying all of it through a full Exploratory Data Analysis (EDA) on a real dataset.

The main focus is developing a complete statistics-to-EDA workflow:

**Descriptive Statistics → Probability → Linear Algebra → EDA (Univariate) → EDA (Bivariate & Correlation)**

All work is implemented using Jupyter Notebooks and managed through Git/GitHub.

---

## Week Objectives 🎯

By the end of Week 2, I will have learned how to:

- Compute and interpret mean, median, mode, variance, standard deviation, and IQR.
- Explain when each measure of central tendency and spread is appropriate.
- Apply core probability rules, including conditional probability and Bayes' theorem.
- Recognize common distributions: normal, binomial, uniform.
- Represent data as vectors and matrices, and understand the dot product and matrix multiplication.
- Connect these math foundations to how ML models represent data and make predictions.
- Perform a complete Exploratory Data Analysis: univariate and bivariate analysis, correlation, and outlier detection.
- Communicate findings through clear Seaborn visualizations and a written data-storytelling summary.

---

# Daily Progress 📅

## Day 1 — Descriptive Statistics 📊

### Topics Covered:

- Why descriptive statistics comes before modeling.
- Dataset exploration using Pandas (`df.info()`, `df.describe()`, `df.isnull().sum()`).
- Measures of central tendency:
  - Mean
  - Median
  - Mode
- Measures of spread:
  - Range
  - Variance
  - Standard deviation
  - Interquartile Range (IQR)
- Percentiles and quartiles (Q1, Q2, Q3).
- The effect of outliers on statistical measures.

### Practical Work:

- Loaded the Pima Indians Diabetes dataset (`diabetes.csv`, 768 patient records, 9 features) and inspected its structure, shape, and missing values.
- Noted that while there are no `NaN` values, columns like `Insulin` and `SkinThickness` contain zero values that likely represent missing or invalid measurements.
- Worked through a toy example (`[10, 12, 12, 13, 100]`) showing how a single outlier pulls the mean up while leaving the median almost unchanged.
- Calculated mean, median, mode, range, variance, standard deviation, and IQR for the **Glucose** feature.
- Computed Q1, Q2, and Q3, and combined all statistics into one summary table.
- Compared the mean (120.89) and median (117.00), identified a slight right-skew, and concluded the median better represents a typical glucose level since it's less affected by outliers.
- Visualized the distribution with a histogram and a box plot to confirm the findings visually.

### Tools Used:

Python • Jupyter Notebook • NumPy • Pandas • Matplotlib

---

## Day 2 — Probability & Distributions 🎲

### Topics Covered:

- Probability basics and core rules (complement, addition, multiplication).
- Conditional probability.
- Bayes' theorem.
- Common distributions: normal, binomial, uniform.

### Practical Work:

*Pending.*

### Tools Used:

NumPy • Matplotlib • Jupyter Notebook

---

## Day 3 — Linear Algebra for ML 🧮

### Topics Covered:

- Vectors and matrices as the data structures ML runs on.
- The dot product and how models use it to predict.
- Matrix multiplication and the shape-matching rule.

### Practical Work:

*Pending.*

### Tools Used:

NumPy • Jupyter Notebook

---

## Day 4 — EDA Part 1: Distributions & Outliers 📈

### Topics Covered:

- Why EDA is a required first step before modeling.
- Univariate analysis with Seaborn: histograms, box plots, count plots, KDE.
- Outlier detection using the IQR method.

### Practical Work:

*Pending.*

### Tools Used:

Seaborn • Pandas • Matplotlib • Jupyter Notebook

---

## Day 5 — EDA Part 2: Correlation & Data Storytelling 🔗

### Topics Covered:

- Bivariate analysis: scatter plots, grouped box plots.
- Correlation and the correlation heatmap.
- The pairplot for scanning relationships.
- Data storytelling and assembling the complete, narrated EDA notebook.

### Practical Work:

*Pending.*

### Tools Used:

Seaborn • Pandas • Matplotlib • Jupyter Notebook • Git & GitHub

---

# Summary 📌

During Week 2 of the AI & Machine Learning Internship Program, I started building the mathematical foundation that every ML model rests on.

I began with descriptive statistics, analyzing the Glucose feature from the Pima Indians Diabetes dataset. I learned how mean, median, and mode describe the center of data, while range, variance, standard deviation, and IQR describe its variability, and I saw firsthand how outliers pull the mean away from the median.

The rest of the week builds on this foundation with probability and Bayes' theorem, the linear algebra behind how models predict, and a full Exploratory Data Analysis combining everything into one narrated notebook.

*This README will be updated as each day is completed.*
