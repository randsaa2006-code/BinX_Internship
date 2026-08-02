# Day 1 — Introduction to Supervised Learning and the Scikit-learn Workflow 🤖

## Overview
This notebook marks the beginning of the Machine Learning phase, after several weeks spent building the data analysis skills (cleaning, EDA, statistics) needed before any modeling task. Rather than focusing on a specific algorithm, it builds the conceptual foundation every supervised learning project relies on: understanding what supervised learning is, distinguishing regression from classification, organizing a dataset into features and target, and applying the standard Scikit-learn workflow used across nearly all classical ML models.

In this notebook, the **Titanic dataset** (`Titanic.csv`) is used throughout — each concept is explained, then immediately applied on this real dataset, rather than saving all the practice for one block at the end.

## Learning Objectives 🎯
By the end of this notebook, I learned how to:

- Explain the concept of supervised learning.
- Differentiate between regression and classification tasks.
- Identify features (X) and target (y) within a dataset.
- Understand the standard Scikit-learn workflow.
- Split a dataset into training and testing subsets.
- Explain why evaluating a model on unseen data is essential.

## Topics Covered 📚

**1. What is Supervised Learning**
Learning from labeled examples, where every training example already contains the correct answer, so the model can generalize to new, unseen data.

**2. Regression vs. Classification**
Distinguished by the type of target variable — a continuous number (regression) vs. a predefined category (classification). Confirmed the Titanic dataset's `Survived` column is binary, making this a **classification** problem.

**3. Features (X) and Target (y)**
Separated the dataset into the input features the model learns from and the target it's trying to predict, and flagged the common beginner mistake of accidentally leaking the target into the features.

**4. The Train/Test Split**
Why a model must never be evaluated on the data it was trained on (the "student memorizing exam questions" analogy), what happens if the split is skipped, and the role of `test_size` and `random_state`.

**5. The Scikit-learn API (Instantiate → Fit → Predict → Score)**
The same four-step workflow used across nearly every classical ML model — instantiate the model, train it with `.fit()`, generate predictions with `.predict()`, and evaluate with `.score()`.

## Hands-On Lab 🧪
- Loaded `Titanic.csv` and checked the target column to confirm this is a classification problem.
- Built `X` from the numeric features (`Pclass`, `Age`, `SibSp`, `Parch`, `Fare`) and `y` from `Survived`, dropping rows with missing `Age`/`Fare`.
- Performed an 80/20 train/test split with `random_state=42` and verified the resulting shapes.
- Instantiated `LogisticRegression(max_iter=1000)` — chosen because the problem is classification, not regression.
- Trained the model with `.fit()`, generated predictions with `.predict()`, and evaluated it with `.score()`.
- Restated the same four steps explicitly at the end as the formal Hands-On Lab deliverable.

## Key Findings 📊
- `Survived` is binary (266 did not survive vs. 152 survived), confirming this is a classification task, not regression.
- The 80/20 split produced 264 training rows and 67 testing rows after dropping missing `Age`/`Fare` values.
- The `LogisticRegression` model scored **≈0.72 accuracy** on the held-out test set — a first baseline, not yet a tuned or fully evaluated model.

## Tools Used 🛠️
Python • Jupyter Notebook • Pandas • Scikit-learn

## Reflection
This notebook introduced the fundamental workflow that underpins almost every supervised Machine Learning project. Understanding the distinction between features and targets, separating training and testing data correctly, and following the standardized Scikit-learn API are critical practices that help build reliable, reproducible, and unbiased Machine Learning models. These principles will remain consistent throughout the rest of the Machine Learning journey, regardless of the algorithm being used.

## Conclusion
In this notebook, I explored the core concepts of supervised learning and applied them end to end on the Titanic dataset using Scikit-learn. I distinguished between regression and classification tasks, organized the dataset into features and target variables, performed a train/test split, and trained, predicted with, and scored a first `LogisticRegression` model. These concepts represent the first stage of the Machine Learning pipeline and provide the foundation for the more advanced modeling techniques to come in later notebooks.
