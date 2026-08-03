# Day 2 — Linear Regression

## Overview

This task focused on building a **Linear Regression** model using Scikit-learn to predict continuous values.

The objective was to understand how Linear Regression learns the relationship between input features and the target variable, interpret the learned parameters, and evaluate the model using common regression metrics.

## Learning Objectives

- Train a Linear Regression model using Scikit-learn.
- Generate predictions on unseen data.
- Interpret the model's coefficients and intercept.
- Evaluate the model using MAE, RMSE, and R².
- Compare predicted values with actual values.
- Understand the importance of comparing the model against a baseline.

## Topics Covered

- Linear Regression
- Model Training (`fit`)
- Model Prediction (`predict`)
- Model Coefficients
- Model Intercept
- Regression Evaluation Metrics
  - MAE
  - RMSE
  - R² Score
- Actual vs Predicted Comparison
- Baseline Comparison

## Hands-On Lab

The California Housing dataset was used to build and evaluate a Linear Regression model.

The following tasks were completed:

1. **Dataset Preparation**
   - Loaded the California Housing dataset.
   - Displayed the dataset and explored its columns.
   - Separated the data into features (`X`) and target (`y`).

2. **Train/Test Split**
   - Split the dataset into training and testing sets using an 80/20 ratio.
   - Used `random_state=42` to ensure reproducible results.

3. **Model Training**
   - Created a `LinearRegression` model.
   - Trained the model using the training dataset.

4. **Prediction**
   - Generated predictions using the testing dataset.

5. **Model Interpretation**
   - Displayed the model coefficients.
   - Displayed the model intercept.
   - Interpreted the effect of each feature on the predicted house price.

6. **Model Evaluation**
   - Calculated:
     - Mean Absolute Error (MAE)
     - Root Mean Squared Error (RMSE)
     - R² Score
   - Compared the predicted values with the actual values.

## Example Workflow

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()

model.fit(X_train, y_train)

predictions = model.predict(X_test)
```

## Evaluation Metrics

```python
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
import numpy as np

mae = mean_absolute_error(y_test, predictions)
rmse = np.sqrt(mean_squared_error(y_test, predictions))
r2 = r2_score(y_test, predictions)
```

## Tools Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Jupyter Notebook

## Conclusion

This task introduced the complete workflow of Linear Regression, from preparing the dataset and training the model to interpreting its parameters and evaluating its performance.

The results demonstrated how regression models predict continuous values and how evaluation metrics such as **MAE**, **RMSE**, and **R²** can be used to measure prediction quality and assess model performance.