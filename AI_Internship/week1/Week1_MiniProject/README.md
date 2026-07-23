# Week 1 — Integrated Data Analysis Mini Project 🧪

## Overview

This mini project combines everything learned throughout **Week 1** of the BinX Tech AI & Machine Learning Internship into a single, complete data analysis workflow.

The dataset used is a real (messy) online-course student dataset, containing missing values, inconsistent category names, and invalid entries — the kind of imperfect data every real-world project starts with.

The project follows the standard Data Analysis pipeline:

**Load → Explore → Clean → Analyze → Visualize**

---

## Objectives 🎯

By the end of this notebook, I practiced how to:

- Load and inspect a real dataset using Pandas.
- Identify and handle missing values, invalid entries, and inconsistent text formatting.
- Compute summary statistics and a derived numeric feature using NumPy.
- Create multiple labeled visualizations using Matplotlib.
- Interpret each visualization and document findings in Markdown.

---

## Dataset 📁

`Students_Courses.csv` — student records including:

- `StudentID`, `Name`
- `StudyTime` (hours studied)
- `Score` (exam score)
- `Level` (course level)
- `Completed` (yes/no)
- `City`

The raw data included missing values (`StudyTime`, `Score`), inconsistent capitalization (`Beginner` / `beginner` / `ADVANCED`), and invalid entries (a negative `StudyTime` and a `Score` above 100).

---

## Workflow 🔄

### 1. Data Loading and Cleaning
Using Pandas to:
- Load the dataset and inspect its structure (`head`, `shape`, `info`, `describe`).
- Fill missing `StudyTime` and `Score` values with the column mean.
- Standardize inconsistent category names (`Level`, `City`) with `.str.title()`.
- Remove invalid rows (negative study time, out-of-range scores).

### 2. Numerical Processing
Using NumPy to:
- Compute mean, standard deviation, and median of scores.
- Generate a derived feature (`Score_per_Hour`) measuring study efficiency.

### 3. Data Visualization
Using Matplotlib to:
- Plot a histogram of score distribution.
- Plot a scatter chart of study time vs. score.
- Plot a bar chart of average score by course level.
- Plot a line chart of sorted scores.
- Combine two of these into a side-by-side subplot comparison.

### 4. Documentation and Version Control
- Explained every cleaning decision and every visualization in Markdown.
- Organized the notebook into clear, labeled sections.
- Committed the finished notebook to GitHub with a clear commit message.

---

## Key Findings 📌

- Cleaning revealed real data-quality issues (duplicate-looking records, invalid entries) that would have distorted every statistic if left unhandled.
- Scores are fairly evenly distributed (mean ≈ median), with no extreme outliers after cleaning.
- Study time and score are positively related, though not perfectly — study time alone doesn't fully determine performance.
- Average score increases from Beginner to Advanced course levels.

---

## Files 📂

| File | Description |
|---|---|
| `Week1 Mini Project.ipynb` | The full integrated notebook (load → clean → analyze → visualize) |
| `Students_Courses.csv` | The raw dataset used in the analysis |

---

## Tools Used 🛠️

Python • NumPy • Pandas • Matplotlib • Jupyter Notebook • Git & GitHub

---

## Conclusion

This project brought together every skill from Week 1 into one realistic workflow: cleaning messy real-world data, extracting insight with NumPy, and communicating findings visually with Matplotlib — the same load → process → visualize pipeline used throughout the rest of the internship.
