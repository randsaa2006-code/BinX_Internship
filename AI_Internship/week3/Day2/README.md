# Day 2 — Linear Regression with Scikit-learn 📈

## Overview
Building on Day 1's supervised learning workflow, this notebook introduces the first actual predictive model: **Linear Regression**. Unlike Day 1's classification task (Titanic survival), regression estimates a continuous numerical value — here, `median_house_value` from the **California Housing dataset** (`California_Housing.csv`, 20,640 observations). The notebook walks through the full pipeline: exploring the dataset, understanding the intuition behind Linear Regression, training and predicting with Scikit-learn, interpreting the model's coefficients, and evaluating it against a baseline.

## Learning Objectives 🎯
By the end of this notebook, I learned how to:

- Explain how Linear Regression models continuous numerical values.
- Train a Linear Regression model using Scikit-learn.
- Generate predictions on unseen data.
- Interpret model coefficients and the intercept.
- Evaluate model performance using MAE, RMSE, and R².
- Compare the model against a simple baseline to determine whether it provides meaningful predictive value.

## Topics Covered 📚

**1. Meeting the Dataset**
Explored the California Housing dataset's structure, size, and data types, checked for missing values, and reviewed descriptive statistics before modeling.

**2. Features and Target, and the Train/Test Split**
Separated the dataset into features (X) and target (y, `median_house_value`), then split into training and testing subsets to allow honest evaluation later.

**3. What is Linear Regression?**
Recapped supervised learning from Day 1, then introduced Linear Regression's intuition (fitting the best line through the data), its equation (connecting back to the dot-product concept from Week 2), and what happens during training — finding the weights that minimize prediction error.

**4. Training and Predicting with Scikit-learn**
Instantiated a `LinearRegression` model, trained it with `.fit()`, and generated predictions with `.predict()` — followed by a direct comparison of predicted vs. actual values.

**5. Interpreting Coefficients and Intercept**
Reviewed each feature's coefficient and the model's intercept. Found that `longitude` and `latitude` have the largest *raw* coefficient magnitudes, but `median_income` is the most practically meaningful predictor — a reminder that coefficient magnitude alone doesn't equal feature importance, especially across differently-scaled features.

**6. Regression Metrics: MAE, RMSE, R²**
Computed and interpreted all three metrics together, since each reveals something the others don't (e.g. the gap between MAE and RMSE flags districts with unusually large errors).

**7. Comparing Against a Baseline**
Checked the model's RMSE against a baseline that always predicts the mean `median_house_value`, to confirm the model is actually adding value rather than just guessing the average.

## Hands-On Lab 🧪
- Loaded `California_Housing.csv` and trained a `LinearRegression` model on the train/test split.
- Reported the model's coefficients and identified the strongest predictor.
- Evaluated the model with MAE, RMSE, and R² on the test set.
- Compared the RMSE against a mean-prediction baseline and confirmed the model adds real value.
- Documented the interpretation of all results in Markdown.

## Key Findings 📊
- The model's predictions are off by about **$51,300 on average (MAE)**; the higher **RMSE ($70,300)** shows a subset of districts have much larger errors.
- **R² ≈ 0.62** — the model explains about 62% of the variance in house values; the rest is driven by factors not used here (e.g. `ocean_proximity`).
- `longitude` and `latitude` have the largest raw coefficients, but `median_income` is the most meaningful predictor in practice, since income has the clearest real-world relationship with house price.
- The model's RMSE is **~39% lower** than a baseline that just predicts the mean — confirming it has learned a real, usable relationship from the data.

## Tools Used 🛠️
Python • Jupyter Notebook • Pandas • NumPy • Scikit-learn

## 🚀 GitHub Submission
This notebook has been completed as part of my AI & Machine Learning internship portfolio. It demonstrates the complete workflow of building a Linear Regression model, including data preparation, model training, prediction, performance evaluation, coefficient interpretation, and comparison against a baseline model. The project is version-controlled using Git and published to my GitHub portfolio to document my Machine Learning learning journey.

## Reflection
This notebook was my first experience training an actual predictive model rather than just preparing data for one. Fitting a `LinearRegression` model on the California housing data and seeing real coefficients come out — like `median_income` having a strong practical relationship with house value — made the abstract idea of "the model learns weights" concrete for the first time. Comparing MAE, RMSE, and R² together, instead of looking at just one metric, also showed me why a single number can be misleading: the gap between MAE and RMSE here revealed that some districts are much harder to predict than others, which a single accuracy figure would have hidden. Checking the model against a mean-prediction baseline was the most valuable step, since it turned "the R² is 0.62" from an abstract number into a clear, comparative statement that the model is actually adding value.

## Conclusion
In this notebook, I trained my first Linear Regression model on the California housing dataset to predict `median_house_value`. I interpreted the model's coefficients and identified `median_income` as the strongest predictor, evaluated the model using MAE, RMSE, and R², and confirmed that it meaningfully outperforms a simple mean-prediction baseline. These skills — training a regression model, interpreting its coefficients, and validating its usefulness against a baseline — form the foundation for evaluating any regression model going forward, regardless of how complex it becomes.
