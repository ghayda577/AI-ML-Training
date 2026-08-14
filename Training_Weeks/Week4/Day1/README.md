# Day 1 — Train / Validation / Test Splits

## Overview

This task focuses on building a proper three-way data split using Training, Validation, and Test sets.

The main goal is to understand the role of each dataset, use the validation set for model development and hyperparameter tuning, and keep the test set completely untouched until the final evaluation.

## Learning Objectives

- Explain why a validation set is needed in addition to a test set.
- Create a correct three-way split using Scikit-learn.
- Explain why tuning against the test set produces misleading results.
- Understand the importance of keeping the test set untouched during model development.

## Dataset

The **Stroke Prediction Dataset** was used for this task.

The dataset contains patient information and a binary target variable, `stroke`, indicating whether a patient experienced a stroke.

The `id` column was removed because it is only an identifier and does not provide meaningful predictive information.

## Three-Way Data Split

The dataset was divided into three subsets:

| Dataset | Proportion | Purpose |
|---|---:|---|
| Training | 60% | Train the machine learning model |
| Validation | 20% | Tune the model and select hyperparameters |
| Test | 20% | Final evaluation on unseen data |

A fixed `random_state=42` was used to make the split reproducible.

The split was created using two calls to `train_test_split`:

1. First, 20% of the data was held out as the final test set.
2. The remaining 80% was split into 75% training and 25% validation data.

This results in an overall split of approximately **60% Training / 20% Validation / 20% Test**.

## Preprocessing

A preprocessing pipeline was created using `ColumnTransformer` and `Pipeline`.

### Numerical Features

The numerical features were processed using:

- Median imputation for missing values.
- Standard scaling using `StandardScaler`.

### Categorical Features

The categorical features were processed using:

- Most-frequent imputation for missing values.
- One-hot encoding using `OneHotEncoder`.

The preprocessing steps are part of the machine learning pipeline, so they are fitted only on the training data during model training. This helps prevent data leakage from the validation and test sets.

## Model

A **Random Forest Classifier** was used for the classification task.

The `n_estimators` hyperparameter was selected for tuning. This parameter controls the number of decision trees in the Random Forest.

The following values were tested:

- `50`
- `100`
- `200`
- `300`

Each model was trained using the training set and evaluated using the validation set.

The test set was not used during this process.

## Validation Results

All tested values of `n_estimators` achieved the same validation accuracy:

| `n_estimators` | Validation Accuracy |
|---:|---:|
| 50 | 95.11% |
| 100 | 95.11% |
| 200 | 95.11% |
| 300 | 95.11% |

Changing the number of trees did not change the validation accuracy. This can happen when additional trees do not provide enough new information to change the model's predictions on the validation set.

Since all tested values performed equally on the validation set, `n_estimators = 100` was selected for the final model as a reasonable balance between model complexity and training time.

This choice was based only on the validation results, and the test set was not used during the selection process.

## Final Test Evaluation

After selecting `n_estimators = 100`, the final Random Forest model was trained on the training set.

The test set was then used **exactly once** to obtain the final performance estimate.

### Results

- **Validation Accuracy:** 95.11%
- **Final Test Accuracy:** 94.62%

The final test accuracy was slightly lower than the validation accuracy. This is expected because the test set contains data that was not used during model development or hyperparameter tuning.

The small difference between the validation and test accuracy indicates relatively consistent performance on unseen data.

## Why the Test Set Should Not Be Used for Tuning

The test set should only be used for the final evaluation.

If the test set were repeatedly used during model tuning, information from the test data would influence decisions such as hyperparameter selection, model selection, or feature selection.

This could cause the development process to become overfitted to the specific test set. As a result, the final test score would no longer provide an honest estimate of how the model performs on completely unseen data.

Therefore, the validation set was used for tuning, while the test set was kept untouched until the final evaluation.

## Key Takeaways

- A three-way split separates model training, model development, and final evaluation.
- The training set is used to fit the model.
- The validation set is used to tune hyperparameters and make development decisions.
- The test set should remain untouched until the final evaluation.
- Tuning against the test set can lead to overly optimistic and misleading performance estimates.
- A fixed `random_state` makes the data split reproducible.
- A single validation set can still be affected by sampling variation, which motivates the use of cross-validation for more reliable model evaluation.

## Hands-On Lab Requirements

The following requirements were completed:

- [x] Created a 60/20/20 train/validation/test split.
- [x] Used a fixed `random_state`.
- [x] Trained a Random Forest model on the training set.
- [x] Tuned the `n_estimators` hyperparameter using the validation set only.
- [x] Kept the test set untouched during tuning.
- [x] Evaluated the final model on the test set exactly once.
- [x] Reported the final test accuracy.
- [x] Explained why tuning against the test set produces misleading results.