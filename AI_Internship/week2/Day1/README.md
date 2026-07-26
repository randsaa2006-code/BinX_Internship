# Day 1 — Descriptive Statistics 📊

## Overview

This project focuses on understanding how to analyze and describe datasets statistically before applying Artificial Intelligence and Machine Learning algorithms.

The goal is to learn how to explore data, understand its center and spread, detect unusual observations, and interpret data distribution before building predictive models.

Descriptive statistics is an essential step in Data Science workflows because it provides a clear understanding of dataset behavior before applying any Machine Learning techniques.

In this notebook, the Pima Indians Diabetes dataset was analyzed. The dataset contains 768 patient records with 9 medical features. The analysis mainly focuses on the Glucose feature because of its importance in diabetes prediction.

---

## Learning Objectives 🎯

By the end of this notebook, I learned how to:

- Understand the importance of descriptive statistics before modeling.
- Explore datasets using Pandas.
- Inspect dataset structure and statistical summaries.
- Calculate measures of central tendency:
  - Mean
  - Median
  - Mode
- Calculate measures of spread:
  - Range
  - Variance
  - Standard deviation
  - Interquartile Range (IQR)
- Understand quartiles and percentiles.
- Analyze the effect of outliers.
- Visualize data distributions using histograms and box plots.
- Interpret statistical results before Machine Learning modeling.

---

## Topics Covered 📚

### 1. Why Descriptive Statistics Matters

Learned why descriptive statistics is an important first step before building Machine Learning models.

Descriptive statistics helps answer important questions:

- What is the typical value of the dataset?
- How much variation exists in the data?
- Are there unusual observations?
- Is the data symmetric or skewed?

Understanding these characteristics helps in data preparation and selecting suitable techniques before training models.

### 2. Dataset Exploration Using Pandas

Learned how to inspect and understand a dataset before performing analysis.

Used the Pima Indians Diabetes dataset, which contains:

- 768 patient records
- 9 medical measurement features

Loaded the dataset into a Pandas DataFrame and explored its structure.

Used:

```python
df.info()
```

to check:

- Number of rows and columns
- Data types
- Missing values

Used:

```python
df.describe()
```

to generate statistical summaries including:

- Mean
- Standard deviation
- Minimum and maximum values
- Quartiles

Checked missing values using:

```python
df.isnull().sum()
```

The dataset does not contain `NaN` values, but some columns such as `Insulin` and `SkinThickness` contain zero values that may represent missing or invalid measurements.

The analysis focused on the Glucose feature.

### 3. Measures of Central Tendency

Learned how to describe the center or typical value of a dataset.

**Mean**

```python
mean = df["Glucose"].mean()
```

The mean represents the average value of all observations. It is calculated by adding all values and dividing by the number of observations. The mean is useful for understanding the general level of data but can be affected by extreme values.

**Median**

```python
median = df["Glucose"].median()
```

The median represents the middle value after sorting the data. It divides the dataset into two equal parts. The median is less affected by outliers, making it a better measure for skewed distributions.

**Mode**

```python
mode = df["Glucose"].mode()
```

The mode represents the most frequently occurring value in a dataset. It helps identify the most common observation.

### 4. Measures of Spread

Learned how to describe how data values are distributed and how much variation exists in the dataset.

Measures of spread help understand whether values are close together or widely scattered.

Key measurements:

- Range
- Variance
- Standard deviation
- Interquartile Range (IQR)

**Range**

The range represents the difference between the maximum and minimum values.

Formula: `Range = Maximum - Minimum`

It provides a simple overview of the total spread of the data.

```python
data_range = df["Glucose"].max() - df["Glucose"].min()
```

**Variance**

Variance measures how far data points are distributed from the mean. A higher variance indicates that values are more spread out, while a lower variance means values are closer to the mean.

```python
variance = df["Glucose"].var()
```

**Standard Deviation**

Standard deviation measures the average distance between data values and the mean. It is one of the most commonly used measurements to understand data variability.

```python
std = df["Glucose"].std()
```

**Interquartile Range (IQR)**

The Interquartile Range measures the spread of the middle 50% of the dataset.

