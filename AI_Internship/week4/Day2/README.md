# Day 2 — Cross-Validation 🔄

## Overview
Day 1 established a train/validation/test split. This notebook moves from a single validation split to **5-fold cross-validation** on the Titanic dataset (`titanic_train.csv`, 891 passengers), using Logistic Regression on a simplified numeric feature set (`Pclass`, `Age`, `SibSp`, `Parch`, `Fare`). It runs `cross_val_score`, reports mean ± standard deviation, verifies `StratifiedKFold` keeps class proportions consistent across folds, and compares the cross-validated estimate to a final test score.

## Learning Objectives 🎯
By the end of this notebook, I learned how to:

- Explain why cross-validation is more reliable than a single validation split.
- Explain how k-fold cross-validation works and run it with `cross_val_score`.
- Interpret mean and standard deviation across folds.
- Explain why Stratified K-Fold matters for a classification problem.

## Topics Covered 📚

**1. Limitations of a Single Validation Split**
One validation split can happen to contain easier or harder examples by chance, making its score unreliable on its own.

**2. k-Fold Cross-Validation**
The training data is divided into k folds; the model trains and validates k times, each time on a different fold, producing k scores instead of one.

**3. Mean ± Standard Deviation**
The mean summarizes average performance across folds; the standard deviation shows how much that performance varies fold to fold.

**4. `cross_val_score` and Stratified K-Fold**
Ran both plain and stratified 5-fold cross-validation, and confirmed each fold's survival rate stays close to the overall training survival rate (~38%).

**5. Cross-Validation vs. a Single Split**
Compared the cross-validated mean F1 to a final test F1, computed only once at the end.

**6. Scope Note on Feature Selection**
`Sex` and `Embarked` were deliberately left out of the feature set, even though `Sex` is the single strongest predictor of Titanic survival — the goal here was to isolate cross-validation mechanics on a small, purely numeric feature set, not to build the strongest possible classifier.

## Hands-On Lab 🖥️
- Ran 5-fold cross-validation on the Logistic Regression model using `cross_val_score`.
- Reported the mean and standard deviation of the F1 scores.
- Compared the cross-validation mean to the final test F1 score.
- Explained, in writing, why Stratified K-Fold is appropriate for this classification problem.

## Key Findings 📊
- Plain 5-fold F1 scores: **[0.539, 0.549, 0.538, 0.558, 0.574]** → mean **0.552**, std **0.014**.
- Stratified 5-fold F1 scores: **[0.558, 0.538, 0.563, 0.462, 0.588]** → mean **0.542**, std **0.043** — a wider spread than the unstratified run, coming from the same 5 rows of data reshuffled into different folds.
- Final test F1: **0.491** — noticeably below both cross-validated means, illustrating exactly the point of Day 2: a single evaluation number (whether from one validation split or one test set) can under- or over-state a model's typical performance.
- Every fold's survival rate stayed close to the overall ~38%, confirming `StratifiedKFold` preserved the class balance correctly.
- These F1 scores (~0.49–0.55) are noticeably lower than what's achievable on this dataset — a deliberate, documented trade-off from excluding `Sex`, not a bug.

## Tools Used 🛠️
Python • Jupyter Notebook • Pandas • NumPy • Scikit-learn (`train_test_split`, `cross_val_score`, `StratifiedKFold`, `LogisticRegression`, `f1_score`)

## 🚀 GitHub Submission
This notebook has been completed as part of my AI & Machine Learning Internship portfolio. It demonstrates 5-fold and stratified 5-fold cross-validation on the Titanic dataset, reporting mean ± standard deviation and comparing that estimate to a final test score. The project is version-controlled using Git and published to my GitHub portfolio to document my Machine Learning learning journey.

## Reflection
Running cross-validation made it clear that a single score — from one validation split or even one test set — can be misleading on its own. The gap between the cross-validated mean (~0.55) and the final test F1 (~0.49) was a concrete example of that: not a mistake, just a reminder that any one number is a sample, not a certainty. Comparing the plain and stratified fold scores was also useful — the stratified run actually showed a wider spread here, which was a good check against assuming stratification always tightens the numbers; it exists to fix class balance, not to guarantee a smoother-looking result. Writing out the Stratified K-Fold explanation by hand, instead of just running the code, also made the ~38% survival rate check in Section 2.10 feel like evidence for an argument rather than just a printed number.

## Conclusion
In this notebook, I applied 5-fold and stratified 5-fold cross-validation to a Logistic Regression model on the Titanic dataset, using `cross_val_score` and `StratifiedKFold`. I reported the mean and standard deviation of the F1 scores, confirmed that stratification kept each fold's class balance close to the overall ~38% survival rate, and compared the cross-validated estimate to a one-time final test score. I also documented why `Sex` and `Embarked` were left out of this notebook's feature set, so the lower F1 scores are read as a scope decision rather than an oversight. This notebook builds directly on Day 1's train/validation/test discipline, replacing the single validation split with a more robust, multi-fold estimate — the foundation for diagnosing bias and variance in Day 3.
