# Day 3 — Bias-Variance & Diagnosing Model Fit 🧠

## Overview
Day 2 replaced a single validation split with a more reliable cross-validated estimate. This notebook uses that same train/validation/test discipline to diagnose *why* a model performs the way it does, using the bias-variance trade-off. On the Titanic dataset (`titanic_train.csv`, 891 passengers), a Decision Tree is deliberately overfit and underfit to see both failure modes directly, regularization (tree-depth control, and Ridge/Lasso on Logistic Regression) is applied to close the gap, and every diagnosis is backed with train-vs-validation score evidence.

## Learning Objectives 🎯
By the end of this notebook, I learned how to:

- Distinguish underfitting from overfitting by their symptoms.
- Explain the bias-variance trade-off and its role in tuning.
- Diagnose model fit from the train-vs-validation score gap and apply regularization.

## Topics Covered 📚

**1. The Two Ways a Model Fails**
Underfitting (high bias — poor on both training and validation) and overfitting (high variance — great on training, poor on validation) require opposite fixes, so diagnosis comes first.

**2. The Bias-Variance Trade-off**
As model complexity increases, bias falls and variance rises; the goal is the sweet spot that generalizes best.

**3. Diagnosing With the Train-vs-Validation Gap**
A large gap signals overfitting; low scores on both sets signal underfitting; high, close scores signal a good fit.

**4. Sanity Checks & Leakage Audit**
Verified the train/validation/test split has no overlapping rows, a fixed `random_state`, and confirmed the test set was not touched during model selection.

**5. Regularization — Tree Depth, Ridge, and Lasso**
Controlled Decision Tree complexity via `max_depth`, then separately applied Ridge (L2) and Lasso (L1) regularization to a Logistic Regression model across a range of `C` values, to show the same complexity-control principle applies beyond tree depth.

**6. Beyond the Requirement: A Full Complexity Sweep**
Rather than checking only 2–3 `max_depth` values, swept across 9 values to see the full overfit → good fit → underfit curve, not just isolated points.

## Hands-On Lab 🧪
- Deliberately overfit a Decision Tree (unrestricted depth) and confirmed a large train-vs-validation gap.
- Deliberately underfit a Decision Tree (`max_depth=1`) and confirmed both scores were low.
- Applied regularization — tree-depth control, and separately Ridge/Lasso on Logistic Regression — and showed the gap shrink.
- Documented each diagnosis and fix with score evidence in Markdown.

## Key Findings 📊
- **Overfit tree** (unrestricted depth, 24 levels, 126 leaves): training F1 = **0.978**, validation F1 = **0.780**, gap = **0.198** — a textbook overfitting signature.
- **Underfit tree** (`max_depth=1`): training F1 = **0.711**, validation F1 = **0.727**, gap = **-0.017** — both scores low and close together, the underfitting signature.
- **Regularized tree** (`max_depth=4`): training F1 = **0.758**, validation F1 = **0.788**, gap = **-0.030** — the overfitting gap closed by simplifying the model.
- **Ridge/Lasso on Logistic Regression**: at low `C` (strong regularization), both train and validation F1 stay modest and close together; as `C` increases toward 10–100, the gap widens — the same overfitting pattern as the tree, produced through a different mechanism (coefficient penalty instead of depth).
- **Final selected model** (`max_depth=10`, chosen via validation F1 = 0.815): test F1 = **0.672**, evaluated only once, after model selection was already final — consistent with the Day 1/Day 2 discipline of never touching the test set during tuning.
- All sanity checks passed: no overlap between train/validation/test indices, fixed `random_state=42`, and confirmed the test set was not used during model selection.

## Tools Used 🛠️
Python • Jupyter Notebook • Pandas • NumPy • Matplotlib • Scikit-learn (`DecisionTreeClassifier`, `LogisticRegression`, `Ridge`/`Lasso` penalties, `train_test_split`, `f1_score`)

## 🚀 GitHub Submission
This notebook has been completed as part of my AI & Machine Learning Internship portfolio. It demonstrates diagnosing overfitting and underfitting through the train-vs-validation gap, fixing both through regularization (tree-depth control and Ridge/Lasso), and includes a leakage audit and sanity checks confirming the test set was never touched during model selection. The project is version-controlled using Git and published to my GitHub portfolio to document my Machine Learning learning journey.

## Reflection
Seeing the same overfitting symptom show up twice — once as a 24-level tree memorizing training rows, once as a Logistic Regression with too little regularization — made the bias-variance trade-off feel like a general principle rather than something specific to trees. The gap number itself became a genuinely useful diagnostic: 0.198 for the overfit tree, -0.017 for the underfit one, -0.030 after fixing it — each one told a clear story before I even looked at the individual scores. Running the full sanity-check and leakage-audit cells at the end also mattered more than I expected; it's one thing to follow the train/validation/test discipline by habit, and another to have code that actually proves it wasn't violated.

## Conclusion
In this notebook, I diagnosed both failure modes of a Decision Tree on the Titanic dataset — a severely overfit tree (gap = 0.198) and a severely underfit one (gap = -0.017) — using the train-vs-validation gap as the diagnostic tool. I applied regularization to fix the overfitting through two different mechanisms: constraining tree depth (closing the gap to -0.030) and applying Ridge/Lasso penalties to a Logistic Regression model across a range of `C` values. A full sanity-check and leakage-audit confirmed the test set was held out correctly throughout, and the final model was evaluated on it exactly once, after selection was complete. This bias-variance diagnosis is the foundation for Day 4, where GridSearchCV automates the search for the complexity level that generalizes best.
