# Day 5 — Scikit-learn Pipelines & Tuned Mini-Project

## Overview

This notebook focuses on building a complete, leak-free machine learning workflow for stroke prediction using Scikit-learn Pipelines.

The workflow combines feature engineering, preprocessing, Random Forest classification, and hyperparameter tuning into a single pipeline. A `ColumnTransformer` is used to apply different preprocessing steps to numerical and categorical features.

The final pipeline is tuned using `GridSearchCV` with stratified 5-fold cross-validation and evaluated once on a held-out test set.

## Learning Objectives

- Build a Scikit-learn `Pipeline` that combines preprocessing and modeling.
- Use `ColumnTransformer` to handle numerical and categorical features differently.
- Apply preprocessing without data leakage.
- Tune the complete pipeline using `GridSearchCV`.
- Evaluate the final model correctly on a held-out test set.
- Compare the tuned model with a majority-class baseline.

## Dataset

The project uses the healthcare stroke prediction dataset.

The target variable is:

- `stroke` — indicates whether a patient experienced a stroke.

The dataset contains both numerical and categorical features and is highly imbalanced, making F1 score an appropriate primary evaluation metric.

## Feature Engineering

Two engineered features from Day 4 were included:

- `age_group` — groups patients into meaningful age categories.
- `health_risk_count` — counts selected risk factors including hypertension, heart disease, and smoking history.

The `id` column was removed because it is only an identifier and does not provide meaningful predictive information.

## Pipeline

The preprocessing and model are combined into a single Scikit-learn Pipeline.

### Numerical Features

- Missing values are replaced using median imputation.
- Features are standardized using `StandardScaler`.

### Categorical Features

- Missing values are replaced using the most frequent category.
- Categories are converted using `OneHotEncoder`.
- `handle_unknown="ignore"` allows the pipeline to handle unseen categories safely.

The preprocessing steps are fitted within the training data and cross-validation folds, preventing data leakage.

## Model and Hyperparameter Tuning

A `RandomForestClassifier` with `class_weight="balanced_subsample"` is used to account for class imbalance.

`GridSearchCV` with stratified 5-fold cross-validation is used to tune:

- `n_estimators`
- `max_depth`
- `min_samples_split`
- `min_samples_leaf`

The F1 score is used as the optimization metric because detecting the minority stroke class is more important than relying only on accuracy.

## Train/Test Evaluation

The dataset is split into:

- 80% training data
- 20% held-out test data

The training set is used for preprocessing, cross-validation, and hyperparameter tuning.

The held-out test set is used only once for the final evaluation.

## Results

The best hyperparameter configuration selected by `GridSearchCV` was:

- `n_estimators = 100`
- `max_depth = 10`
- `min_samples_split = 2`
- `min_samples_leaf = 2`

The best cross-validated F1 score was approximately **0.182**.

On the held-out test set:

| Model | F1 Score |
| --- | ---: |
| Baseline | 0.000 |
| Tuned Pipeline | 0.240 |

The tuned pipeline achieved an F1 score of **0.240**, compared with **0.000** for the majority-class baseline.

The tuned pipeline also achieved a stroke recall of **0.300**, correctly identifying 30% of the actual stroke cases in the test set.

## Conclusion

The project demonstrates how Scikit-learn Pipelines can combine preprocessing and modeling into a single leak-free workflow.

Using `ColumnTransformer`, different preprocessing strategies were applied to numerical and categorical features. The complete pipeline was then tuned using `GridSearchCV` with stratified 5-fold cross-validation.

The final tuned pipeline outperformed the majority-class baseline on the held-out test set, achieving an F1 score of **0.240** compared with **0.000** for the baseline.

This workflow provides a professional and reproducible structure for building machine learning models while avoiding data leakage.
