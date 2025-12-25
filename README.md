# Thyroid Disease Classification – Supervised Machine Learning Project

## Overview
This project implements a complete **supervised machine learning pipeline** to classify thyroid disease conditions using a cleaned clinical dataset.  
The work follows a **project-grade ML workflow**, covering preprocessing, model training, evaluation, comparison, and final model selection.

The focus is not only on training models, but on **correct evaluation, error analysis, and justification**, as required in academic and real-world ML projects.

---

## Dataset
- **File:** `thyroid_cleaned.csv`
- **Target column:** `target` (numeric, multiclass)
- **Features:** Clinical and laboratory measurements
- **Preprocessing status:**  
  - Missing values handled  
  - Categorical features encoded  
  - Numerical features scaled  

---

## Problem Type
- **Learning type:** Supervised Learning  
- **Task:** Multiclass Classification  
- **Domain:** Medical / Healthcare  

---

## Models Implemented
The following supervised learning models were trained and evaluated:

### Linear Models
- Logistic Regression  
- Ridge Classifier  
- Lasso (L1-regularized Logistic Regression)

### Instance-Based
- K-Nearest Neighbors (KNN)

### Margin-Based
- Support Vector Machine (SVM)

### Tree-Based
- Decision Tree

### Probabilistic
- Naive Bayes (Gaussian)

### Ensemble Models
- Random Forest  
- Gradient Boosting  

---

## Preprocessing Pipeline
A unified preprocessing pipeline is used for all models to prevent data leakage and ensure consistency.

- **Numerical features:** StandardScaler  
- **Categorical features:** OneHotEncoder  
- **Tool:** `ColumnTransformer` + `Pipeline`

This ensures all models receive a fully numeric feature matrix.

---

## Evaluation Metrics
Because this is a **medical classification problem**, multiple metrics are used:

- Accuracy  
- Precision (weighted)  
- Recall (weighted)  
- F1-score (**primary metric**)  
- ROC-AUC (multiclass, OvR strategy)  
- Log Loss  
- Confusion Matrix  

**Why F1-score?**  
It balances precision and recall, making it more reliable than accuracy when class imbalance and medical risk are present.

---

## Model Comparison
All model results are aggregated into a single comparison table (`results_df`), enabling:

- Metric-based ranking  
- Visual comparison  
- Objective model selection  

Models are ranked primarily by **F1-score**, with ROC-AUC used as a secondary metric.

---

## Final Model Selection
The final model is chosen based on:
- Highest F1-score on the test set  
- Stable generalization performance  
- Acceptable bias–variance tradeoff  

Ensemble models (Random Forest / Gradient Boosting) typically outperform single learners, while linear models provide strong interpretable baselines.

---

## Error Analysis
- Confusion matrices are analyzed for the selected model  
- Misclassification patterns are inspected  
- Special attention is given to clinically similar classes  

This step explains *how* and *why* the model fails, not just how well it performs.

---

## Interpretability
- **Linear models:** Coefficient analysis  
- **Tree / Ensemble models:** Feature importance ranking  

This provides insight into which clinical features most influence predictions.

---

## Validation Strategy
- Train/Test split with stratification  
- No data leakage (preprocessing inside pipelines)  
- Metrics computed strictly on unseen test data  

---

## Conclusion
This project demonstrates a **complete supervised machine learning workflow**, from cleaned data to justified model selection.  
It is suitable for academic submission, portfolio presentation, or as a baseline for production-grade medical ML systems.