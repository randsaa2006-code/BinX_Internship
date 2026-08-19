# 🧠 Day 4 — t-SNE & Anomaly Detection

**BinX Tech • AI & Machine Learning Internship • Week 5**

## 📖 Overview

This notebook covers two connected unsupervised topics: **t-SNE** for visualizing high-dimensional data through local neighborhoods (as opposed to PCA's global variance view), and **anomaly detection** with Isolation Forest. Both build directly on the same Digits dataset used on Day 3, keeping the visualization comparison meaningful rather than arbitrary.

## 🎯 Learning Objectives

By the end of this notebook, I am able to:

- Use t-SNE to visualize high-dimensional data and distinguish it from PCA.
- Explain what anomaly detection is and why it is often unsupervised.
- Detect anomalies with Isolation Forest and interpret the flagged points.

## 📌 Topics Covered

- t-SNE for local-structure visualization
- PCA vs. t-SNE: when to use each
- What anomaly detection is
- Isolation Forest and the contamination parameter
- Anomaly detection and clustering overlap

## 📊 Dataset

Same **Digits dataset** (`digits_dataset.csv`) used on Day 3 — 1,797 samples, 64 pixel features — reused deliberately so the t-SNE vs. PCA comparison in Step 2 is a genuine apples-to-apples comparison, not two different datasets.

## 🖥️ Hands-On Lab

0. Recreated Day 1's K-Means clustering (`k=3`) on the scaled Digits data, purely to provide labels for coloring the visualizations.
1. Applied t-SNE to reduce the 64 features to 2D and plotted it, colored by cluster.
2. Compared the t-SNE plot to a fresh 2D PCA plot on the same data, noting what each reveals.
3. Ran Isolation Forest (`contamination=0.05`) and reported the number of flagged anomalies.
4. Inspected two flagged points individually and hypothesized why each was flagged.

## 🔬 Beyond the Requirement

Compared the anomaly rate across the three K-Means clusters, since anomaly detection and clustering conceptually overlap (a point in a sparse region can look both like an outlier and like a weak cluster fit). Cluster 0 had a notably higher anomaly rate (7.1%) than Cluster 2 (2.6%), suggesting the clusters aren't uniformly "tight" — some capture more heterogeneous digit-writing styles than others.

## 🔑 Key Findings

- **t-SNE vs. PCA:** PCA's 2D projection retained only 21.60% of total variance and organizes points by global variance along interpretable axes; t-SNE has no meaningful axes but revealed the ten digit classes as far more visually separated and locally coherent groups — showing structure PCA's linear, global view compresses away.
- **Isolation Forest flagged 90 of 1,797 points (5.0083%)** — matching the `contamination=0.05` setting almost exactly, confirming the parameter was applied correctly.
- **Anomalies are model-defined, not automatically errors:** inspecting two flagged points suggested unusual stroke thickness, shape, or pixel intensity relative to the majority — atypical handwriting, not necessarily corrupted data.
- **Anomaly rate varies by K-Means cluster** (7.1% / 5.0% / 2.6% across clusters 0/1/2), showing clustering and anomaly detection surface related but not identical structure.
- All sanity checks passed: t-SNE output shape correct, one Isolation Forest prediction per sample, `-1`/`1` convention verified, flagged proportion consistent with `contamination`, and target labels never used as model features.

## 🛠 Tools Used

Scikit-learn (`TSNE`, `PCA`, `KMeans`, `IsolationForest`) • Pandas • NumPy • Matplotlib • Jupyter Notebook

## 📤 GitHub Submission

Notebook and dataset committed to `randsaa2006-code/BinX_Internship`, under Week 5 / Day 4, alongside this README.

## 💭 Reflection

Today clarified that t-SNE and PCA are not interchangeable, even though both reduce to 2D. PCA gave me a global, mathematically interpretable view; t-SNE gave me a much clearer visual separation of the ten digit classes, but its axes carry no direct meaning and its output would change with different settings — it's for looking, not for feeding into another model. The anomaly detection side taught me something I hadn't fully internalized before: an "anomaly" is a statement about the model's learned distribution, not a factual claim that a data point is wrong. That distinction matters before treating any flagged point as an error worth removing.

## ✅ Conclusion

I built the full t-SNE and Isolation Forest workflow, compared t-SNE against PCA on the same data to see what each actually reveals, and confirmed Isolation Forest's flagged proportion matched its configured contamination rate almost exactly. Extending the analysis to compare anomaly rates across K-Means clusters showed these unsupervised techniques surface overlapping but distinct structure — a theme that connects Day 1 through Day 4 of this week's work.
