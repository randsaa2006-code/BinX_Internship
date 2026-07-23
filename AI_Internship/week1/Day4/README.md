# Day 4 — Pandas: Tabular Data 📊

## Overview

This project explores the fundamentals of **Pandas** for working with tabular datasets.  
The goal is to learn how to load, inspect, clean, transform, and analyze real-world data using **DataFrames** and essential Pandas operations.

Pandas is one of the most important libraries in Python for data analysis and is widely used in **Machine Learning workflows** for data preparation and exploration.

---

## Learning Objectives 🎯

By the end of this notebook, I learned how to:

- Load a real dataset into a Pandas DataFrame.
- Understand the structure and characteristics of a dataset.
- Inspect datasets using different Pandas functions.
- Select columns and filter rows based on conditions.
- Handle missing values and duplicate records.
- Convert data types when needed.
- Perform grouping and aggregation operations.
- Extract insights and patterns from tabular data.

---

## Topics Covered 📚

### 1. Series and DataFrames

- Understanding the difference between:

  - **Series:** A one-dimensional labeled structure that represents a single column.
  - **DataFrame:** A two-dimensional table containing rows and multiple named columns.

- Practiced accessing columns and understanding the basic structure of Pandas objects.

---

### 2. Loading and Inspecting Data

Loaded the dataset using:

```python
pd.read_csv()
```

Used different functions to explore and understand the dataset:

```python
df.head()
df.shape
df.info()
df.describe()
```

Performed:

- Viewing the first rows of the dataset.
- Checking the number of rows and columns.
- Understanding column names and data types.
- Generating statistical summaries for numerical features.

---

### 3. Selecting and Filtering Data

Learned different methods for accessing and extracting data.

Selecting a single column:

```python
df["column"]
```

Selecting multiple columns:

```python
df[["column1", "column2"]]
```

Filtering rows using conditions:

```python
df[df["column"] > value]
```

Also practiced:

- `.loc[]` for selecting data using labels and conditions.
- `.iloc[]` for selecting data based on row and column positions.

---

### 4. Data Cleaning 🧹

Learned that real-world datasets usually require preprocessing before analysis.

Applied different cleaning techniques:

Checking missing values:

```python
df.isnull().sum()
```

Handling missing values:

```python
df.fillna()
df.dropna()
```

Removing duplicate records:

```python
df.drop_duplicates()
```

Type conversion:

- Converted columns into suitable data types when required.
- Improved data consistency for further analysis.

---

### 5. Grouping and Aggregation

Used Pandas grouping techniques to analyze data and discover patterns.

Applied:

```python
df.groupby()
```

and:

```python
df.agg()
```

Performed operations such as:

- Calculating averages.
- Finding maximum values.
- Comparing different categories.
- Summarizing grouped data.

This helped understand the **split-apply-combine** concept in Pandas.

---

## Hands-On Lab 🧪

### Step 1: Dataset Exploration

Loaded a CSV dataset and inspected its:

- Shape.
- Columns.
- Data types.
- General information.

---

### Step 2: Missing Values Handling

Identified missing values in the dataset and applied suitable handling methods.

The chosen approach was based on the type of data and the importance of preserving useful records.

---

### Step 3: Data Filtering

Created meaningful subsets of the dataset using conditional filtering.

Analyzed the filtered results to identify observations and patterns.

---

### Step 4: Group Analysis

Applied `groupby()` operations to calculate statistics for different categories.

Used aggregation functions to summarize the data and extract useful insights.

---

## Tools Used 🛠️

- Python 🐍
- Pandas
- Jupyter Notebook
- CSV Dataset

---

## Summary 📌

During this project, I learned how to work with **tabular data using Pandas** and gained practical experience in the data analysis workflow.

I practiced loading datasets into DataFrames, exploring their structure, checking data types, and generating statistical summaries using different Pandas functions such as `head()`, `shape`, `info()`, and `describe()`.

I learned how to select specific columns, filter rows based on conditions, and use `.loc[]` and `.iloc[]` to access data efficiently. These techniques helped me understand how to extract meaningful information from datasets.

A major part of this project focused on **data cleaning and preprocessing**. I practiced identifying missing values, handling incomplete data, removing duplicate records, and converting data types when required. This highlighted the importance of preparing clean and consistent data before performing analysis or applying Machine Learning algorithms.

Additionally, I applied grouping and aggregation techniques using `groupby()` and `agg()` to analyze categories, calculate statistics, and discover patterns within the dataset.

Through this hands-on experience, I developed a better understanding of the role of Pandas in data analysis and how it is used as an essential step in preparing datasets for Machine Learning projects.
