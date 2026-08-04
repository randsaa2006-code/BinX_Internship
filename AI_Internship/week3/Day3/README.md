# Day 3 — Logistic Regression & Classification Metrics 📈

## Overview
Building on Day 2's regression work, this notebook shifts into **classification** — predicting which category an observation belongs to rather than a continuous number. Using the **Titanic dataset** (`Titanic_Clean.csv`, 418 passengers), the notebook trains a first Logistic Regression classifier, walks through the full workflow from data preprocessing to prediction, and evaluates the model with multiple classification metrics rather than relying on accuracy alone.

## Learning Objectives 🎯
By the end of this notebook, I learned how to:

- Explain the difference between regression and classification.
- Understand how Logistic Regression predicts probabilities.
- Train a Logistic Regression classifier using Scikit-learn.
- Generate class predictions and class probabilities.
- Interpret a Confusion Matrix.
- Evaluate a classifier using Accuracy, Precision, Recall, F1-score, and AUC-ROC.
- Explain why accuracy alone is not always a reliable evaluation metric.

## Topics Covered 📚

**1. Meeting the Dataset & Preprocessing**
Loaded the cleaned Titanic dataset, dropped non-predictive columns (`PassengerId`, `Name`, `Ticket`, `Cabin`), and encoded `Sex` and `Embarked` into numeric values so the model could use them.

**2. From Regression to Classification**
Why Linear Regression isn't suited to predicting categories, and how Logistic Regression solves this with the sigmoid function, which converts a weighted sum into a probability between 0 and 1.

**3. Decision Threshold, Features & Target, Train/Test Split**
Split the dataset into `X` (7 features) and `y` (`Survived`), then into training and test sets (80/20, `random_state=42`).

**4. Model Training and Predictions**
Instantiated, trained, and used the model to generate both class predictions (`.predict()`) and class probabilities (`.predict_proba()`), then compared predictions against actual outcomes.

**5. Model Evaluation**
Computed Accuracy, then moved into the Confusion Matrix, Precision, Recall, F1-score, and finally the ROC curve and AUC — building the case for why no single metric is enough.

## Hands-On Lab 🧪
- Trained a `LogisticRegression` model on the Titanic dataset.
- Generated predictions and produced the confusion matrix.
- Evaluated the model with precision, recall, and F1-score via `classification_report`.
- Decided recall matters slightly more for this problem (missing an actual survivor is costlier than a false alarm) and justified it.
- Computed and interpreted the AUC-ROC.

## Key Findings 📊
- With `Sex`, `Pclass`, `Age`, `SibSp`, `Parch`, `Fare`, and `Embarked` as features, the model achieved a **perfect score on the test set**: 100% accuracy, a confusion matrix of `[[50, 0], [0, 34]]` (zero misclassifications), precision/recall/F1 all at 1.00, and an AUC of 1.000.
- **Important caveat:** this particular `Titanic_Clean.csv` test file is a well-known public dataset whose `Survived` labels were reconstructed from real historical passenger records rather than independently collected — and they align very closely with simple rules like "women and higher-class passengers were far more likely to survive." Once `Sex` is included as a feature, this specific file becomes close to perfectly separable, which is why the score is so clean. A perfect score here reflects a known quirk of this specific dataset, not proof that Logistic Regression will perform this well in general — a healthy point to raise with the mentor rather than present at face value.
- Recall was judged slightly more important than precision for this problem, since missing an actual survivor (false negative) is a worse mistake than a false alarm.

## Tools Used 🛠️
Python • Jupyter Notebook • Pandas • NumPy • Scikit-learn (LogisticRegression) • Matplotlib

## 🚀 GitHub Submission
This notebook has been completed as part of my AI & Machine Learning internship portfolio. It demonstrates training a Logistic Regression classifier and evaluating it with multiple metrics — accuracy, confusion matrix, precision, recall, F1-score, and AUC-ROC — rather than relying on accuracy alone. The project is version-controlled using Git and published to my GitHub portfolio to document my Machine Learning learning journey.

## Reflection
This notebook introduced my first classification model using Logistic Regression. Beyond learning how to train a classifier, I realized that evaluating classification models requires much more than simply checking Accuracy. Understanding the Confusion Matrix, Precision, Recall, F1-score, and ROC-AUC showed me that different metrics answer different questions about model performance. One of the most valuable lessons was recognizing that the importance of a metric depends on the problem itself. In some applications, identifying every positive case is more important than avoiding false alarms, while in others the opposite is true. This notebook also reinforced the importance of interpreting model outputs rather than only generating predictions, helping me better understand how Machine Learning models make classification decisions.

## Conclusion
In this notebook, I built my first Logistic Regression classifier using the Titanic dataset. I explored the complete Machine Learning workflow, beginning with data preparation and train-test splitting, followed by model training, prediction generation, probability estimation, and performance evaluation. The classifier was assessed using Accuracy, the Confusion Matrix, Precision, Recall, F1-score, and ROC-AUC, demonstrating that no single metric is sufficient to evaluate a classification model. These concepts establish the foundation for more advanced classification algorithms that will be explored in the following notebook, where multiple models will be trained and compared on the same dataset to understand their strengths and limitations.
