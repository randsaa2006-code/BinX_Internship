# Day 1 — Train / Validation / Test Splits 🎯

## Overview
Week 4 opens Phase 2 by turning "a model that runs" into "a model that can be trusted." Up through Week 3, models were evaluated with a single train/test split — this notebook shows why that isn't enough once tuning is involved, and introduces the **three-way split** (train, validation, test) as the professional fix. Using the cleaned **Titanic dataset** (`titanic_preprocessed.csv`, 418 passengers), this notebook builds a stratified 60/20/20 split, tunes a Logistic Regression hyperparameter using the validation set only, and opens the test set exactly once at the end.

## Learning Objectives 🎯
By the end of this notebook, I learned how to:

- Explain why a validation set is needed in addition to a test set.
- Create a correct three-way split in Scikit-learn.
- Explain why tuning against the test set produces misleading results.

## Topics Covered 📚

**1. The Problem With a Single Test Set**
Repeatedly checking the test set while tuning slowly fits decisions to that specific test set, so its score stops being an honest estimate of real-world performance.

**2. The Three-Way Split**
Train (learns parameters), validation (tuning decisions), test (one-time honest estimate) — each set has exactly one job, and the test set is opened only once, after every decision is final.

**3. Building the Split in Code**
Two calls to `train_test_split`: first carve off 20% as test, then split the remainder 75/25 into train (60% of total) and validation (20% of total) — stratified on `Survived` and reproducible via `random_state=42`.

**4. Tuning Using Validation Only**
Trained Logistic Regression on the training set and compared several values of `C` (regularization strength), judged only on validation accuracy — the test set stayed untouched during this step.

**5. Why One Validation Split Can Still Mislead**
A single validation set can be an unusually easy or hard slice of the data, especially on a small dataset — motivating k-fold cross-validation, covered next on Day 2.

## Hands-On Lab 🖥️
- Took the preprocessed Titanic dataset and created a stratified 60/20/20 train/validation/test split with a fixed `random_state`.
- Trained a Logistic Regression model on the training set and tuned `C` by checking validation accuracy only.
- Evaluated the final model on the test set exactly once and reported the score.
- Documented, in Markdown, what would go wrong if `C` had been tuned against the test set instead.

## Key Findings 📊
- The 60/20/20 split landed almost exactly on target (250 / 84 / 84 rows), and stratifying on `Survived` kept the survival rate consistent (~0.36) across all three sets.
- `C=0.1` was selected using validation accuracy alone; the test set was never opened during the tuning loop.
- **A known quirk of this specific file** (also flagged in Week 3, Day 3): its `Survived` column matches the classic gender-only benchmark (every female marked survived, every male not) with 100% agreement. This means the very high validation/test accuracy reflects that labeling quirk, not genuine model skill — the split and tuning *process* is still exactly what's being evaluated here.
- Tuning against the test set instead of validation would have produced an overly optimistic, misleading performance estimate, since the chosen hyperparameter would have been fit to that one specific test sample rather than to what generalizes.

## Tools Used 🛠️
Python • Jupyter Notebook • Pandas • NumPy • Scikit-learn • Git & GitHub

## 🚀 GitHub Submission
This notebook has been completed as part of my AI & Machine Learning Internship portfolio. It demonstrates correct train/validation/test discipline — a stratified 60/20/20 split, hyperparameter tuning using the validation set only, and a test set opened exactly once — on a real-world dataset. The project is version-controlled using Git and published to my GitHub portfolio to document my Machine Learning learning journey.

## Reflection
Before this notebook, splitting data into train and test always felt like a single, final step. Building the three-way split made it clear that the validation set is really what protects the honesty of the test set — every tuning decision needs somewhere to happen that isn't the final exam. Starting from the already-preprocessed file also let me focus entirely on the split and tuning logic instead of redoing cleaning work. Finding that this file's `Survived` column is just the gender-only benchmark was a good reminder to check *why* a result looks good before trusting it, the same lesson from Week 3, Day 3. The discipline of "test set opened exactly once" is a habit I want to carry into every notebook from here on, especially once GridSearchCV in Day 4 makes it much easier to accidentally tune against the wrong set.

## Conclusion
In this notebook, I built a stratified 60/20/20 train/validation/test split on the cleaned Titanic dataset and used it correctly: trained on the training set, tuned the `C` hyperparameter of a Logistic Regression model using only the validation set, and evaluated the final model on the test set exactly once. I identified and documented a labeling quirk in this specific dataset file so the high accuracy is interpreted correctly rather than mistaken for model skill, and explained why tuning against the test set instead would have produced a misleading, overly optimistic estimate. This three-way split discipline is the foundation the rest of Week 4 builds on — cross-validation (Day 2) replaces the single validation split with a more robust average, and by Day 5 this gets packaged into a leak-free Scikit-learn Pipeline.
