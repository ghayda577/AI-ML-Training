# 🧠 Stroke Prediction Classification Project

## 📌 Project Overview

This project builds a machine learning classification pipeline to predict whether a patient is likely to experience a stroke based on healthcare-related information.

The project covers the complete machine learning workflow, including data exploration, preprocessing, model training, evaluation, baseline comparison, and model selection.

---

## 🎯 Objective

The objective is to identify the most suitable classification model for predicting stroke cases while considering the class imbalance in the dataset.

---

## 📂 Dataset

**Dataset:** Healthcare Stroke Dataset

**Target Variable:**

- `stroke`
  - **0** → No Stroke
  - **1** → Stroke

### Features

- Gender
- Age
- Hypertension
- Heart Disease
- Ever Married
- Work Type
- Residence Type
- Average Glucose Level
- BMI
- Smoking Status

---

## 🔍 Exploratory Data Analysis (EDA)

The following analyses were performed:

- Dataset overview
- Missing value analysis
- Duplicate check
- Target class distribution
- Numerical feature distributions
- Categorical feature distributions
- Outlier analysis
- Correlation analysis

### Key Findings

- The **BMI** feature contained missing values.
- The dataset contains **no duplicate records**.
- The target variable is **highly imbalanced**, with significantly fewer stroke cases.
- Age showed the strongest positive correlation with stroke.

---

## ⚙️ Data Preprocessing

A preprocessing pipeline was implemented using **ColumnTransformer** and **Pipeline**.

The preprocessing steps include:

### Numerical Features

- Median imputation using `SimpleImputer`
- Feature scaling using `StandardScaler`

### Categorical Features

- One-Hot Encoding using `OneHotEncoder`

The preprocessing pipeline was fitted only on the training data to prevent data leakage.

---

## 🤖 Models Trained

The following classification models were evaluated:

- Logistic Regression
- Decision Tree
- Random Forest
- Support Vector Machine (SVM)
- K-Nearest Neighbors (KNN)

---

## 📊 Baseline Model

A **Dummy Classifier** with the **Most Frequent** strategy was used as the baseline model.

This provides a reference point to determine whether the machine learning models learned meaningful patterns from the data.

---

## 📈 Evaluation Metrics

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

Because the dataset is highly imbalanced, **Stroke Recall** was considered the primary evaluation metric.

---

## 🏆 Best Model

**Logistic Regression** achieved the best overall performance for this problem.

### Why?

- Highest Stroke Recall (**80%**)
- Better detection of stroke cases
- `class_weight="balanced"` improved performance on the minority class
- More suitable than high-accuracy models that failed to detect stroke patients

---

## 🛠 Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn



---

## 🚀 Workflow

1. Load the dataset
2. Perform exploratory data analysis
3. Handle missing values within the preprocessing pipeline
4. Encode categorical features
5. Scale numerical features
6. Train multiple classification models
7. Compare against a baseline model
8. Evaluate model performance
9. Select the best-performing model

---

## 📌 Conclusion

Although several models achieved high accuracy, accuracy alone was not sufficient because of the severe class imbalance.

Logistic Regression achieved the highest stroke recall, making it the most appropriate model for identifying patients at risk of stroke.