# Day 3 — Bias-Variance & Diagnosing Model Fit

## Overview

This day focuses on understanding and diagnosing model fit by distinguishing between **underfitting** and **overfitting**.

The notebook demonstrates how model complexity affects generalization and how the train-validation performance gap can be used to diagnose model behavior.

Two approaches for addressing overfitting are demonstrated:

* Reducing model complexity using `max_depth` in a Decision Tree.
* Applying regularization using Ridge (L2) and Lasso (L1) with Polynomial Regression.

## Learning Objectives

* Distinguish underfitting from overfitting based on their symptoms.
* Explain the bias-variance trade-off and its role in model tuning.
* Diagnose model fit using the train-validation score gap.
* Understand how reducing model complexity can reduce overfitting.
* Understand how Ridge and Lasso regularization can control model complexity.

## Key Topics

* Underfitting (High Bias)
* Overfitting (High Variance)
* Bias-Variance Trade-off
* Train vs. Validation Performance Gap
* Model Complexity
* Ridge Regularization (L2)
* Lasso Regularization (L1)

## Dataset

The **Diabetes dataset** provided by Scikit-learn is used for the experiments.

The dataset contains:

* 442 samples
* 10 numerical features
* 1 continuous target variable

The dataset is used as a regression problem and model performance is evaluated using the **R² score**.

## Experiments

### 1. Deliberate Overfitting

A Decision Tree Regressor without a maximum depth limit is used to create a highly complex model.

The model achieves a very high training score while performing considerably worse on the validation set, producing a large train-validation gap.

This demonstrates **overfitting (high variance)**.

### 2. Deliberate Underfitting

A Decision Tree with a very small `max_depth` is used to create an overly simple model.

Both training and validation performance are relatively low, demonstrating **underfitting (high bias)**.

### 3. Reducing Model Complexity

The overfitted Decision Tree is simplified by limiting its maximum depth.

This reduces the model's complexity, decreases the train-validation gap, and improves validation performance.

### 4. Polynomial Regression Baseline

Polynomial Regression is used to introduce additional model complexity.

The unregularized polynomial model provides a baseline for evaluating the effect of regularization.

### 5. Ridge Regularization

Ridge Regression (L2 regularization) is applied to the Polynomial Regression model.

Ridge penalizes large coefficients and helps control model complexity, reducing the difference between training and validation performance.

### 6. Lasso Regularization

Lasso Regression (L1 regularization) is also applied to the Polynomial Regression model.

Lasso penalizes model coefficients and can shrink some coefficients toward zero, helping control model complexity and potentially improving generalization.

## Model Fit Diagnosis

The train-validation gap is used as the main diagnostic signal:

| Training Performance | Validation Performance | Diagnosis             |
| -------------------- | ---------------------- | --------------------- |
| Low                  | Low                    | Underfitting          |
| High                 | Much Lower             | Overfitting           |
| Similar              | Similar                | Better Generalization |

A large gap between training and validation performance can indicate that the model is fitting the training data too closely.

A small gap indicates that the model performs more similarly on training and validation data.

## Final Evaluation

After comparing the models using the validation set, the best-performing model is selected and evaluated once on the previously unseen test set.

The test set is kept separate during model development to provide a final estimate of the model's generalization performance.

## Conclusion

The experiments demonstrate the **bias-variance trade-off** and show how model complexity affects model generalization.

The results demonstrate that:

* An overly complex model can overfit the training data.
* An overly simple model can underfit the data.
* Reducing model complexity can help control overfitting.
* Ridge and Lasso regularization can reduce the effects of excessive complexity in linear models.
* Comparing training and validation performance provides a practical way to diagnose model fit.
