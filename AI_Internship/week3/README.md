# Week 3 — Supervised Learning: Regression & Classification with Scikit-learn 🤖

## Overview
Week 3 of the BinX Tech AI & Machine Learning Internship Program marks the transition from Phase 2's math/EDA foundations into training the first real Machine Learning models. This week covers regression models that predict numbers and classification models that predict categories — linear and logistic regression, decision trees, random forests, SVMs, and k-NN — all using the Scikit-learn API.

The main focus is developing a complete supervised-learning workflow:

Supervised Learning Concepts & Scikit-learn API → Linear Regression → Logistic Regression & Classification Metrics → Trees, Forests, SVMs & k-NN → Supervised-Learning Mini-Project

All work is implemented using Jupyter Notebooks and managed through Git/GitHub.

## Week Objectives 🎯
By the end of Week 3, I have learned how to:

- Explain what supervised learning is and distinguish regression from classification.
- Split data correctly into training and test sets and explain why this prevents misleading results.
- Train, predict with, and evaluate a linear regression model and interpret its coefficients and error.
- Train and evaluate a logistic regression classifier and read a confusion matrix.
- Train and compare tree-based models (decision trees, random forests) plus SVM and k-NN.
- Assemble a complete supervised-learning mini-project: EDA → preprocessing → model → evaluation.

## Daily Progress 📅

### Day 1 — Supervised Learning Concepts & the Scikit-learn API 🤖
**Topics Covered:**
- What supervised learning is, and the difference between regression and classification.
- Features (X) and target (y).
- The consistent Scikit-learn API: instantiate, fit, predict, score.
- The train/test split and why it matters.

**Practical Work:**
- Loaded the Titanic dataset (`Titanic.csv`, 418 passengers) and confirmed `Survived` is binary, making this a classification problem.
- Built `X` from the numeric features (`Pclass`, `Age`, `SibSp`, `Parch`, `Fare`) and `y` from `Survived`, dropping rows with missing values.
- Performed an 80/20 train/test split with `random_state=42`.
- Instantiated `LogisticRegression` (matching the model to the classification problem), trained it, generated predictions, and scored it — test accuracy ≈ **0.72**.
- Completed a Hands-On Lab section restating the four required steps explicitly.

**Tools Used:**
Scikit-learn • Pandas • Jupyter Notebook

### Day 2 — Linear Regression 📈
**Topics Covered:**
- What linear regression does: fitting the best line.
- Training and predicting with Scikit-learn.
- Interpreting coefficients and the intercept.
- Regression metrics: MAE, RMSE, R².
- Comparing against a baseline.

**Practical Work:**
- Explored the California Housing dataset (`California_Housing.csv`, 20,640 observations) and split it into training and testing subsets.
- Trained a `LinearRegression` model to predict `median_house_value`.
- Interpreted the coefficients: `longitude` and `latitude` have the largest raw magnitude, but `median_income` is the most practically meaningful predictor.
- Evaluated the model — MAE ≈ $51,300, RMSE ≈ $70,300, R² ≈ 0.62.
- Compared against a mean-prediction baseline: ~39% lower RMSE, confirming the model adds real value.
- Completed a Hands-On Lab section (Steps 1–5) and a GitHub Submission summary.

**Tools Used:**
Scikit-learn (LinearRegression) • Pandas • Jupyter Notebook

### Day 3 — Logistic Regression & Classification Metrics 🎯
**Topics Covered:**
- From regression to classification: the weighted sum + sigmoid → probability.
- Why accuracy alone is misleading on imbalanced data.
- The confusion matrix: TP, FP, FN, TN.
- Precision, recall, F1, and the trade-off between them.
- AUC-ROC.

**Practical Work:**
- Preprocessed the Titanic dataset (`Titanic_Clean.csv`) — dropped `PassengerId`/`Name`/`Ticket`/`Cabin`, encoded `Sex`/`Embarked` numerically.
- Trained a `LogisticRegression` classifier and evaluated it with a confusion matrix, precision/recall/F1, and AUC-ROC.
- Achieved a perfect test-set score (100% accuracy, AUC 1.000) — flagged as a known quirk of this specific Titanic file (labels become close to perfectly separable once `Sex` is included) rather than proof of a flawless model.
- Completed a Hands-On Lab section (Steps 1–5) and a GitHub Submission summary.

**Tools Used:**
Scikit-learn (LogisticRegression) • Pandas • Matplotlib • Jupyter Notebook

### Day 4 — Trees, Forests, SVMs & k-NN 🌳
**Topics Covered:**
- Decision trees: rule-based, interpretable, prone to overfitting.
- Random forests: ensembles and feature importances.
- Support Vector Machines and the margin.
- k-Nearest Neighbors.
- Comparing models fairly on the same train/test split (no free lunch).

**Practical Work:**
- Trained a Decision Tree, Random Forest, SVM, and k-NN on the same train/test split from `Titanic_Clean.csv`.
- Compared all four on Accuracy, Precision, Recall, and F1-score in one table.
- Decision Tree and Random Forest tied exactly at F1 = 1.000 (same dataset quirk as Day 3); SVM and k-NN performed noticeably worse (F1 = 0.108 and 0.526) due to unscaled features — a real, generalizable finding.
- Reported and interpreted the Random Forest's feature importances.
- Completed a Hands-On Lab section (Steps 1–4) and a GitHub Submission summary.

**Tools Used:**
Scikit-learn (tree, ensemble, svm, neighbors) • Pandas • Jupyter Notebook

### Day 5 — Supervised-Learning Mini-Project 🏁
**Topics Covered:**
- The full pipeline: EDA → preprocessing → split → model → evaluation.
- Basic preprocessing: one-hot encoding, feature scaling.
- Avoiding data leakage (fit scaler on train only).
- Choosing the right model and metric for the task.
- Documenting the result against a baseline.

**Practical Work:**
- Assembled the complete pipeline on `Titanic_Clean.csv`: brief EDA, preprocessing (dropped non-predictive columns, one-hot encoded categoricals, scaled numeric features with the scaler fit on train only).
- Trained Logistic Regression and Random Forest, evaluated both against a majority-class baseline (baseline F1 = 0.0).
- Both models tied exactly at F1 = 1.000; selected Logistic Regression over Random Forest for its simplicity and interpretability given the tie.
- Completed a Hands-On Lab section (Steps 1–5) and a GitHub Submission summary.

**Tools Used:**
Scikit-learn • Pandas • Matplotlib / Seaborn • Jupyter Notebook • Git & GitHub

## Summary 📌
During Week 3 of the AI & Machine Learning Internship Program, I moved from pure data analysis into actually building predictive models.

I started with the shared foundations of supervised learning and Scikit-learn's consistent API, applying them to a classification problem (Titanic survival) with Logistic Regression, then to regression with a Linear Regression model on the California Housing dataset. From there, I went deeper into classification evaluation with Logistic Regression and the confusion matrix/precision/recall/F1/AUC-ROC toolkit, compared four classifier families (Decision Tree, Random Forest, SVM, k-NN) fairly on the same data, and closed the week with an end-to-end mini-project combining EDA, leakage-free preprocessing, modeling, and evaluation against a baseline into one narrated notebook.

A recurring, important lesson across Days 3–5: a perfect or near-perfect score isn't automatically something to celebrate at face value — this particular Titanic test file has a well-documented quirk that makes it close to perfectly separable once `Sex` is included, so recognizing and naming that limitation became as important as the metrics themselves.

Week 3 is complete — all five days built, evaluated, and documented with matching READMEs.
