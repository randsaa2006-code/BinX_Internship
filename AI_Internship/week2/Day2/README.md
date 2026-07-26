# Day 2 — Probability & Distributions 🎲

## Overview

This project focuses on understanding probability as the mathematical language of uncertainty — the foundation that every Machine Learning model's predictions ("85% likely to churn") are built on.

The goal is to learn the core rules of probability, understand how conditional probability and Bayes' theorem let a model update its beliefs as new evidence arrives, and recognize the common distributions that describe how data behaves.

The conditional probability section of this notebook continues working with the **Pima Indians Diabetes dataset** (`diabetes.csv`) used in Day 1, asking a real question: given a patient's Glucose level, what is the probability they have a positive diabetes Outcome?

---

## Learning Objectives 🎯

By the end of this notebook, I will have learned how to:

- Apply the complement, addition, and multiplication rules of probability.
- Explain conditional probability and compute P(A | B).
- Explain Bayes' theorem and how it reverses a conditional probability.
- Recognize the normal, binomial, and uniform distributions and where each appears in ML.
- Simulate probability experiments in code and verify them against theory.

---

## Topics Covered 📚

### 1. Probability Basics

Probability quantifies uncertainty on a scale from 0 (impossible) to 1 (certain). The probability of an event is the number of favorable outcomes divided by the total number of possible outcomes.

### 2. Core Rules

- **Complement**: P(not A) = 1 - P(A)
- **Addition**: P(A or B) = P(A) + P(B) - P(A and B)
- **Multiplication (independent events)**: P(A and B) = P(A) × P(B)

### 3. Conditional Probability

Conditional probability, P(A | B), is the probability of A given that B has already happened. It is the foundation of predictive modeling: "given these patient features, what is the probability of a positive diagnosis?" is a conditional probability question.

### 4. Bayes' Theorem

Bayes' theorem reverses a conditional probability — computing P(A | B) from P(B | A):

`P(A | B) = ( P(B | A) × P(A) ) / P(B)`

It combines the prior belief P(A) with the likelihood P(B | A) to produce an updated posterior belief P(A | B).

### 5. Common Distributions

| Distribution | Describes | Example |
|---|---|---|
| Normal (Gaussian) | Symmetric, bell-shaped data clustered around a mean | Glucose levels, measurement error |
| Binomial | Number of successes in a fixed number of yes/no trials | Number of heads in coin flips |
| Uniform | Every outcome equally likely | A fair die roll |

---

## Hands-On Lab 🧪 *(in progress)*

### Step 1: Coin Flip Simulation

Simulate 10,000 coin flips with NumPy and confirm the proportion of heads approaches 0.5.

### Step 2: Sampling from a Normal Distribution

Sample from a normal distribution using `np.random.normal` and plot a histogram to confirm the bell shape.

### Step 3: Conditional Probability on the Diabetes Dataset

Using `diabetes.csv`, compute P(Outcome = 1 | Glucose > threshold) by hand from the data, then verify it with a simulation/resampling check.

### Step 4: Documentation

Document each result with a Markdown explanation of what it demonstrates.

---

## Tools Used 🛠️

Python • Jupyter Notebook • NumPy • Pandas • Matplotlib

---

## Status

📌 Planning complete — notebook implementation in progress.
