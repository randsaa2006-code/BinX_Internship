# Day 5 — Supervised-Learning Mini-Project 🏁

## Overview
Week 3 closes by combining everything from Days 1–4 into one complete, end-to-end supervised-learning pipeline — the same pipeline shape every project in this program follows, and a direct rehearsal for the Phase 3 capstone. Using the **Titanic dataset** (`Titanic_Clean.csv`, 418 passengers), this notebook moves through EDA, preprocessing, a leakage-free train/test split, training two models, and an honest evaluation against a baseline — all in one narrated project rather than isolated pieces.

## Learning Objectives 🎯
By the end of this notebook, I learned how to:

- Assemble a complete supervised-learning pipeline from EDA to evaluation.
- Apply basic preprocessing (encoding, scaling) without data leakage.
- Select and justify an appropriate model and metric for the task, and document the result.

## Topics Covered 📚

**1. EDA**
Checked missing values, target balance (64% did not survive vs. 36% survived), and how `Sex` and `Pclass` relate to survival before modeling anything.

**2. Preprocessing**
Dropped non-predictive columns (`PassengerId`, `Name`, `Ticket`) and `Cabin` (too sparse even after cleaning), then one-hot encoded `Sex` and `Embarked`.

**3. Train/Test Split (Before Scaling)**
Split first, stratified by `Survived` to preserve the class balance in both sets — critical for avoiding data leakage before any scaling happens.

**4. Scaling — Fit on Train Only**
Fit `StandardScaler` on the training data only, then applied `.transform()` (never `.fit()`) to the test set.

**5. Modeling & Evaluation**
Trained Logistic Regression and Random Forest on identical data, evaluated both against a majority-class baseline.

**6. Model Selection**
Chose between two tied models based on interpretability and simplicity rather than a metric difference.

## Hands-On Lab 🧪
- Chose the Titanic dataset and confirmed the task is classification (binary target).
- Performed brief EDA, then preprocessed: encoded categoricals and scaled numeric features (fit on train only).
- Trained Logistic Regression and Random Forest and evaluated both against a baseline.
- Selected Logistic Regression and justified the choice.
- Documented a suggested Git commit message for the finished notebook.

## Key Findings 📊
- The baseline (always predicting the majority class) reached **≈63% accuracy but an F1-score of 0.0**, since it never predicts the positive class — a clear illustration of why accuracy alone isn't enough.
- **Logistic Regression and Random Forest tied exactly** at F1 = 1.000. As with Days 3 and 4, this reflects a known quirk of this specific Titanic test file (its labels become close to perfectly separable once `Sex` is included) rather than proof either model is flawless in general.
- Given the exact tie, **Logistic Regression was selected** over Random Forest — when performance is equal, the simpler, more interpretable model is the better default rather than defaulting to the more complex one.

## Tools Used 🛠️
Python • Jupyter Notebook • Pandas • NumPy • Scikit-learn • Matplotlib / Seaborn • Git & GitHub

## 🚀 GitHub Submission
This notebook has been completed as part of my AI & Machine Learning Internship portfolio. It demonstrates a complete, leakage-free supervised-learning pipeline — from EDA through preprocessing, modeling, and evaluation against a baseline — on a real-world dataset. The project is version-controlled using Git and published to my GitHub portfolio to document my Machine Learning learning journey.

## Reflection
This notebook felt different from the previous four days, because for the first time I had to make every decision myself instead of following a single guided path: which columns to drop, how to encode categories, which two models to compare, and — most importantly — how to break a tie when both models performed identically. Building the full pipeline end-to-end, rather than one isolated piece of it, made it much clearer how each stage depends on the one before it: a mistake in preprocessing (like fitting the scaler on the wrong data) would have quietly invalidated the entire evaluation stage that comes after it. Realizing that Logistic Regression and Random Forest tied exactly was also a useful moment — it forced me to justify a choice using reasoning (simplicity, interpretability) rather than just pointing at a metric, which is closer to how model selection actually works in practice.

## Conclusion
In this notebook, I assembled a complete supervised-learning pipeline on the Titanic dataset, from EDA through preprocessing, a leakage-free train/test split, model training, and evaluation against a baseline. I trained and compared two models — Logistic Regression and Random Forest — found they tied exactly on every metric, and selected Logistic Regression for its simplicity and interpretability rather than defaulting to the more complex model. This notebook closes out Week 3 by combining everything from Days 1–4 into one narrated, end-to-end project, and rehearses the exact pipeline structure the Phase 3 capstone will formalize.
