# IMMF-TNBC

**Integrated Multi-Model Framework for Triple-Negative Breast Cancer (TNBC)**

## Overview

This repository accompanies our manuscript and provides an overview of the computational pipeline used to identify TNBC status from clinical/molecular data and to model patient outcomes using classical machine learning and deep learning approaches.

The full implementation is currently shared **on request** to support reviewer and reader evaluation while the associated manuscript is under peer review. This README describes the pipeline at a conceptual level so that reviewers, editors, and readers can understand the overall workflow and evaluate its validity without requiring access to the complete source code at this stage.

## Pipeline Summary

**1. Data Ingestion**
Clinical and molecular data (e.g., TSV/CSV/Excel format, such as panel sequencing or clinical cohort data) are loaded and inspected for structure and completeness.

**2. TNBC Label Derivation**
Where a validated TNBC label is not already provided, ER, PR, and HER2 receptor status fields are parsed and standardized, and a binary TNBC label is derived according to established clinical criteria (ER-negative, PR-negative, HER2-negative).

**3. Preprocessing & Leakage Control**
Receptor-status fields used to derive the label are excluded from the feature set to prevent label leakage. Identifier columns are removed. Remaining features are filtered to numeric types, missing values are imputed, and features are standardized.

**4. Class Balancing**
Given the typical class imbalance in TNBC cohorts, synthetic oversampling (SMOTE) and class-weighting strategies are applied during training to reduce bias toward the majority class.

**5. Model Training**
Multiple model families are trained and compared, including:
- Logistic Regression
- Random Forest
- Support Vector Machine
- XGBoost
- A feedforward Artificial Neural Network (Keras/TensorFlow)

**6. Evaluation**
Models are evaluated using standard classification metrics (accuracy, precision, recall, F1-score, AUC) on held-out test data, with train/test comparisons used to assess overfitting.

**7. Interpretability**
Model explainability is assessed using SHAP (SHapley Additive exPlanations) to identify features contributing most to predictions.

**8. External Validation**
The framework is additionally validated on independent cohorts (e.g., METABRIC and TCGA-derived datasets) using survival/outcome labels, following the same preprocessing and modeling structure, to assess generalizability.

## Data Availability

Datasets used in this study are available at Zenodo: https://doi.org/10.5281/zenodo.22293152

## Code Availability

The complete source code is available from the corresponding author upon reasonable request. This is intended to support open scientific review while formal release procedures (e.g., versioned, citable deposition) are finalized alongside manuscript publication.

## Citation

If referencing this work prior to formal publication, please cite the associated preprint:
https://doi.org/10.64898/2026.08.19.745809

## Contact

For code access requests or questions, please contact the corresponding author listed in the associated manuscript/preprint.
