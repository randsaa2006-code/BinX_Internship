# Day 5 — Exploratory Data Analysis (EDA) Part 2: Correlation & Data Storytelling 📈

## Overview

This notebook introduces bivariate exploratory data analysis, correlation analysis, and data storytelling. After exploring each variable individually in Day 4, the next step is to study how variables relate to one another — understanding these interactions is essential before training machine learning models, since predictive models learn patterns from relationships between variables, not from individual variables in isolation.

In this notebook, the Pima Indians Diabetes dataset (`diabetes.csv`) is explored through scatter plots, grouped box plots, a correlation matrix and heatmap, a pairplot, and a full data-storytelling summary.

---

## Learning Objectives 🎯

By the end of this notebook, I learned how to:

- Explain the purpose of bivariate analysis.
- Create scatter plots and grouped box plots using Seaborn.
- Compute and interpret correlation coefficients.
- Visualize correlations using a heatmap.
- Explain why correlation does not imply causation.
- Explore relationships using pair plots.
- Present analytical findings through data storytelling.

---

## Topics Covered 📚

### 1. Bivariate Analysis

Examining the relationship between two variables. Depending on the variable types, different visualizations are used:

- Numerical vs Numerical → Scatter Plot
- Numerical vs Categorical → Grouped Box Plot

### 2. Scatter Plot

Visualizes the relationship between two numerical variables — each point represents one observation, revealing trends, clusters, or unusual observations.

### 3. Grouped Box Plot

Compares the distribution of a numerical variable across categories, highlighting differences in medians, variability, and outliers between groups.

### 4. Correlation

Measures the strength and direction of the linear relationship between two numerical variables, ranging from -1 to +1:

| Correlation Value | Interpretation |
|---|---|
| +1 | Perfect positive correlation |
| +0.7 to +0.99 | Strong positive correlation |
| +0.3 to +0.69 | Moderate positive correlation |
| 0 | No linear correlation |
| -0.3 to -0.69 | Moderate negative correlation |
| -0.7 to -0.99 | Strong negative correlation |
| -1 | Perfect negative correlation |

### 5. Correlation Heatmap

A color-coded visualization of the correlation matrix that makes strong positive and negative relationships easy to spot at a glance.

### 6. Correlation Does Not Imply Causation

A strong correlation between two variables doesn't mean one causes the other — the relationship may come from coincidence or a hidden third factor (e.g. ice cream sales and drowning incidents both rising because of hot weather, not because of each other).

### 7. Pairplot

Displays scatter plots for every pair of numerical variables plus each variable's distribution on the diagonal, giving a quick overview of the dataset's relationships, clusters, and outliers in one figure.

### 8. Data Storytelling

Turning analysis into a narrative with four components: Context, Findings, Interpretation, and Recommendation — because visualizations alone provide limited value without explaining what they mean and why it matters.

---

## Hands-On Lab 🧪

- Loaded `diabetes.csv` and produced a scatter plot of Glucose vs BMI.
- Produced a grouped box plot of Glucose by Outcome to compare diabetic vs non-diabetic patients.
- Computed the full correlation matrix with `df.corr(numeric_only=True)`.
- Visualized the correlation matrix as an annotated heatmap.
- Produced a pairplot of the full dataset colored by Outcome.
- Wrote interpretation, Machine Learning Connection, and Key Takeaways sections after each visualization.

---

## Key Findings 📊

- Glucose shows the clearest separation between diabetic and non-diabetic patients in the grouped box plot.
- The correlation heatmap and matrix reveal which features move together most strongly.
- The pairplot shows some visible separation between Outcome classes across several feature pairs.
- Example data story: glucose level has the strongest positive relationship with diabetes outcome, and patients with higher glucose values were more likely to belong to the diabetic class; BMI showed a moderate relationship, while other variables were only weakly correlated — suggesting glucose and BMI may be valuable predictors in future models.

---

## Tools Used 🛠️

Python • Jupyter Notebook • Pandas • NumPy • Seaborn • Matplotlib

---

## Reflection

In this notebook, I learned how to explore relationships between variables using bivariate analysis techniques such as scatter plots, grouped box plots, correlation matrices, heatmaps, and pairplots. I also realized that creating visualizations is only one part of data analysis — interpreting the results and communicating insights through data storytelling are equally important. These techniques provide valuable information that supports feature selection, preprocessing, and the development of reliable machine learning models.

---

## Conclusion

This notebook introduced the fundamental concepts of bivariate exploratory data analysis and correlation analysis. Using Seaborn visualizations and correlation techniques, I explored relationships between variables, identified meaningful patterns, and learned how to communicate analytical findings through data storytelling. These skills complete the theoretical foundation of exploratory data analysis and prepare me to build a comprehensive EDA notebook that combines descriptive statistics, univariate analysis, outlier detection, bivariate analysis, and correlation analysis before moving to machine learning modeling.
