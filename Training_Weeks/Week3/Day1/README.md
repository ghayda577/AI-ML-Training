# Day 1 — Supervised Learning Concepts & Scikit-learn API

## Overview

This task introduces the fundamentals of Supervised Learning and the standard workflow used in Scikit-learn.

The goal was to understand how models learn from labeled data, separate features from targets, and prepare a dataset for Machine Learning modeling.

## Learning Objectives

- Understand supervised learning and how models learn from labeled examples.
- Differentiate between regression and classification problems.
- Separate features (X) from the target (y).
- Perform a train/test split and understand the importance of evaluating on unseen data.
- Learn the basic Scikit-learn model workflow.

## Topics Covered

- Supervised Learning
- Regression vs Classification
- Features and Target Variables
- Scikit-learn API
- Model Training and Prediction
- Train/Test Split
- Model Evaluation

## Hands-On Lab

The workflow was implemented using Python, Pandas, and Scikit-learn.

The following tasks were completed:

1. **Dataset Preparation**
   - Loaded a dataset and separated it into features (X) and target (y).
   - Identified the input variables and the value to predict.

2. **Train/Test Split**
   - Split the dataset into training and testing sets using an 80/20 ratio.
   - Used `random_state=42` to ensure reproducible results.
   - Verified the shapes of training and testing data.

3. **Scikit-learn Workflow**
   - Applied the standard Scikit-learn workflow:
     - Instantiate the model.
     - Fit the model on training data.
     - Predict results on test data.
     - Evaluate model performance.

Example workflow:

```python
model = Model()
model.fit(X_train, y_train)
predictions = model.predict(X_test)
model.score(X_test, y_test)
```

## Tools Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Jupyter Notebook

## Conclusion

This task provided the foundation for working with supervised Machine Learning models by understanding data preparation, feature-target separation, train/test splitting, and the Scikit-learn workflow.

These concepts will be used in future tasks to build and evaluate Machine Learning models.