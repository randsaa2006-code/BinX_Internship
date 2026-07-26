Day 1 — Descriptive Statistics 📊
Week 2 — Math Foundations & EDA
Overview

Week 2 marks the transition from Phase 1 (Python foundations) to Phase 2 (the math that machine learning actually runs on). Day 1 focuses on descriptive statistics — the vocabulary for describing a dataset's center, spread, and shape before any modeling begins.

Instead of jumping straight into algorithms, this day is about learning to read a dataset statistically: what is the typical value, how much do the values vary, and are there any unusual observations that could distort a future model.

Topics Covered:
Why descriptive statistics comes before modeling
Measures of central tendency:
Mean
Median
Mode
Measures of spread:
Range
Variance
Standard deviation
Interquartile range (IQR)
Percentiles and quartiles (Q1, Q2, Q3)
How outliers affect each measure differently
Dataset

Used the Pima Indians Diabetes dataset (diabetes.csv) — 768 patient records with 9 medical measurement columns. Checked the dataset structure first with df.info() and df.describe(), and confirmed there are no NaN values, though some columns (like Insulin and SkinThickness) contain zero values that likely represent missing or invalid measurements rather than real readings.

The analysis focuses on the Glucose column, since it's one of the most medically relevant features in the dataset.

Practical Work:
Loaded the dataset into a Pandas DataFrame and inspected its shape, structure, and missing values.
Worked through a small toy example ([10, 12, 12, 13, 100]) to see firsthand how a single outlier pulls the mean up while leaving the median unaffected.
Calculated mean, median, and mode for the Glucose column and compared them.
Calculated range, variance, standard deviation, and IQR to describe the spread of Glucose values.
Computed Q1, Q2 (median), and Q3 using .quantile().
Built a summary table combining all calculated statistics.
Compared the mean (120.89) and median (117.00) values, identified the distribution as slightly right-skewed, and justified why the median is the better measure of a "typical" glucose level here — it isn't strongly influenced by the unusually high glucose readings.
Visualized the distribution with a histogram and a box plot to confirm the statistical findings visually.
Tools Used

NumPy • Pandas • Matplotlib • Jupyter Notebook

Reflection

This notebook showed how far a dataset can be understood before any model is trained. Comparing the mean and median side by side made the effect of skewed data and outliers concrete rather than theoretical, and the box plot gave a quick visual way to confirm what the numbers already suggested. This groundwork — knowing the center, the spread, and where the data leans — is what the rest of Week 2 (probability, linear algebra, and the full EDA) builds on.
