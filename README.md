# icu-mortality-prediction
Predicting ICU mortality using Machine Learning

## Objective
This project was completed as part of the Advanced Machine Learning coursework for the MS in Business Analytics program at The University of Texas at Austin, McCombs School of Business. It aims to address the critical challenge of predicting ICU mortality using the Global Open Source Severity of Illness Score (GOSSIS) dataset. The project seeks to develop machine learning models that enhance clinical decision-making, optimize resource allocation, and improve patient survival rates globally.

## Key Features

***Data Preprocessing & Exploration***

Dataset Source: GOSSIS consortium, containing international critical care data, with a publicly available subset of 91,713 rows on Kaggle.

Preprocessing Steps: Dropped irrelevant columns and rows with missing values, created new features (like summing the presence of chronic conditions for comorbidity scores, aggregating Glasgow Coma Scale (GCS) components into a total score, consolidating infrequent categorical values to reduce dimensionality), and scaled numerical features using StandardScaler. We also applied PCA to reduce dimensionality, retaining only key features while maintaining explained variance.


***Handling Class Imbalance***

ICU mortality represents only ~8% of cases in the dataset, leading to a severe imbalance that can skew predictions. We implemented and compared the following strategies:

Do Nothing: Used the dataset as-is.

SMOTENC: Synthetic Minority Oversampling Technique for Nominal and Continuous variables.

Class Weight Adjustment: Penalized misclassification of minority classes during training.


***Modeling Techniques***

We explored a wide range of machine learning algorithms, including Logistic Regression, Naive Bayes, Random Forest, Gradient Boosting (XGBoost, CatBoost), Support Vector Machines (SVM), K-Nearest Neighbors (KNN), and Multi-Layer Perceptron (MLP) Neural Networks.

Trained 27 models using combinations of class imbalance strategies.

Focused on maximizing **recall** to ensure accurate identification of at-risk patients, minimizing false negatives.


## Outcomes

***Model Evaluation Process***

Adjusted decision thresholds to achieve high recall (~90%), prioritizing patient safety by minimizing false negatives.

Conducted K-fold cross-validation for robust performance evaluation.


***Best Model Performance***

The Multi-Layer Perceptron (MLP) neural network with SMOTENC was our top performer, with the following stats :-

Accuracy: 92.71%

Recall: 90.18% (critical for identifying at-risk patients)

Precision: 94.57%

F1-Score: 92.32%

ROC AUC: 98.5%

PR AUC: 98.37%


***Feature Importance and Interpretability***

Used SHAP values for tree-based models and DeepLIFT for neural networks to identify key predictors and enhance transparency.

Key predictors: Age, BMI, Glasgow Coma Scale (GCS).


## Extensions

***Comparison with APACHE Scoring***

We benchmarked our best model against traditional APACHE scores:

_*MLP:*_

Recall: 0.58

ROC AUC: 0.8430


_*APACHE:*_

Recall: 0.41

ROC AUC: 0.8457

While APACHE had higher precision, our MLP model demonstrated superior recall, a critical metric in clinical settings where missing at-risk patients can have severe consequences.
