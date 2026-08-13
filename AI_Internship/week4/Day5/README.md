# Day 5 — Scikit-learn Pipelines & Tuned Mini-Project 🧠

## Overview
Week 4 closes by combining every idea from Days 1–4 into one professional, leakage-free workflow. On the Titanic dataset (`titanic_train.csv`, 891 passengers), this notebook carries forward Day 4's engineered features, builds a `ColumnTransformer` that treats numeric and categorical columns differently, chains preprocessing and modeling into a single `Pipeline`, tunes the entire pipeline end-to-end with `GridSearchCV`, and evaluates the final tuned pipeline exactly once on a held-out test set.

## Learning Objectives 🎯
By the end of this notebook, I learned how to:

- Build a `Pipeline` that chains preprocessing and modeling leak-free.
- Use `ColumnTransformer` to preprocess numeric and categorical columns differently.
- Tune an entire pipeline with `GridSearchCV` and evaluate it correctly.

## Topics Covered 📚

**1. EDA-Informed Data Quality Check**
A concise check of missing values, duplicates, and target balance before building the pipeline.

**2. Feature Engineering**
Carried forward `FamilySize`, `IsAlone`, and `FarePerPerson` from Day 4.

**3. Holding Out the Test Set**
Separated the final test set before any model development; the training portion alone is used for tuning and 5-fold cross-validation.

**4. ColumnTransformer for Mixed Data**
Numeric columns get median imputation + scaling; categorical columns get most-frequent imputation + one-hot encoding — combined in one `ColumnTransformer`.

**5. Building the End-to-End Pipeline**
Preprocessing and the Random Forest model become a single object: `pipe.fit()` scales/encodes and trains in one call, and every cross-validation fold is preprocessed using only that fold's training data.

**6. Tuning the Whole Pipeline**
`GridSearchCV` searched 12 configurations (`model__n_estimators` × `model__max_depth` × `model__min_samples_leaf`) with 5-fold cross-validation — 60 total pipeline fits.

**7. Train-vs-Validation Diagnostic**
Applied Day 3's bias-variance lens directly to the grid search results, comparing `mean_train_score` and `mean_test_score` across configurations.

**8. Leakage Audit & Final Test Evaluation**
Verified no target leakage, correct train/test separation, and that preprocessing lives entirely inside the pipeline — then evaluated the best pipeline on the test set exactly once, after every decision was already final.

## Hands-On Lab 🧪
- Built a `Pipeline` with a `ColumnTransformer` handling numeric (imputation + scaling) and categorical (imputation + one-hot encoding) columns.
- Added the Day 4 engineered features into the workflow.
- Tuned the full pipeline with `GridSearchCV` and 5-fold cross-validation.
- Evaluated the final tuned pipeline once on the held-out test set and reported the metric against the baseline.
- Documented a Git commit message for the finished pipeline notebook.

## Key Findings 📊
- **Baseline pipeline** (untuned Random Forest inside the full preprocessing pipeline): CV F1 = **0.7357 ± 0.0153**.
- **Tuned pipeline** (`GridSearchCV`, best config: `max_depth=10`, `min_samples_leaf=2`, `n_estimators=200`): CV F1 = **0.7623 ± 0.0274** — an improvement of **+0.0266** over the baseline.
- **Final test F1** (evaluated exactly once, after all tuning was complete): **0.7302** — consistent with the cross-validated estimate, with no sign the model was fit to the test set.
- All leakage checks passed: no target leakage, correct train/test separation, preprocessing entirely inside the pipeline, and 5-fold cross-validation confirmed on every grid configuration.
- The train-vs-validation gap across grid configurations stayed reasonable for the selected model, consistent with Day 3's diagnosis that a well-regularized model (via `max_depth` and `min_samples_leaf`) avoids the large gap seen in an unrestricted tree.

## Tools Used 🛠️
🐍 Python • 🐼 Pandas • 🔢 NumPy • 📊 Matplotlib • 🤖 Scikit-learn (`Pipeline`, `ColumnTransformer`, `GridSearchCV`, `StratifiedKFold`, `RandomForestClassifier`, `StandardScaler`, `OneHotEncoder`, `SimpleImputer`) • Git & GitHub

## 🚀 GitHub Submission
**Notebook:** `Scikit-learn Pipelines & Tuned Mini-Project.ipynb`
**Suggested commit message:** `feat: complete week 4 tuned pipeline mini-project`

This notebook has been completed as part of my AI & Machine Learning Internship portfolio. It demonstrates a complete, leak-free machine-learning workflow — feature engineering, a `ColumnTransformer` for mixed data, a `Pipeline` combining preprocessing and modeling, end-to-end `GridSearchCV` tuning, and a one-time final test evaluation. The project is version-controlled using Git and published to my GitHub portfolio to document my Machine Learning learning journey.

## Reflection
The main lesson from this mini-project is that a professional machine-learning workflow is more than a sequence of separate preprocessing and modeling commands — it's one object that can be fit, cross-validated, and tuned as a single unit, with no manual step where leakage could sneak in. Applying Day 3's train-vs-validation lens directly to the grid search results tied the whole week together: the same diagnostic that caught an overfit Decision Tree earlier in the week worked just as well on a tuned Random Forest inside a full pipeline. Watching the tuned pipeline's final test F1 (0.7302) land close to its cross-validated estimate (0.7623) was reassuring in a specific way — a bigger gap there would have suggested the tuning process had somehow leaked information, and it didn't.

## Conclusion
Week 4 ends with a complete, tuned, leakage-free machine-learning workflow. The final pipeline combines feature engineering, numeric/categorical preprocessing via `ColumnTransformer`, a Random Forest model, and end-to-end `GridSearchCV` tuning — all cross-validated as a single object. The tuned pipeline improved cross-validated F1 from 0.7357 to 0.7623 (+0.0266) over the untuned baseline, and its final one-time test F1 (0.7302) confirmed the improvement generalizes rather than reflecting overfitting to the validation folds. This is the exact structure — clean data in, leak-free pipeline out — that the Phase 3 capstone project builds on.
