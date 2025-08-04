# Computational Analysis of Human Liver RNA-Seq Data

## Overview

This project presents a computational analysis of human liver RNA-Seq data to identify key genetic markers associated with specific liver conditions. We utilized a dataset containing RNA expression profiles and associated metadata, building a robust machine learning pipeline to classify samples.

## Key Objectives

The primary goals of this analysis were:

1.  To develop and train three distinct machine learning classifiers—**Support Vector Machines (SVMs), XGBoost, and Random Forest**—to accurately predict sample class based on RNA expression data.
2.  To evaluate the performance of each model, ensuring they are effectively trained and capable of making accurate predictions.
3.  To identify and compare the most important genes (features) used by each model during training.
4.  To pinpoint vital genes that are consistently highlighted across different models, which may be crucial for the effective diagnosis of liver diseases.

## Methodology

### Data Preprocessing
The raw dataset, sourced from [**(https://www.refine.bio/experiments/GSE61260/human-liver-gene-expression-data-from-subjects-of-varying-ages)**], contained both RNA-Seq expression data and clinical metadata. We performed the following key preprocessing steps:
* Combined RNA expression data with a carefully selected subset of metadata to form the final training dataset.
* **Feature Scaling:** Applied a `StandardScaler` to normalize the data, which is essential for models like SVM and helps improve the convergence and performance of all classifiers.
* **Addressing Class Imbalance:** Employed the **SMOTE (Synthetic Minority Over-sampling Technique)** component within our pipeline to handle class imbalances, preventing the models from becoming biased towards the majority class.

### Machine Learning Pipeline

Our workflow was built around a robust machine learning pipeline to ensure consistency and prevent data leakage. The pipeline integrated the preprocessing steps with the chosen classifiers. For each model, the pipeline included:
* `StandardScaler` for data normalization.
* `SMOTE` for balancing the training data.
* The selected classifier (SVM, XGBoost, or Random Forest).

### Model Evaluation

Each trained model was evaluated on a held-out test set using three key metrics to provide a comprehensive understanding of its performance:

1.  **Classification Report:** A detailed report that provides per-class metrics such as **precision, recall, and F1-score**, offering a clear view of how well the model performs on each class individually.
2.  **Confusion Matrix:** A visual representation of the model's predictions versus the actual values. This matrix allows for a clear visualization of the number of correct and incorrect classifications for each class.
3.  **Feature Importance Analysis:** We identified the most influential genes used by each model to make its predictions.
    * For **Random Forest and XGBoost**, we used the built-in `feature_importances_` attribute.
    * For the **Support Vector Machine**, we utilized the permutation importance method to rank features, as SVMs do not have a native feature importance attribute.

## Repository Contents

* `notebooks/`: Jupyter notebooks detailing the data exploration, preprocessing, model training, and evaluation steps.
* `data/`: Raw and processed data files.
* `README.md`: This file.
* `requirements.txt`: A list of all necessary Python libraries to run the project.
