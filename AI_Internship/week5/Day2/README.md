# 🧠 Day 2 — DBSCAN & Hierarchical Clustering

**BinX Tech • AI & Machine Learning Internship • Week 5**

## 📖 Overview

This notebook builds on Day 1's K-Means work by exploring two additional clustering approaches — **DBSCAN** (density-based) and **Hierarchical Clustering** (agglomerative, Ward linkage) — on the same Mall Customer Segmentation dataset, then compares all three methods on equal footing.

## 🎯 Learning Objectives

By the end of this notebook, I am able to:

- Explain why K-Means alone is not always sufficient for clustering.
- Run DBSCAN and interpret its clusters and noise points.
- Build and read a hierarchical clustering dendrogram, and choose a cut height.
- Compare K-Means, DBSCAN, and hierarchical clustering on the same data and justify which fits a given dataset best.

## 📌 Topics Covered

- Limitations of K-Means (fixed `k`, forced assignment, no noise concept)
- DBSCAN: `eps`, `min_samples`, and the noise label (`-1`)
- Hierarchical clustering: Ward linkage and dendrograms
- Choosing a dendrogram cut height
- Comparing clustering methods on the same standardized data

## 📊 Dataset

Same **Mall Customer Segmentation Dataset** used on Day 1 (`Mall_Customers.csv`, 200 records), reusing the identical standardized numeric features (Age, Annual Income, Spending Score) so all three methods are compared on equal footing.

## 🖥️ Hands-On Lab

1. Ran DBSCAN (`eps=0.5`, `min_samples=5`) and reported clusters and noise points.
2. Built a Ward-linkage dendrogram and chose a data-derived cut height.
3. Compared K-Means, DBSCAN, and hierarchical clustering visually and via silhouette score.
4. Determined which method best fits this dataset's structure, with reasoning.

As an additional diagnostic beyond the lab requirement, I tested DBSCAN's sensitivity to `eps` across a small range (0.3–0.7) to show that the parameter choice needs justification rather than being treated as universally correct.

## 🔑 Key Findings

- **DBSCAN** (`eps=0.5`, `min_samples=5`) found **6 clusters** and flagged **60 of 200 points (30%) as noise** — a high noise rate that reflects how strongly DBSCAN's result depends on its density parameters for this dataset.
- **Hierarchical clustering** (Ward linkage), cut at height ≈9.73, produced **5 clusters** — matching Day 1's K-Means result.
- **Silhouette comparison:** all three methods were evaluated on the same standardized features; DBSCAN's score excluded noise points, since those aren't a real cluster.
- **Conclusion: K-Means is the most suitable primary method for this dataset.** The Mall Customers data forms relatively compact, interpretable groups, and Day 1's elbow/silhouette evidence already supports a 5-cluster solution. DBSCAN would be preferable if the data showed irregular shapes or meaningful outliers; hierarchical clustering remains a useful exploratory tool for viewing nested structure via the dendrogram.
- Different algorithms legitimately produced different results here — that's expected, since each defines "cluster" differently, not a sign one method is wrong.

## 🛠 Tools Used

Scikit-learn (`DBSCAN`, `KMeans`, `silhouette_score`) • SciPy (`linkage`, dendrogram) • Pandas • NumPy • Matplotlib • Jupyter Notebook

## 📤 GitHub Submission

Notebook and dataset committed to `randsaa2006-code/BinX_Internship`, under Week 5 / Day 2, alongside this README.

## 💭 Reflection

Today showed me there isn't one clustering algorithm that's automatically correct for every dataset. K-Means was straightforward and gave an interpretable five-segment solution, but it needs `k` chosen in advance and has no concept of noise. DBSCAN addressed that by labeling ambiguous points as noise instead of forcing them into a cluster, but its result depended heavily on `eps` and `min_samples` — the sensitivity check made that concrete rather than theoretical. Hierarchical clustering added a different view entirely, showing how groups nest at different similarity levels through the dendrogram.

## ✅ Conclusion

The lesson from today wasn't just learning to run three algorithms — it was learning to choose a clustering method based on data shape, noise, and the kind of structure I actually need to discover. For the Mall Customers dataset specifically, K-Means remains my primary method, with hierarchical clustering as a useful exploratory complement and DBSCAN reserved for data with genuine irregular density or outlier structure.
