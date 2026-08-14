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

[We'll put your actual final results here.]

## Limitations

This project uses a small, preprocessed tabular dataset and is intended for educational machine-learning purposes, not clinical diagnosis.

## Tools

Python, Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn
