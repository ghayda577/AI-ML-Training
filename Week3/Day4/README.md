# Day 4 — Trees, Forests, SVMs & k-NN

## Overview

This task focused on training and comparing different classification models using Scikit-learn.

The objective was to understand how Decision Trees, Random Forests, Support Vector Machines (SVM), and k-Nearest Neighbors (k-NN) work, evaluate their performance using the same metric, and select the best-performing model for the dataset.

## Learning Objectives

- Train and evaluate Decision Tree and Random Forest classifiers.
- Understand how SVM and k-NN classifiers make predictions.
- Compare multiple classification models fairly using the same train/test split.
- Evaluate classification models using the F1-score metric.
- Analyze Random Forest feature importances.
- Select the best-performing model based on evaluation results.

## Topics Covered

- Decision Trees
- Random Forests
- Support Vector Machines (SVM)
- k-Nearest Neighbors (k-NN)
- Model Training (`fit`)
- Model Prediction (`predict`)
- Classification Evaluation:
  - F1-score
- Model Comparison
- Feature Importance Analysis
- Best Model Selection

# Hands-On Lab

The Titanic dataset was used to train and evaluate multiple classification models.

The following tasks were completed:

## 1. Dataset Preparation

- Prepared the dataset for classification.
- Separated the data into features (`X`) and target variable (`y`).
- Ensured the dataset was ready for model training.

## 2. Train/Test Split

- Split the dataset into training and testing sets.
- Used the same train/test split for all models to ensure a fair comparison.

## 3. Model Training

Four classification models were trained:

### Decision Tree

- Trained a Decision Tree classifier.
- Controlled the tree depth to reduce overfitting.
- Generated predictions on the test dataset.

### Random Forest

- Trained an ensemble model containing multiple decision trees.
- Used multiple trees to improve performance and reduce overfitting.
- Extracted feature importance values to understand feature contributions.

### Support Vector Machine (SVM)

- Trained an SVM classifier to find the optimal decision boundary between classes.
- Generated predictions using the trained model.

### k-Nearest Neighbors (k-NN)

- Trained a KNN classifier based on similarity between data points.
- Predicted classes using the nearest neighbors.

## 4. Model Evaluation

- Generated predictions for all trained models.
- Calculated the F1-score for each classifier.
- Compared model performance using the same evaluation metric.
- Collected all results into one comparison table.

## 5. Feature Importance Analysis

- Extracted feature importance scores from the Random Forest model.
- Ranked features based on their contribution to predictions.
- Interpreted the most influential features affecting the model decisions.

## 6. Model Comparison and Selection

- Compared the performance of all classification models.
- Identified the best-performing model based on the F1-score.
- Explained why the selected model achieved better results compared with the other models.

## Example Workflow

```python
from sklearn.ensemble import RandomForestClassifier

model = RandomForestClassifier(
    n_estimators=100,
    random_state=42
)

model.fit(X_train, y_train)

predictions = model.predict(X_test)
```

## Evaluation Metric

### F1-score

The F1-score was used to evaluate the performance of the classification models.

It combines precision and recall into a single metric, providing a balance between correctly identifying positive cases and avoiding false predictions.

Formula:

```
F1-score = 2 × (Precision × Recall) / (Precision + Recall)
```

## Tools Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Jupyter Notebook

## Conclusion

This task introduced the workflow of training, evaluating, and comparing different classification algorithms.

The results demonstrated the differences between tree-based models, SVM, and k-NN classifiers. Random Forest achieved the best performance on this dataset, and feature importance analysis helped identify the most influential features affecting the predictions.

This task highlighted the importance of comparing multiple models using the same evaluation metric before selecting the final model.