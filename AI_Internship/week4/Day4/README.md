# Day 4 — Feature Engineering & Hyperparameter Tuning 🧠

## Overview
Day 3 diagnosed model fit through the bias-variance trade-off. This notebook moves to systematically improving a model: engineering new features from the Titanic dataset (`titanic_train.csv`, 891 passengers), establishing an untuned Random Forest baseline, tuning it with `GridSearchCV` and 5-fold stratified cross-validation, comparing tuned vs. untuned performance, and identifying which engineered feature mattered most through controlled ablation.

## Learning Objectives 🎯
By the end of this notebook, I learned how to:

- Engineer new features and justify each with domain reasoning.
- Distinguish learned parameters from hyperparameters.
- Tune a model systematically with `GridSearchCV`.
- Interpret `best_params_` and `best_score_`.
- Compare tuned performance against an untuned baseline.

## Topics Covered 📚

**1. Feature Engineering**
Created `FamilySize` (`SibSp + Parch + 1`), `IsAlone` (whether `FamilySize == 1`), and `FarePerPerson` (`Fare / FamilySize`) — all built from predictor columns only, so `Survived` is never used to construct them.

**2. Train/Validation/Test Split**
Held out the final test set first; hyperparameters are selected only from the training portion using stratified cross-validation, and the test set is opened once at the end.

**3. Hyperparameters vs. Parameters**
A parameter (e.g. a tree split) is learned during fitting; a hyperparameter (e.g. `n_estimators`, `max_depth`) is chosen before fitting.

**4. GridSearchCV**
Searched a 12-configuration grid (`n_estimators` × `max_depth` × `min_samples_leaf`) with 5-fold stratified cross-validation and F1 scoring — 60 total model fits.

**5. Tuned vs. Untuned Comparison**
Compared the best cross-validated configuration directly against the untuned baseline, using the same metric and the same split.

**6. Feature Contribution — Controlled Ablation**
Rather than guessing which engineered feature mattered most, each one was removed separately and the tuned model re-evaluated with the same 5-fold CV — the largest score drop after removal identifies the strongest measured contributor.

**7. Leakage Audit & Sanity Checks**
Verified no target leakage, matching train/test columns, disjoint train/val/test indices, and correct 5-fold stratification — plus confirmation the test set was never touched during tuning.

## Hands-On Lab 🧪
- Created and justified three engineered features (`FamilySize`, `IsAlone`, `FarePerPerson`) in Markdown.
- Defined a hyperparameter grid for a Random Forest.
- Ran `GridSearchCV` with 5-fold cross-validation and reported the best parameters and score.
- Compared the tuned model's cross-validated score against the untuned baseline.
- Documented which engineered feature and hyperparameter mattered most, using controlled ablation rather than assumption.

## Key Findings 📊
- **Untuned baseline** (Random Forest, default settings): CV F1 = **0.7258 ± 0.0481**.
- **Tuned model** (`GridSearchCV`, best config: `max_depth=None`, `min_samples_leaf=2`, `n_estimators=100`): CV F1 = **0.7539 ± 0.0576** — an improvement of **+0.0281** over the untuned baseline.
- **Strongest engineered feature by ablation**: `FamilySize` (estimated contribution ≈ 0.0179 F1) — determined by actually removing each feature and re-measuring performance, not by assumption.
- **Final test F1** (evaluated exactly once, after all tuning was complete): **0.6970**.
- All leakage and sanity checks passed: no target leakage, correct train/val/test separation, 5-fold stratification confirmed, and the test set was not used during model selection.

## Tools Used 🛠️
Python • Jupyter Notebook • Pandas • NumPy • Matplotlib • Scikit-learn (`GridSearchCV`, `RandomForestClassifier`, `ColumnTransformer`, `Pipeline`, `StratifiedKFold`, `f1_score`)

## 🚀 GitHub Submission
This notebook has been completed as part of my AI & Machine Learning Internship portfolio. It demonstrates feature engineering with domain justification, systematic hyperparameter tuning with `GridSearchCV`, a tuned-vs-untuned comparison, and evidence-based feature-contribution analysis via ablation — all inside a leak-free Scikit-learn Pipeline. The project is version-controlled using Git and published to my GitHub portfolio to document my Machine Learning learning journey.

## Reflection
This notebook reinforced that improving a model isn't only about choosing a fancier algorithm — how the raw data is represented can hand the model more useful signal than a more complex model would. The ablation experiment was the most valuable part: instead of assuming `FamilySize` mattered because it made narrative sense, actually removing it and re-measuring performance turned that into evidence. `GridSearchCV` also made the case for systematic search over manual tuning — every one of the 60 fits was evaluated under the exact same cross-validation procedure, so the comparison between configurations was fair in a way that hand-tuning never quite is. Keeping preprocessing inside the pipeline, rather than doing it once beforehand, was the detail that made the whole evaluation trustworthy: every fold's transformations were fit only on that fold's training data.

## Conclusion
In this notebook, I engineered three features from the Titanic dataset and justified each with domain reasoning, established an untuned Random Forest baseline (CV F1 = 0.7258), and used `GridSearchCV` with 5-fold stratified cross-validation to tune it (CV F1 = 0.7539, +0.0281 improvement). I identified `FamilySize` as the strongest-contributing engineered feature through controlled ablation rather than assumption, and confirmed the final model's test F1 (0.6970) reflects a one-time evaluation after all tuning decisions were already final. This systematic, leak-free approach to feature engineering and tuning is the foundation Day 5 builds on, packaging this same workflow into a single, reusable Scikit-learn Pipeline.
