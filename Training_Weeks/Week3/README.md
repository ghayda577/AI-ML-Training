# Week 3 — Supervised Learning with Scikit-learn

This repository contains the work completed during **Week 3 of the AI & Machine Learning Internship Program**.

The main focus of this week was learning supervised learning workflows using **Scikit-learn**, including regression, classification, preprocessing, model evaluation, and model comparison.

---

## Topics Covered

- Supervised Learning Concepts
- Regression vs Classification
- Train/Test Split
- Linear Regression
- Logistic Regression
- Classification Metrics
- Confusion Matrix
- ROC Curve and AUC
- Decision Trees
- Random Forest
- Support Vector Machine (SVM)
- K-Nearest Neighbors (KNN)
- Machine Learning Pipelines
- Data Preprocessing and Feature Transformation

---

# Week 3 Mini Project — Stroke Prediction Classification

## Project Overview

This project applies machine learning classification algorithms to predict stroke occurrence using healthcare data.

Since the target variable is binary:

- `0` → No Stroke
- `1` → Stroke

This task is formulated as a **binary classification problem**.

The project follows a complete machine learning workflow:

- Exploratory Data Analysis (EDA)
- Data preprocessing
- Feature transformation
- Train/Test split
- Model training
- Model evaluation
- Model comparison
- Final model selection

---

## Dataset

The dataset contains healthcare information about patients, including:

- Age
- Gender
- Hypertension
- Heart disease
- Marital status
- Work type
- Residence type
- Average glucose level
- BMI
- Smoking status

Target variable:

- `stroke`

Dataset size:

- 5110 samples
- 12 features

---

## Data Preprocessing

The following preprocessing steps were applied:

- Removed the `id` column because it does not provide useful predictive information.
- Handled missing BMI values using median imputation.
- Applied One-Hot Encoding for categorical features.
- Applied Standard Scaling for numerical features.
- Used Scikit-learn Pipeline to prevent data leakage.

---

## Models Compared

The following classification models were trained and evaluated:

- Logistic Regression
- Decision Tree
- Random Forest
- Support Vector Machine (SVM)
- K-Nearest Neighbors (KNN)

A Dummy Classifier was also used as a baseline model for comparison.

---

## Evaluation Metrics

Because the dataset is highly imbalanced, accuracy alone is not a reliable evaluation metric.

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix
- ROC-AUC

For this healthcare problem, **Stroke Recall** was considered the most important metric because detecting actual stroke cases and reducing False Negatives is critical.

---

## Model Results

The best performing model was:

## Logistic Regression

Performance:

- Stroke Recall: **80%**
- ROC-AUC: **0.84**

Logistic Regression achieved the highest ability to detect stroke cases compared with the other evaluated models.

The use of:

```python
class_weight="balanced"
```

helped the model handle the class imbalance by giving more importance to the minority class (`stroke = 1`).

---

## Key Findings

- Accuracy was not sufficient for this problem because the dataset contains many more non-stroke cases than stroke cases.
- Models with high accuracy did not always detect stroke cases effectively.
- Logistic Regression and SVM achieved the best Stroke Recall by reducing False Negatives.
- Reducing missed stroke cases was considered more important than minimizing False Positives.

---

## Tools Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## Project Structure

```
Week3-Supervised-Learning/

│
├── Stroke_Prediction_Classification.ipynb
│
└── README.md
```

---

## Learning Outcomes

Through this project, I practiced:

- Building an end-to-end supervised learning pipeline.
- Preparing real-world healthcare data for machine learning.
- Handling missing values and categorical variables.
- Comparing multiple classification algorithms.
- Choosing suitable evaluation metrics for imbalanced datasets.
- Selecting a final model based on the problem objective.
