# Breast Cancer Diagnosis Classification

## Overview

A machine learning classification project that predicts whether a breast tumor is malignant or benign using the Wisconsin Diagnostic Breast Cancer dataset.

## Dataset

- 569 samples
- 30 original numerical features
- Binary classification
- Malignant / Benign

## Data Cleaning

- Checked for missing values
- Checked for duplicate rows
- Checked for impossible negative measurements
- Analyzed highly correlated features

## Feature Engineering

Created a shape-based compactness ratio:

mean perimeter² / mean area

## Models

- Dummy Classifier (baseline)
- Logistic Regression
- Random Forest

## Evaluation

Models were evaluated on a stratified 20% held-out test set using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

Confusion-matrix analysis was used to identify missed malignant cases.


## Results

The models were evaluated on a stratified 20% held-out test set containing 114 samples.

| Model | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Baseline | 0.632 | 0.632 | 1.000 | 0.774 | — |
| Logistic Regression | **0.974** | **0.986** | **0.972** | **0.979** | **0.993** |
| Random Forest | 0.956 | 0.959 | 0.972 | 0.966 | 0.992 |

Logistic Regression achieved the best overall performance, outperforming the Random Forest despite being a simpler model.
<img width="600" height="590" alt="image" src="https://github.com/user-attachments/assets/36f6885c-a82e-4031-903e-8f089fdc3f54" />

## Failure Analysis

Because missing a malignant case is particularly important in a clinical screening context, malignant cases were examined separately.

For the Random Forest:

- 39 of 42 malignant cases were correctly identified.
- **3 malignant cases were misclassified as benign (false negatives).**
- 70 of 72 benign cases were correctly identified.
- 2 benign cases were incorrectly classified as malignant (false positives).
- Malignant recall was **92.9%**.

The confusion matrix was:

| Actual / Predicted | Malignant | Benign |
|---|---:|---:|
| Malignant | 39 | **3** |
| Benign | 2 | 70 |

Logistic Regression performed better on the held-out test set, achieving **97.4% accuracy** and **97.6% malignant recall**, compared with 95.6% accuracy and 92.9% malignant recall for Random Forest.
<img width="664" height="561" alt="image" src="https://github.com/user-attachments/assets/30892209-9234-492b-9cc6-c1996c651518" />


## Feature Importance

The most influential features for the Random Forest were:

1. Worst perimeter
2. Worst concave points
3. Worst radius
4. Mean concave points
5. Worst area

These features capture measurements related to the size and geometric characteristics of cell nuclei.
<img width="779" height="561" alt="image" src="https://github.com/user-attachments/assets/1aa07269-f6e5-4efb-828e-5c16a6565f11" />

## Key Findings

- Both trained models substantially outperformed the majority-class baseline.
- Logistic Regression achieved the strongest overall performance.
- The simpler Logistic Regression model slightly outperformed the more complex Random Forest.
- Accuracy alone does not fully describe model performance; examining malignant recall and false negatives revealed that the Random Forest missed 3 malignant cases.

## Limitations

- The dataset contains only 569 samples, with 42 malignant cases in the held-out test set.
- The false-negative estimate may therefore be unstable and would benefit from validation on larger datasets and/or cross-validation.
- The dataset contains preprocessed numerical measurements rather than raw medical images.
- This project is an educational machine learning exercise and has not been clinically validated. It should not be used for medical diagnosis.

## Conclusion

This project demonstrated a complete machine learning classification workflow, including data cleaning, feature analysis, feature engineering, model training, baseline comparison, held-out evaluation, and failure analysis.

Logistic Regression achieved the best performance on the held-out test set, while the Random Forest provided useful feature-importance insights. The analysis also demonstrated why evaluating model failures, particularly missed malignant cases, is important when accuracy alone can hide costly errors.

## Limitations

This project uses a small, preprocessed tabular dataset and is intended for educational machine-learning purposes, not clinical diagnosis.

## Tools

Python, Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn
