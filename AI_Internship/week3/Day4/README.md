# Day 4 — Tree-Based Models, SVM, and k-Nearest Neighbors 🌳

## Overview
Building on Day 3's Logistic Regression classifier, this notebook explores four more classification algorithms — Decision Tree, Random Forest, Support Vector Machine (SVM), and k-Nearest Neighbors (k-NN) — all trained on the same **Titanic dataset** (`Titanic_Clean.csv`, 418 passengers) and evaluated with the same metrics, so their performance can be compared fairly rather than assuming one algorithm is universally better.

## Learning Objectives 🎯
By the end of this notebook, I learned how to:

- Explain how Decision Trees make predictions.
- Understand why Random Forests generally outperform a single decision tree.
- Describe how Support Vector Machines separate classes.
- Explain how k-Nearest Neighbors classifies new observations.
- Train and evaluate multiple classification models using Scikit-learn.
- Compare different algorithms using the same evaluation metric.
- Interpret feature importance from a Random Forest model.
- Select the most appropriate model based on objective performance rather than assumptions.

## Topics Covered 📚

**1. Decision Trees**
Rule-based, highly interpretable, but prone to overfitting if grown too deep.

**2. Random Forests & Feature Importances**
An ensemble of many decision trees that averages their votes to reduce overfitting, plus which features (`feature_importances_`) drove its predictions most.

**3. Support Vector Machines (SVM)**
Finds the decision boundary that maximizes the margin between classes; powerful in high dimensions but sensitive to feature scale.

**4. k-Nearest Neighbors (k-NN)**
Classifies a new point by majority vote among its closest training points; simple, but also sensitive to feature scale and slower as data grows.

**5. Comparing Models Fairly**
Trained all four models on the identical train/test split and compared them on Accuracy, Precision, Recall, and F1-score in one table, instead of assuming any one algorithm wins by default.

## Hands-On Lab 🧪
- Trained a Decision Tree, Random Forest, SVM, and k-NN on the same train/test split.
- Evaluated all four with Accuracy, Precision, Recall, and F1-score in one comparison table.
- Reported and interpreted the Random Forest's top feature importances.
- Identified the best-performing model(s) and explained the result in Markdown.

## Key Findings 📊
| Model | Accuracy | Precision | Recall | F1-score |
|---|---|---|---|---|
| Decision Tree | 1.000 | 1.000 | 1.000 | 1.000 |
| Random Forest | 1.000 | 1.000 | 1.000 | 1.000 |
| k-Nearest Neighbors | 0.679 | 0.652 | 0.441 | 0.526 |
| Support Vector Machine | 0.607 | 0.667 | 0.059 | 0.108 |

- **Decision Tree and Random Forest tied exactly** at a perfect F1-score of 1.000 — as with Day 3's Logistic Regression, this reflects a known quirk of this specific Titanic test file (its `Survived` labels become close to perfectly separable once `Sex` is included), not proof that either model is flawless in general.
- The more generalizable finding is the **gap between model families**: SVM and k-NN performed noticeably worse (F1 = 0.108 and 0.526) than the tree-based models. Both are distance/margin-based algorithms that are sensitive to feature scale, and the features here (`Age`, `Fare`, etc.) were never scaled — a real, actionable takeaway for the next iteration.
- Selecting a "best model" by simply taking the first row of a sorted comparison table can hide exact ties — worth checking for ties explicitly rather than assuming the top row is uniquely best.

## Tools Used 🛠️
Python • Jupyter Notebook • Pandas • NumPy • Scikit-learn (tree, ensemble, svm, neighbors) • Matplotlib

## 🚀 GitHub Submission
This notebook has been completed as part of my AI & Machine Learning Internship portfolio. It demonstrates the complete workflow of comparing multiple classification algorithms using a real-world dataset, from data preparation and model training to evaluation, interpretation, and model selection. The notebook is fully reproducible and has been organized following GitHub portfolio best practices.

## Reflection
This notebook showed me that selecting a machine learning model is not about choosing the most complex algorithm, but about comparing several approaches objectively. Although each classifier uses a different learning strategy, evaluating them on the same dataset using identical metrics made it clear that every algorithm has its own strengths and limitations. The Random Forest model particularly demonstrated how combining multiple Decision Trees can improve predictive performance while reducing overfitting. Most importantly, I learned that model evaluation is just as important as model training, since selecting the best classifier should always be supported by objective evidence rather than personal preference.

## Conclusion
In this notebook, I explored four widely used classification algorithms: Decision Tree, Random Forest, Support Vector Machine, and k-Nearest Neighbors. Each model was trained using the same training dataset and evaluated using the same testing dataset to ensure a fair comparison. By analyzing Accuracy, Precision, Recall, and F1-score, I identified the models that achieved the strongest overall performance on the Titanic dataset, and found a meaningful gap between the tree-based models and the scale-sensitive SVM and k-NN classifiers. This notebook reinforced the importance of comparing multiple machine learning algorithms objectively and selecting models based on evaluation metrics rather than assumptions.
