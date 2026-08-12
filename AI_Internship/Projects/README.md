# Cardiac Patient Monitoring System 🫀

## Overview
This is my individual AI & Machine Learning capstone project: an end-to-end analysis of cardiovascular disease risk using the **Cardiovascular Disease dataset** (`cardio_train.csv`, 70,000 patient records). Per my mentor's guidance, the project covers every topic through the end of Week 4 of the training track — data cleaning, EDA, a supervised baseline and comparison model, cross-validation and evaluation, and feature engineering packaged into a leak-free Scikit-learn Pipeline. It does not include the unsupervised (clustering/PCA) section, since that's a later-track topic not yet covered. The whole project is delivered as a single, top-to-bottom notebook.

## Learning Objectives 🎯
By the end of this project, I learned how to:

- Load and clean a real-world healthcare dataset, documenting the target and any data-quality issues.
- Explore data with descriptive statistics, visualizations, and correlation analysis.
- Train and evaluate a baseline classifier and a comparison classifier under the same split.
- Evaluate models with cross-validation, a confusion matrix, and standard classification metrics.
- Engineer new features and package preprocessing + modeling into a single, reusable Scikit-learn Pipeline.

## Topics Covered 📚

**1. Environment & Dataset**
Loaded `cardio_train.csv` (semicolon-separated), documented a full data dictionary, and confirmed the target `cardio` is close to perfectly balanced (~50/50).

**2. Data Preparation**
Found and removed physically implausible readings (e.g. blood pressure of -150 or 16020 mmHg, heights/weights outside adult ranges) — about 2% of rows — and converted `age` from days to years.

**3. EDA & Statistics**
Studied distributions, feature-target relationships, and a correlation matrix. Found real, moderate predictive signal across several features (blood pressure, age, cholesterol) rather than one dominant feature — cardiovascular disease rate rises from ~44% at normal cholesterol to ~76% at "well above normal."

**4. Supervised Baseline**
An 80/20 stratified split, then a scaled Logistic Regression baseline (scaler fit on training data only).

**5. Model Comparison**
A Random Forest trained on the identical split, compared against the baseline on accuracy, F1, precision, recall, and ROC-AUC.

**6. Evaluation**
5-fold cross-validation for both models, a confusion matrix, and a plain-language discussion of why false negatives (missed disease cases) matter more than false positives for this application.

**7. Feature Engineering & Pipeline**
Engineered `bmi` and `pulse_pressure` (both clinically meaningful cardiovascular risk indicators), then combined scaling, encoding, and modeling into a single Scikit-learn `Pipeline`, cross-validated end-to-end with no leakage.

## Hands-On Lab 🧪
- Cleaned and documented data-quality issues in a real healthcare dataset.
- Performed EDA: distributions, feature-target relationships, correlation analysis.
- Trained a baseline (Logistic Regression) and a comparison model (Random Forest) on the same split.
- Evaluated both with 5-fold cross-validation, a confusion matrix, and standard classification metrics.
- Explained false positives vs. false negatives in plain language for this specific application.
- Engineered two new features and justified each with domain reasoning.
- Built and cross-validated a leak-free Scikit-learn Pipeline combining preprocessing and modeling.

## Key Findings 📊
- Target `cardio` stayed close to 50/50 even after cleaning — no resampling or class-weighting was needed for a fair baseline.
- **Baseline (Logistic Regression)**: F1 = 0.7145, accuracy = 0.7326.
- **Comparison model (Random Forest)**: F1 = 0.7218, accuracy = 0.7389 — a modest edge, consistent with the mild multicollinearity (`ap_hi`/`ap_lo` correlation ≈ 0.735) and non-linearity observed in EDA.
- **5-fold cross-validation**: mean F1 = 0.7067 (Logistic Regression) and 0.7149 (Random Forest), both with low standard deviation — stable estimates, not the result of a lucky split.
- **Engineered features**: `pulse_pressure` correlates with `cardio` at ~0.34 (comparable to `ap_lo` alone) and `bmi` at ~0.19 — both added real, if modest, signal.
- **Pipeline (with engineered features)**: CV F1 = 0.7088, on par with the Section 5 Random Forest result, confirming the engineered features held up under a fully leak-free evaluation.
- False negatives (missed disease cases) are the more consequential error for a cardiac monitoring system, making recall an important metric alongside accuracy.

## Tools Used 🛠️
Python • Jupyter Notebook • Pandas • NumPy • Matplotlib • Scikit-learn (`LogisticRegression`, `RandomForestClassifier`, `StandardScaler`, `ColumnTransformer`, `Pipeline`, `train_test_split`, `cross_val_score`, `StratifiedKFold`, `confusion_matrix`, `ConfusionMatrixDisplay`)

## 🚀 GitHub Submission
This notebook is my individual AI & Machine Learning capstone project submission, covering every topic through the end of Week 4 of the training track: environment setup, data cleaning, EDA, a baseline and comparison classifier, cross-validation and evaluation, and feature engineering packaged into a leak-free Scikit-learn Pipeline. It is version-controlled using Git and published to my GitHub portfolio.

## Reflection
Building this as one continuous notebook, instead of separate milestone files, made the project's logic easier to follow — each section's decisions (which features to keep, how to handle the blood pressure outliers, why Random Forest was a reasonable second model given the multicollinearity in EDA) connect directly to the section before it. The plain-language false-positive/false-negative discussion was a useful exercise too: explaining *why* one error type matters more here forced me to think about this as a real application, not just a metrics exercise. Confirming that the engineered features actually helped — through correlation and cross-validated performance, not just clinical intuition — also felt like the right habit to build.

## Conclusion
In this project, I built a complete, leak-free supervised-learning pipeline on real cardiovascular health data: cleaning physically implausible readings, exploring the data's real predictive signal, training and comparing a Logistic Regression baseline against a Random Forest, evaluating both with cross-validation and a confusion matrix, and packaging feature engineering and modeling into a single reusable Scikit-learn Pipeline. This covers every topic through the end of Week 4 of the training track, and the same leak-free structure is exactly what later hyperparameter-tuning and unsupervised-analysis work would build on.

## Limitations
- Blood pressure and anthropometric outliers were filtered using reasonable clinical bounds, but some borderline real patients may have been excluded along with genuine data-entry errors.
- The dataset doesn't include other well-known cardiovascular risk factors (e.g. family history, diet), so the achievable performance ceiling is bounded by what's actually recorded.
- Model complexity was kept modest (no automated hyperparameter search) — this scope covers evaluation and pipelines, not GridSearchCV tuning or unsupervised analysis, which are later topics.

## How to Run
1. Ensure `cardio_train.csv` is in the same directory as the notebook.
2. Install dependencies: `pandas`, `numpy`, `matplotlib`, `scikit-learn`.
3. Run the notebook top to bottom — no manual or hidden steps are required.
