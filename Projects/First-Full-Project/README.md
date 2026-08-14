# Cardiac Patient Monitoring System

## AI & Machine Learning Individual Project

## Project Overview

This project applies Machine Learning techniques to analyze cardiac patient data and build classification models for predicting the presence of heart disease.

The project follows a complete machine learning workflow, including data cleaning, exploratory data analysis, feature engineering, preprocessing, model training, model comparison, cross-validation, hyperparameter tuning, and final model evaluation.

The main goal is to compare different classification models and identify the most suitable model based on appropriate evaluation metrics.

---

## Project Objective

The objective of this project is to:

* Analyze and understand the cardiac patient dataset.
* Clean and prepare the data for machine learning.
* Perform Exploratory Data Analysis (EDA) to identify important patterns and relationships.
* Build a baseline classification model using Logistic Regression.
* Train and compare an additional classification model using Random Forest.
* Apply Feature Engineering and evaluate its impact on model performance.
* Build reusable Scikit-learn Pipelines for preprocessing and modeling.
* Use Stratified Cross-Validation for more reliable model evaluation.
* Perform hyperparameter tuning using GridSearchCV.
* Evaluate the final selected model using appropriate classification metrics and a confusion matrix.

---

## Dataset

The project uses a cardiac-related dataset containing patient health and clinical information.

The dataset includes features such as:

* Age
* Sex
* ChestPainType
* RestingBP
* Cholesterol
* FastingBS
* RestingECG
* MaxHR
* ExerciseAngina
* Oldpeak
* ST_Slope

### Target Variable

The target variable is:

`HeartDisease`

* `0` → No Heart Disease
* `1` → Heart Disease

---

# Project Workflow

## 1. Data Loading and Initial Inspection

The dataset is loaded using Pandas and inspected to understand:

* Dataset shape
* Column names
* Data types
* Missing values
* Duplicate records
* Feature types

---

## 2. Data Cleaning

The dataset is checked for data quality issues, including:

* Missing values
* Duplicate records
* Invalid values
* Potential outliers
* Numerical and categorical feature preparation

---

## 3. Exploratory Data Analysis (EDA)

EDA is performed to better understand the dataset and identify important patterns and relationships.

The analysis includes:

* Descriptive statistics
* Target class distribution
* Numerical feature distributions
* Outlier analysis
* Categorical feature analysis
* Relationships between features and the target variable
* Correlation analysis
* Data quality observations

---

## 4. Feature Engineering

Feature Engineering is applied based on insights obtained from the dataset analysis.

The impact of the engineered feature is evaluated by comparing model performance before and after adding it.

The feature is retained in the final workflow after evaluating its contribution to model performance.

---

## 5. Features and Target Definition

The input features (`X`) and target variable (`y`) are defined for the classification task.

```python
X = df.drop("HeartDisease", axis=1)
y = df["HeartDisease"]
```

---

## 6. Train-Test Split

The dataset is divided into training and testing sets.

A stratified split is used to preserve the distribution of the target classes across both sets.

The test set remains untouched during model development and is used only for the final evaluation.

---

## 7. Data Preprocessing

Numerical and categorical features are preprocessed using Scikit-learn.

The preprocessing workflow includes:

### Numerical Features

* Missing value imputation
* Feature scaling

### Categorical Features

* Missing value handling
* One-Hot Encoding

A `ColumnTransformer` is used to apply the appropriate preprocessing steps to each type of feature.

---

## 8. Baseline Model

Logistic Regression is used as the baseline classification model.

The baseline model provides an initial performance reference for evaluating other approaches.

---

## 9. Stratified Cross-Validation

Stratified Cross-Validation is used to evaluate model performance across multiple folds.

Stratification helps maintain a similar distribution of the `HeartDisease` classes in each fold, providing a more reliable evaluation of model performance.

---

## 10. Baseline Model Evaluation

The baseline model is evaluated using classification metrics to establish its initial performance.

The evaluation helps provide a reference point for comparison with the additional model.

---

## 11. Random Forest Model

A Random Forest Classifier is trained as an additional model and compared with the Logistic Regression baseline.

Both models are evaluated using a consistent methodology.

---

## 12. Model Comparison

The performance of Logistic Regression and Random Forest is compared based on the selected evaluation metrics and cross-validation results.

This comparison helps identify the better-performing approach for the dataset.

---

## 13. Feature Engineering Impact

The impact of the engineered feature is evaluated by comparing model performance before and after adding the feature.

This step helps determine whether the feature provides useful information for the classification task.

---

## 14. Final Pipeline

A final Scikit-learn Pipeline is created using the selected features, preprocessing steps, and model.

The Pipeline combines preprocessing and model training into a single reproducible workflow.

This helps prevent inconsistencies between training and evaluation and makes the workflow easier to rerun.

---

## 15. Hyperparameter Tuning

GridSearchCV is used to search for suitable hyperparameter combinations for the selected model.

The tuning process uses cross-validation to evaluate different parameter combinations and select the best-performing configuration.

---

## 16. Best Model Selection

The best model configuration is selected based on the results of model comparison and hyperparameter tuning.

The selected model is then used for final evaluation.

---

## 17. Final Test Evaluation

The final model is evaluated on the untouched test set.

This provides an estimate of how well the selected model generalizes to unseen data.

---

## 18. Evaluation Metrics

The final model is evaluated using:

* Accuracy
* Precision
* Recall
* F1-Score
* ROC-AUC

---

## 19. Confusion Matrix and Classification Report

A confusion matrix is used to visualize the model predictions and errors.

The Classification Report provides a detailed summary of:

* Precision
* Recall
* F1-Score
* Support

The results are interpreted to better understand the strengths and limitations of the final model.

---

# Models Used

### Logistic Regression

Used as the baseline classification model.

### Random Forest Classifier

Used as the comparison model and further optimized using hyperparameter tuning.

---

# Technologies and Libraries

This project was developed using:

* Python
* Jupyter Notebook
* NumPy
* Pandas
* Matplotlib
* Seaborn
* Scikit-learn

---

# Key Findings

The project analyzes cardiac patient data to identify patterns related to the presence of heart disease.

The workflow evaluates the impact of feature engineering and compares Logistic Regression with Random Forest using consistent evaluation methods.

The final model is selected after model comparison, cross-validation, feature engineering evaluation, and hyperparameter tuning.

The selected model is then evaluated on an untouched test set to estimate its generalization performance.

---

# Limitations

* The analysis is limited to the available dataset and its features.
* Model performance may vary when applied to different datasets or populations.
* The project is intended for educational and machine learning analysis purposes.
* The model should not be used as a substitute for professional medical diagnosis or treatment.

---

# Requirements

Install the required libraries using:

```bash
pip install -r requirements.txt
```

The project is designed to run in a reproducible Python environment using the libraries listed in `requirements.txt`.

---


