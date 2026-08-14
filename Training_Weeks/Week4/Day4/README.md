# Day 4 — Feature Engineering & Hyperparameter Tuning

## Overview

This notebook focuses on feature engineering and systematic hyperparameter tuning using a Stroke Prediction dataset.

The workflow includes creating meaningful engineered features, preprocessing numerical and categorical data, tuning a Random Forest classifier using GridSearchCV with 5-fold cross-validation, and comparing the tuned model with an untuned baseline.

## Learning Objectives

- Create meaningful engineered features and justify them.
- Apply feature transformation techniques such as binning and encoding.
- Understand the difference between model parameters and hyperparameters.
- Tune a Random Forest model systematically using GridSearchCV.
- Evaluate model performance using 5-fold cross-validation.
- Analyze the impact of engineered features and hyperparameters.

## Dataset

The dataset contains patient information and a binary `stroke` target.

The following engineered features were created:

- `age_group`: Groups patients into age categories using binning.
- `health_risk_count`: Counts selected health risk factors including hypertension, heart disease, and smoking history.

The `id` column was removed because it is an identifier and does not provide meaningful predictive information.

## Model and Preprocessing

A Random Forest classifier was used with:

- Median imputation for numerical features.
- Most-frequent imputation for categorical features.
- One-hot encoding for categorical features.
- `class_weight="balanced_subsample"` to address class imbalance.

## Hyperparameter Tuning

GridSearchCV was used with 5-fold stratified cross-validation.

The hyperparameters searched were:

- `n_estimators`
- `max_depth`
- `min_samples_split`
- `min_samples_leaf`

The best configuration was:

- `n_estimators = 200`
- `max_depth = 10`
- `min_samples_split = 5`
- `min_samples_leaf = 1`

The best cross-validated F1 score was approximately **0.202**.

## Results

The untuned Random Forest achieved a mean 5-fold F1 score of approximately **0.031**, while the tuned model achieved approximately **0.202**.

The absolute improvement in F1 was approximately **0.171**.

Among the engineered features, `health_risk_count` had the largest positive impact on the cross-validated F1 score.

Among the tested hyperparameters, `max_depth` had the greatest impact on the mean cross-validated F1 score.

## Conclusion

Feature engineering and systematic hyperparameter tuning improved the Random Forest performance on the selected F1 metric. The experiments also demonstrated how meaningful feature creation and cross-validation can help identify useful features and hyperparameter settings.