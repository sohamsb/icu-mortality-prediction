# icu-mortality-prediction
Predicting ICU mortality using Machine Learning

## Objective
This project was completed as part of the Advanced Machine Learning coursework for the MS in Business Analytics program at The University of Texas at Austin, McCombs School of Business. It aims to address the critical challenge of predicting ICU mortality using the Global Open Source Severity of Illness Score (GOSSIS) dataset. The project seeks to develop machine learning models that enhance clinical decision-making, optimize resource allocation, and improve patient survival rates globally.

## Key Features

*Data Preprocessing & Exploration*

Dataset Source: GOSSIS consortium, containing international critical care data, with a publicly available subset of 91,713 rows on Kaggle.

Preprocessing Steps: Dropped irrelevant columns and rows with missing values, created new features (like summing the presence of chronic conditions for comorbidity scores, aggregating Glasgow Coma Scale (GCS) components into a total score, consolidating infrequent categorical values to reduce dimensionality), and scaled numerical features using StandardScaler. We also applied PCA to reduce dimensionality, retaining only key features while maintaining explained variance.

*Handling Class Imbalance*

ICU mortality represents only ~8% of cases in the dataset, leading to a severe imbalance that can skew predictions. We implemented and compared the following strategies:

Do Nothing: Used the dataset as is.

SMOTENC: Synthetic Minority Oversampling Technique for Nominal and Continuous variables.

Class Weight Adjustment: Penalized misclassification of minority classes during training.
