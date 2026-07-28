# Day 3 — Linear Algebra for ML 🧮

## Overview

This project focuses on the linear-algebra objects every Machine Learning model is built on: vectors, matrices, the dot product, and matrix multiplication.

The goal is to understand that every dataset in ML is a matrix (rows are samples, columns are features), every model's parameters are vectors or matrices, and training is simply a sequence of matrix operations — so understanding these objects means understanding what a model is literally doing internally.

---

## Learning Objectives 🎯

By the end of this notebook, I will have learned how to:

- Represent a single data sample as a vector and a full dataset as a matrix.
- Compute a dot product and explain why it is central to how a model predicts.
- Perform matrix multiplication and reason about the resulting shapes.
- Recognize and fix shape-mismatch errors.

---

## Topics Covered 📚

### 1. Why Linear Algebra Is the Language of ML

Every dataset in ML is a matrix: rows are samples, columns are features. Every model's parameters are vectors or matrices, and training is a sequence of matrix operations.

### 2. Vectors

A vector is an ordered list of numbers — in ML, it usually represents one data sample's features.

```python
v = np.array([25, 50000, 3])  # a sample: age, income, tenure
```

### 3. Matrices

A matrix is a 2D grid of numbers — a full dataset, where each row is a sample vector and each column is a feature. Its shape is (rows, columns) = (samples, features).

```python
X = np.array([[25, 50000, 3],
              [40, 80000, 10],
              [33, 62000, 5]])
X.shape  # (3, 3): 3 samples, 3 features
```

### 4. The Dot Product

The dot product multiplies two vectors element-by-element and sums the result, producing a single number. A linear model's prediction is exactly the dot product of a feature vector and a weight vector, plus a bias.

```python
prediction = np.dot(features, weights)
```

### 5. Matrix Multiplication

Matrix multiplication applies the dot product across whole matrices at once, letting a model predict for every sample in a dataset in one operation. The rule: an (m × n) matrix times an (n × p) matrix gives an (m × p) matrix — the inner dimensions must match.

```python
predictions = X @ w
```

---

## Hands-On Lab 🧪 *(in progress)*

### Step 1: Represent Data as a Matrix

Represent three data samples as a (3 × features) NumPy matrix.

### Step 2: Compute a Dot Product

Compute the dot product of one sample vector with a weight vector by hand, then verify it with `np.dot`.

### Step 3: Matrix Multiplication for Predictions

Use matrix multiplication (`@`) to produce a prediction for all three samples at once.

### Step 4: Shape-Mismatch Error

Deliberately create a shape-mismatch error, read the message, and explain in Markdown why it occurred and how to fix it.

---

## Tools Used 🛠️

Python • Jupyter Notebook • NumPy

---

## Status

📌 Planning complete — notebook implementation in progress.
