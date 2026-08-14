# Day 3 — Logistic Regression & Classification Metrics

## Overview

This task focused on building a **Logistic Regression** classification model using Scikit-learn to predict passenger survival.

The objective was to understand classification workflow, generate predictions and probabilities, and evaluate model performance using different classification metrics.

## Learning Objectives

- Train a Logistic Regression classifier using Scikit-learn.
- Generate predictions and class probabilities.
- Understand the limitations of accuracy as an evaluation metric.
- Interpret the confusion matrix.
- Calculate and analyze precision, recall, F1-score, and AUC-ROC.
- Understand the trade-off between precision and recall.

## Topics Covered

- Logistic Regression
- Classification Workflow
- Model Training (`fit`)
- Model Prediction (`predict`)
- Class Probabilities (`predict_proba`)
- Confusion Matrix
  - True Positive (TP)
  - True Negative (TN)
  - False Positive (FP)
  - False Negative (FN)
- Classification Metrics
  - Precision
  - Recall
  - F1-score
- ROC Curve and AUC-ROC

## Hands-On Lab

The Titanic dataset was used to build and evaluate a Logistic Regression classifier.

The following steps were completed:

1. **Data Preparation**
   - Loaded the Titanic dataset.
   - Selected relevant features.
   - Removed unnecessary columns.
   - Handled missing values.
   - Encoded categorical features.

2. **Train/Test Split**
   - Split the dataset into training and testing sets using an 80/20 ratio.
   - Used `random_state=42` for reproducibility.

3. **Model Training**
   - Created and trained a Logistic Regression classifier.
   - Generated predictions and class probabilities.

4. **Model Evaluation**
   - Created a confusion matrix.
   - Calculated precision, recall, and F1-score.
   - Analyzed the importance of recall for survival prediction.
   - Computed the AUC-ROC score.

## Results

The Logistic Regression model achieved:

- Accuracy: 80%
- Precision (Survival class): 77%
- Recall (Survival class): 73%
- F1-score (Survival class): 75%
- AUC-ROC Score: 0.88

The results indicate that the model has good classification performance and can effectively distinguish between survivors and non-survivors.

## Tools Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Jupyter Notebook

## Conclusion

This task introduced the complete workflow of a classification model, from data preprocessing and training to performance evaluation.

The results demonstrated the importance of using metrics such as precision, recall, F1-score, and AUC-ROC instead of relying only on accuracy to evaluate classification models.