Formula: `IQR = Q3 - Q1`

Where:
- Q1 represents the 25th percentile
- Q3 represents the 75th percentile

IQR is useful for detecting outliers because it focuses on the central part of the data.

```python
Q1 = df["Glucose"].quantile(0.25)
Q3 = df["Glucose"].quantile(0.75)
IQR = Q3 - Q1
```

### 5. Percentiles and Quartiles

Learned how data can be divided into sections using percentiles.

The main quartiles are:

- Q1: 25th percentile
- Q2: 50th percentile (Median)
- Q3: 75th percentile

Quartiles help understand:

- Data distribution
- The location of most observations
- Possible unusual values

Calculated quartiles using:

```python
df["Glucose"].quantile()
```

### 6. Effect of Outliers on Statistics

Learned how extreme values can influence statistical measurements.

Used the example:

```python
[10, 12, 12, 13, 100]
```

The value 100 increased the mean significantly because the mean uses all values in the calculation. However, the median remained almost unchanged because it depends on the middle position of sorted values.

This demonstrated that:

- Mean is sensitive to outliers.
- Median is more resistant to extreme values.

Understanding outliers is important because they can affect Machine Learning models and predictions.

---

## Hands-On Lab 🧪

### Step 1: Load and Inspect the Dataset

Loaded the Pima Indians Diabetes dataset using Pandas.

Performed initial exploration by checking:

- Dataset shape
- Column information
- Missing values
- Statistical summaries

```python
df.shape
df.info()
df.describe()
```

### Step 2: Calculate Central Tendency

Calculated the main measures of central tendency for the Glucose feature.

```python
mean = df["Glucose"].mean()
median = df["Glucose"].median()
mode = df["Glucose"].mode()
```

Compared these values to understand the typical glucose level.

### Step 3: Calculate Measures of Spread

Calculated different measurements to describe data variability.

```python
data_range = df["Glucose"].max() - df["Glucose"].min()
variance = df["Glucose"].var()
std = df["Glucose"].std()
```

Calculated IQR:

```python
Q1 = df["Glucose"].quantile(0.25)
Q3 = df["Glucose"].quantile(0.75)
IQR = Q3 - Q1
```

### Step 4: Create a Statistical Summary Table

Combined all calculated statistics into one summary table.

The table included:

- Mean
- Median
- Mode
- Range
- Variance
- Standard deviation
- Q1
- Q2
- Q3
- IQR

This table provided a complete statistical overview of the Glucose feature and helped compare different measurements together.

### Step 5: Data Visualization

Created visualizations to support and confirm the statistical analysis.

**Histogram**

Used the histogram to understand:

- Frequency distribution
- Data shape
- Possible skewness

The histogram helped visualize how glucose values are distributed across different ranges.

**Box Plot**

Used the box plot to identify:

- Median value
- Spread of the data
- Possible outliers

The box plot provided a quick visual summary of the distribution and supported the statistical findings.

---

## Results & Analysis 📈

The calculated statistics showed:

- Mean Glucose value: **120.89**
- Median Glucose value: **117.00**

The mean is slightly higher than the median, which indicates that some higher glucose values increased the average. This means that the Glucose feature has a slight right-skewed distribution.

Because the dataset contains some extreme values, the median provides a better representation of the typical glucose level because it is less affected by outliers.

The histogram and box plot confirmed these statistical observations visually.

---

## Tools Used 🛠️

Python • Jupyter Notebook • NumPy • Pandas • Matplotlib

---

## Summary 📌

During this project, I learned how descriptive statistics provides the foundation for understanding datasets before applying Machine Learning algorithms.

I gained practical experience in exploring datasets, calculating measures of central tendency and spread, and analyzing the effect of outliers on statistical results.

I learned that mean, median, and mode describe the center of data, while range, variance, standard deviation, and IQR describe its variability.

I also practiced using visualization techniques such as histograms and box plots to confirm statistical findings and better understand data distribution.

By analyzing the Pima Indians Diabetes dataset, I was able to understand the behavior of the Glucose feature, identify skewness, and prepare a strong foundation for upcoming topics such as Exploratory Data Analysis (EDA), probability, and Machine Learning.
