# Day 2 — Cross-Validation

## Overview

This task focuses on evaluating a classification model using 5-fold cross-validation.

The goal is to understand how cross-validation provides a more stable and reliable estimate of model performance than relying on a single validation split.

The Random Forest model from Week 3 is evaluated using stratified 5-fold cross-validation. The mean and standard deviation of the cross-validation scores are reported and compared with the single-split score obtained on Day 1.

---

## Learning Objectives

- Explain how k-fold cross-validation produces a reliable performance estimate.
- Run cross-validation using `cross_val_score`.
- Interpret the mean and standard deviation of cross-validation scores.
- Explain why stratified k-fold cross-validation is important for classification.
- Compare cross-validation performance with a single train/test split.

---

## Key Topics

- Why cross-validation is more reliable than a single validation split.
- How k-fold cross-validation works.
- Rotating training and validation folds.
- Using `cross_val_score`.
- Interpreting the mean and standard deviation of scores.
- Stratified k-fold cross-validation for imbalanced classification tasks.
- Preventing data leakage by including preprocessing inside the pipeline.

---

## Dataset

The **Stroke Prediction Dataset** was used for this task.

The target variable is `stroke`, which indicates whether a patient experienced a stroke.

The dataset is highly imbalanced, with significantly fewer stroke cases than non-stroke cases. Therefore, stratification is particularly important when performing cross-validation.

The `id` column was removed because it is only an identifier and does not provide meaningful predictive information.

---

## Model

The **Random Forest Classifier** from Week 3 was selected for this task.

The preprocessing steps and classifier were combined into a single Scikit-learn `Pipeline`.

The preprocessing pipeline includes:

- Median imputation for missing numerical values.
- Most-frequent imputation for missing categorical values.
- Standardization of numerical features.
- One-hot encoding of categorical features.

Keeping preprocessing inside the pipeline ensures that preprocessing is fitted independently within each cross-validation fold and prevents data leakage.

---

## 5-Fold Cross-Validation

Stratified 5-fold cross-validation was used to evaluate the model across multiple validation sets.

Each fold uses approximately 80% of the data for training and 20% for validation. The validation fold changes in each iteration so that every sample is used for validation exactly once.

The cross-validation scores were:

- **Fold 1:** 95.21%
- **Fold 2:** 94.81%
- **Fold 3:** 95.11%
- **Fold 4:** 95.21%
- **Fold 5:** 94.91%

The scores are close to each other, indicating consistent model performance across the five folds.

---

## Mean and Standard Deviation

The Random Forest model achieved:

- **Mean CV Accuracy:** 95.05%
- **Standard Deviation:** 0.16%

The mean represents the average accuracy across the five validation folds.

The standard deviation measures how much the model's performance varies between folds. The relatively small standard deviation indicates that the model produced consistent accuracy across different subsets of the dataset.

---

## Comparison with Day 1

On Day 1, the Random Forest model achieved a validation accuracy of **95.11%** using a single train/test split.

With 5-fold stratified cross-validation, the model achieved a mean accuracy of **95.05%**.

The difference between the two estimates is only **0.06 percentage points**.

This small difference is expected because the two evaluations use different data splits. The Day 1 score represents performance on one specific validation subset, while the cross-validation estimate is based on five different validation folds.

Therefore, the cross-validation mean provides a more stable estimate of the model's performance across different subsets of the dataset rather than relying on a single split.

---

## Stratified k-Fold Cross-Validation

Because this is a binary classification problem with a highly imbalanced target variable, `StratifiedKFold` was used instead of regular `KFold`.

`StratifiedKFold` preserves approximately the same proportion of each class in every fold.

This is important because the dataset contains significantly fewer Stroke cases than No Stroke cases. Without stratification, some folds could contain an unrepresentative number of Stroke cases, which could make the evaluation less reliable.

The cross-validation setup was:

- **Number of folds:** 5
- **Shuffling:** Enabled
- **Random state:** 42
- **Cross-validation strategy:** Stratified k-fold

---

## Additional Verification: Class Distribution Across Folds

As an additional verification step, inspired by an external reference, the class distribution of the validation set in each fold was examined.

This check confirms that `StratifiedKFold` maintains a similar proportion of Stroke and No Stroke cases across all five folds.

The validation folds contained approximately:

- **Stroke:** 4.8%
- **No Stroke:** 95.2%

The results were:

- **Fold 1:** Stroke = 4.89%, No Stroke = 95.11%
- **Fold 2:** Stroke = 4.89%, No Stroke = 95.11%
- **Fold 3:** Stroke = 4.89%, No Stroke = 95.11%
- **Fold 4:** Stroke = 4.89%, No Stroke = 95.11%
- **Fold 5:** Stroke = 4.79%, No Stroke = 95.21%

The nearly identical class proportions across the folds provide a practical verification that stratification is preserving the class distribution.

---

## Important Note About Accuracy

Although the cross-validation accuracy is high and consistent, accuracy alone may not be sufficient for this highly imbalanced classification problem.

A model can achieve high accuracy while still failing to detect a meaningful number of Stroke cases.

Therefore, metrics such as **Recall, Precision, F1-score, and ROC-AUC** should also be considered when evaluating the model, especially when detecting Stroke cases is important.

---

## Conclusion

The Random Forest model was evaluated using stratified 5-fold cross-validation.

The model achieved a **mean accuracy of 95.05%** with a **standard deviation of 0.16%**, indicating stable performance across the five folds.

Compared with the **95.11%** accuracy obtained from the single split on Day 1, the cross-validation estimate was slightly lower by **0.06 percentage points**.

The small difference demonstrates how performance can vary depending on the selected data split. Using multiple validation folds provides a more stable estimate than relying on a single split.

Finally, `StratifiedKFold` was used to preserve the highly imbalanced class distribution across the folds, making the cross-validation evaluation more appropriate and reliable for this classification problem.