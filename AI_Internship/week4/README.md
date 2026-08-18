# Week 4 — Evaluation, Tuning & Pipelines 🎯

## Overview
Week 4 is the second week of Phase 2: turning a model that runs into a model that is trustworthy. Using the Titanic dataset (`titanic_train.csv`, 891 passengers), this week moves through five connected days — a three-way train/validation/test split, 5-fold cross-validation, diagnosing bias-variance trade-offs, feature engineering with systematic hyperparameter tuning, and finally packaging everything into a single leak-free Scikit-learn Pipeline.

## Learning Objectives 🎯
By the end of this week, I learned how to:

- Explain why a validation set and a test set each need their own separate role.
- Evaluate a model reliably with k-fold cross-validation instead of a single split.
- Diagnose overfitting and underfitting using the bias-variance trade-off.
- Engineer new features and correctly encode/scale existing ones to improve model performance.
- Tune hyperparameters systematically with `GridSearchCV`.
- Package preprocessing and modeling into a single leakage-free Scikit-learn `Pipeline`.

## Topics Covered 📚

**Day 1 — Train/Validation/Test Splits**
Repeatedly checking a single test set while tuning fits decisions to that test set, so its score stops being honest. The fix: a stratified 60/20/20 split, where the validation set absorbs every tuning decision and the test set opens exactly once, at the end. Tuned Logistic Regression's `C` using validation accuracy only.

**Day 2 — Cross-Validation**
A single validation split can be a lucky or unlucky slice of the data. 5-fold cross-validation replaces it with five rotating folds, averaged into a mean ± standard deviation — a far more stable estimate. Confirmed `StratifiedKFold` preserves the true survival rate in every fold.

**Day 3 — Bias-Variance & Diagnosing Model Fit**
Every model failure is underfitting (high bias — poor on both training and validation) or overfitting (high variance — great on training, poor on validation). The train-vs-validation gap is the diagnostic tool. Deliberately overfit and underfit a Decision Tree, then fixed the overfitting via `max_depth` regularization and via Ridge/Lasso penalties on Logistic Regression.

**Day 4 — Feature Engineering & Hyperparameter Tuning**
Better features often improve results more than a fancier model. Engineered `FamilySize`, `IsAlone`, and `FarePerPerson`, then used `GridSearchCV` with 5-fold cross-validation to systematically search a Random Forest hyperparameter grid — comparing the tuned result against the untuned baseline and identifying which engineered feature mattered most through controlled ablation.

**Day 5 — Scikit-learn Pipelines & Tuned Mini-Project**
Manual preprocessing-then-modeling is exactly how leakage sneaks in. A `Pipeline` chains a `ColumnTransformer` (scaling numeric columns, encoding categorical ones) and a model into one object, so every cross-validation fold is preprocessed using only that fold's own training data. Tuned the entire pipeline end-to-end with `GridSearchCV` and evaluated it once on the held-out test set.

## Hands-On Lab 🧪
- **Day 1**: Built a 60/20/20 stratified split; tuned `C` on validation only; evaluated on test exactly once; documented what would go wrong tuning against the test set instead.
- **Day 2**: Ran 5-fold `cross_val_score`; reported mean ± std; compared to the Day 1 single-split score; confirmed stratified folds.
- **Day 3**: Deliberately overfit and underfit a Decision Tree; applied regularization to close the gap; documented each diagnosis with score evidence.
- **Day 4**: Engineered and justified new features; defined and ran a `GridSearchCV` hyperparameter grid; compared tuned vs. untuned; identified the most impactful feature and hyperparameter.
- **Day 5**: Built a `ColumnTransformer` + `Pipeline`; added Day 4's engineered features; tuned the whole pipeline with `GridSearchCV`; evaluated once on the test set; documented a Git commit message.

## Key Findings 📊
- **Day 1**: Stratified 60/20/20 split (250/84/84 rows), `C=0.1` selected purely from validation accuracy.
- **Day 2**: Cross-validated F1 ranged 0.65–0.76 across folds (mean ≈ 0.72, std ≈ 0.04) — real, visible spread that shows why a single split can't be fully trusted.
- **Day 3**: Overfit tree gap = 0.198; underfit tree gap = -0.017; regularized tree (`max_depth=4`) gap = -0.030; final selected model (`max_depth=10`) test F1 = 0.672.
- **Day 4**: Untuned baseline CV F1 = 0.7258 ± 0.0481; tuned CV F1 = 0.7539 ± 0.0576 (+0.0281); strongest feature by ablation = `FamilySize`; final test F1 = 0.6970.
- **Day 5**: Baseline pipeline CV F1 = 0.7357 ± 0.0153; tuned pipeline CV F1 = 0.7623 ± 0.0274 (+0.0266, best config: `max_depth=10`, `min_samples_leaf=2`, `n_estimators=200`); final test F1 = 0.7302, consistent with the cross-validated estimate.
- Across the week, F1 climbed from an early baseline (~0.72–0.74) to a fully tuned, leak-free pipeline (~0.76 cross-validated, 0.73 on a one-time final test) — a real, evidence-backed improvement, not overfitting to the validation folds.

## Tools Used 🛠️
Python • Jupyter Notebook • Pandas • NumPy • Matplotlib • Scikit-learn (`train_test_split`, `cross_val_score`, `StratifiedKFold`, `LogisticRegression`, `Ridge`, `Lasso`, `DecisionTreeClassifier`, `RandomForestClassifier`, `GridSearchCV`, `ColumnTransformer`, `Pipeline`, `StandardScaler`, `OneHotEncoder`) • Git & GitHub

## 🚀 GitHub Submission
This repository covers Week 4 of my AI & Machine Learning internship at BinX Tech: five connected notebooks demonstrating correct train/validation/test discipline, cross-validation, bias-variance diagnosis, systematic feature engineering and hyperparameter tuning, and a fully leak-free Scikit-learn Pipeline. Each day builds directly on the one before it, culminating in Day 5's tuned end-to-end pipeline — the same structure the Phase 3 capstone project requires. Version-controlled using Git and published to my GitHub portfolio.

## Reflection
This week changed how I think about a model's score — a single number from one split or one test set was never the point; the point is whether that number can be trusted, and how much it might have moved under a different split. Each day built directly on the last: Day 2's cross-validated mean gave Day 3 something reliable to diagnose bias-variance against, Day 3's gap diagnosis explained why Day 4's tuning needed cross-validation rather than a lucky single split, and Day 5's pipeline made every one of those earlier lessons structurally enforced rather than just something I remembered to do by hand. Finding and fixing the same subtle bug in my own Day 4 and Day 5 work (a pandas `.astype(str)` quirk with `None` values silently breaking a plot) was also a good reminder that a notebook running without visible errors isn't the same as a notebook that's actually correct — it needs to be executed and checked, not just read.

## Conclusion
Over five days, I moved from a single train/test split to a fully tuned, leakage-free Scikit-learn Pipeline. I learned to hold out a test set correctly, get a reliable performance estimate through cross-validation, diagnose why a model is failing before trying to fix it, engineer features and search for good hyperparameters systematically rather than by hand, and finally combine all of that into one reusable, leak-free object. The week's final tuned pipeline improved F1 from an early baseline around 0.72–0.74 to a cross-validated 0.7623, confirmed by a one-time final test F1 of 0.7302 — real, generalizing improvement rather than a result of overfitting to the tuning process itself. This is the exact professional workflow the Phase 3 capstone project builds on.
