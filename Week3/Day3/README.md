````markdown
# Day 3 — Logistic Regression & Classification Metrics

## Overview

This task focused on building a **Logistic Regression** classification model using Scikit-learn to predict passenger survival.

The objective was to understand how classification models work, generate class probabilities, and evaluate performance using different classification metrics.

## Learning Objectives

- Train a Logistic Regression classifier using Scikit-learn.
- Generate predictions and class probabilities.
- Understand why accuracy alone may be misleading.
- Interpret the confusion matrix.
- Evaluate the model using precision, recall, F1-score, and AUC-ROC.
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

The following tasks were completed:

1. **Dataset Preparation**
   - Loaded the Titanic dataset.
   - Selected relevant features.
   - Removed unnecessary columns.
   - Handled missing values.
   - Encoded categorical variables.

2. **Train/Test Split**
   - Split the dataset into training and testing sets using an 80/20 ratio.
   - Used `random_state=42` to ensure reproducible results.

3. **Model Training**
   - Created a `LogisticRegression` model.
   - Trained the model using the training dataset.

4. **Prediction**
   - Generated class predictions.
   - Generated class probabilities using `predict_proba()`.

5. **Model Evaluation**
   - Created a confusion matrix to analyze prediction errors.
   - Calculated precision, recall, and F1-score using `classification_report`.
   - Determined the importance of recall over precision for the survival prediction problem.
   - Computed the AUC-ROC score and interpreted the model performance.

## Example Workflow

```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression(max_iter=1000)

model.fit(X_train, y_train)

predictions = model.predict(X_test)

probabilities = model.predict_proba(X_test)
````

## Evaluation Metrics

The model was evaluated using:

* Confusion Matrix
* Precision
* Recall
* F1-score
* AUC-ROC

The Logistic Regression model achieved an AUC-ROC score of approximately **0.88**, indicating good ability to distinguish between survivors and non-survivors.

## Tools Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Jupyter Notebook

## Conclusion

This task introduced the complete workflow of a classification model, from preparing the dataset and training the model to evaluating its performance using classification metrics.

The results demonstrated the importance of using metrics such as precision, recall, F1-score, and AUC-ROC instead of relying only on accuracy when evaluating classification models.
