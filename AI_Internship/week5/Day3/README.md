# 🧠 Day 3 — Dimensionality Reduction with PCA

**BinX Tech • AI & Machine Learning Internship • Week 5**

## 📖 Overview

This notebook covers dimensionality reduction using **Principal Component Analysis (PCA)**, applied to the Digits dataset — 1,797 handwritten-digit samples, each with 64 numeric pixel features. Unlike Day 1–2's clustering work, the goal here isn't grouping — it's compressing a genuinely high-dimensional dataset while keeping as much information as possible.

## 🎯 Learning Objectives

By the end of this notebook, I am able to:

- Explain the curse of dimensionality and why reduction helps.
- Apply PCA to reduce a dataset's dimensions.
- Interpret explained variance and choose how many components to keep.

## 📌 Topics Covered

- The curse of dimensionality
- What PCA does: principal components and variance
- Explained variance ratio
- Choosing the number of components (95% variance rule)
- When (and when not) to use PCA

## 📊 Dataset

**Digits dataset**, provided as `digits_dataset.csv` — 1,797 samples, 64 numeric pixel features (8×8 handwritten-digit images) plus a `target` column (digits 0–9). Verified: no missing values, no infinite values, all ten classes present — genuinely high-dimensional, which is what makes it a meaningful PCA case rather than a toy example.

## 🖥️ Hands-On Lab

1. Scaled the 64-feature dataset with `StandardScaler` (required before PCA, since it's variance-based).
2. Fit PCA on all components and plotted cumulative explained variance.
3. Chose the number of components retaining ≥95% of variance, with justification.
4. Reduced the data to 2 components and produced a 2D scatter plot colored by digit class.
5. Documented what the reduction preserved and what it cost.

## 🔬 Beyond the Requirement

- **Component loadings:** inspected which original pixel features contribute most to PC1 and PC2, connecting the abstract components back to the original feature space.
- **Reconstruction visualization:** rebuilt digit images from the 40-component (95% variance) and 2-component representations via `inverse_transform`, and compared them visually and by MSE against the original. This made the variance trade-off concrete rather than just a percentage on a plot.
- **Practical downstream impact:** trained and timed a KNN classifier on the original 64 features versus the 40 PCA components, using an identical train/test split for both, to test whether the reduction helps or hurts a real task — not just in theory.

## 🔑 Key Findings

- **95% variance retained at 40 components** (down from 64 — a 24-dimension reduction).
- **Reconstruction MSE:** 1.08 (40 components) vs. 14.05 (2 components) — the 2-component reconstruction has **13× the error**, making the earlier "95% vs. ~22% variance" comparison tangible rather than abstract.
- **2D projection retains only ~21.6% of total variance** — useful for visualization, but expected to lose real structure, which the reconstructed image confirmed visually (recognizable digit shape, blurred detail).
- **KNN comparison:** the 40-component representation matched or slightly **improved** accuracy (0.975 vs. 0.967) versus the full 64 features, while cutting prediction time by roughly **11×** (0.0043s vs. 0.0489s) — PCA removed redundant/correlated pixel information without hurting a distance-based model, and made it faster.
- All sanity checks passed: PCA was fit on `X` only (target `y` reserved purely for visualization/coloring, no leakage into the transformation).

## 🛠 Tools Used

Scikit-learn (`PCA`, `StandardScaler`, `KNeighborsClassifier`) • Pandas • NumPy • Matplotlib • Jupyter Notebook

## 📤 GitHub Submission

Notebook and dataset committed to `randsaa2006-code/BinX_Internship`, under Week 5 / Day 3, alongside this README.

## 💭 Reflection

This day reframed what "95% variance retained" actually means. As a number on a cumulative-variance plot, it's abstract; reconstructing an actual digit from the reduced representation made the trade-off visible, and comparing a real KNN classifier's accuracy and speed on both representations made the benefit concrete instead of theoretical. The most useful realization was that dimensionality reduction isn't only a compression exercise — done well, it can actively improve a downstream model by removing redundant, correlated information, not just shrink it.

## ✅ Conclusion

Today I learned the PCA workflow end to end: scale first, fit and inspect cumulative explained variance, choose a component count with a justified threshold, and interpret what's preserved versus lost — both numerically and by testing it against a real model. Reducing from 64 to 40 dimensions kept 95% of the variance, produced visually faithful reconstructions, and even improved a KNN classifier's accuracy while making it substantially faster — a concrete demonstration of why dimensionality reduction is a genuinely useful tool, not just a theoretical exercise.
