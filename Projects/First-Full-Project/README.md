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

The project uses a public cardiac-related dataset containing patient health and clinical information.

The dataset contains 918 patient records and includes the following features:

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

Invalid numerical values are identified and handled as part of the data preparation process.

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

The target distribution is also analyzed to understand the balance between the two heart disease classes.

---

## 4. Feature Engineering

Feature Engineering is applied based on insights obtained from the EDA.

Two engineered features are evaluated:

* `AgeGroup` — groups patients into meaningful age categories.
* `health_risk_count` — combines selected health-related risk factors into a single feature.

The engineered features are evaluated using five-fold cross-validation with F1-score.

The results showed that `health_risk_count` slightly improved the cross-validated F1-score, while `AgeGroup` did not improve model performance.

Therefore, `health_risk_count` was retained in the final workflow and `AgeGroup` was excluded.

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

* Missing value imputation using the median
* Feature scaling using StandardScaler

### Categorical Features

* Missing value handling using the most frequent category
* One-Hot Encoding

A `ColumnTransformer` is used to apply the appropriate preprocessing steps to each type of feature.

The preprocessing steps are included inside Scikit-learn Pipelines to ensure that transformations are learned only from the training data and to help prevent data leakage during cross-validation.

---

## 8. Baseline Model

Logistic Regression is used as the baseline classification model.

The baseline model provides an initial performance reference for evaluating the additional Random Forest model.

---

## 9. Stratified Cross-Validation

Five-fold Stratified Cross-Validation is used to evaluate model performance across multiple folds.

Stratification helps maintain a similar distribution of the `HeartDisease` classes in each fold, providing a more reliable evaluation of model performance.

The same cross-validation strategy is used for both Logistic Regression and Random Forest to ensure a consistent comparison.

---

## 10. Baseline Model Evaluation

The Logistic Regression baseline is evaluated using multiple classification metrics, including:

* Accuracy
* Precision
* Recall
* F1-Score
* ROC-AUC

These results provide a reference point for comparison with the Random Forest model.

---

## 11. Random Forest Model

A Random Forest Classifier is trained as an additional classification model.

The Random Forest model is evaluated using the same training data, preprocessing steps, cross-validation strategy, and evaluation metrics used for Logistic Regression.

This provides a fair comparison between the two models.

---

## 12. Model Comparison

The performance of Logistic Regression and Random Forest is compared using the mean results from five-fold Stratified Cross-Validation.

The comparison considers:

* Accuracy
* Precision
* Recall
* F1-Score
* ROC-AUC

Random Forest was selected as the stronger comparison model based on the cross-validation results.

---

## 13. Feature Engineering Impact

The impact of the engineered features is evaluated using the same Random Forest configuration, preprocessing steps, five-fold cross-validation strategy, and F1-score.

The results were:

* Original Features: F1 = 0.8757
* Original + `AgeGroup`: F1 = 0.8725
* Original + `health_risk_count`: F1 = 0.8775
* Original + Both: F1 = 0.8750

Based on these results, `health_risk_count` was retained because it achieved the highest cross-validated F1-score, while `AgeGroup` was excluded because it reduced model performance.

---

## 14. Final Pipeline

A final Scikit-learn Pipeline is created using the selected features, preprocessing steps, and Random Forest model.

The Pipeline combines preprocessing and model training into a single reproducible workflow.

This helps prevent inconsistencies between training and evaluation and makes the workflow easier to rerun.

---

## 15. Hyperparameter Tuning

GridSearchCV is used to search for suitable hyperparameter combinations for the Random Forest model.

The tuning process uses five-fold Stratified Cross-Validation and evaluates different combinations of:

* `n_estimators`
* `max_depth`
* `min_samples_split`
* `min_samples_leaf`

The test set remains completely unseen during feature selection, cross-validation, and hyperparameter tuning.

---

## 16. Best Model Selection

The best Random Forest configuration identified by GridSearchCV is selected based on cross-validated F1-score.

The selected configuration is then used for the final evaluation on the held-out test set.

---

## 17. Final Test Evaluation

After completing feature selection, cross-validation, and hyperparameter tuning, the final Random Forest model is evaluated on the untouched test set.

The test set was not used during:

* Model training
* Feature selection
* Cross-validation
* Hyperparameter tuning

This provides an unbiased estimate of the selected model's performance on unseen data.

---

## 18. Evaluation Metrics

The final model is evaluated using:

* Accuracy
* Precision
* Recall
* F1-Score
* ROC-AUC

These metrics provide different perspectives on model performance and are used together rather than relying on accuracy alone.

---

## 19. Confusion Matrix and Classification Report

A confusion matrix is used to visualize the model predictions and errors.

It includes:

* True Negatives (TN)
* False Positives (FP)
* False Negatives (FN)
* True Positives (TP)

The Classification Report provides a detailed summary of:

* Precision
* Recall
* F1-Score
* Support

False negatives are particularly important to analyze because they represent heart disease cases that were incorrectly classified as negative.

---

# Final Results

The final Random Forest model achieved the following performance on the unseen test set:

| Metric | Score |
|---|---:|
| Accuracy | 90.76% |
| Precision | 89.72% |
| Recall | 94.12% |
| F1-Score | 91.87% |
| ROC-AUC | 93.79% |

The confusion matrix showed:

* True Negatives (TN): 71
* False Positives (FP): 11
* False Negatives (FN): 6
* True Positives (TP): 94

The high Recall of 94.12% for the Heart Disease class indicates that the model successfully detected most of the positive cases in the test set.

---

# Models Used

### Logistic Regression

Used as the baseline classification model and reference point for model comparison.

### Random Forest Classifier

Used as the comparison model and further optimized using GridSearchCV.

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

The analysis identified meaningful relationships between patient characteristics and the presence of heart disease.

The machine learning experiments showed that Random Forest provided stronger performance than the Logistic Regression baseline based on the cross-validation results.

Feature Engineering was also evaluated systematically. The `health_risk_count` feature slightly improved the cross-validated F1-score and was therefore retained in the final workflow, while `AgeGroup` was excluded because it did not improve performance.

After hyperparameter tuning, the final Random Forest model achieved strong performance on the unseen test set, with a Recall of 94.12%, F1-Score of 91.87%, and ROC-AUC of 93.79%.

---

# Limitations

* The analysis is limited to the available dataset and its features.
* Model performance may vary when applied to different datasets or populations.
* The dataset may not represent all patient populations or real-world clinical settings.
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

# How to Run

1. Clone or download the project repository.
2. Create and activate a Python virtual environment.
3. Install the required dependencies:

```bash
pip install -r requirements.txt
```

4. Open Jupyter Notebook:

```bash
jupyter notebook
```

5. Open the project notebook.
6. Run the notebook from top to bottom.

---

# Project Structure

```text
Cardiac-Patient-Monitoring-System/
│
├── data/
│   └── heart.csv
│
├── notebooks/
│   └── project.ipynb
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

# Disclaimer

This project is developed for educational purposes as part of an AI and Machine Learning training track.

It demonstrates machine learning techniques for analyzing cardiac-related data and does not provide medical diagnosis, treatment recommendations, or clinical decision-making.