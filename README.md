# Gallstone Disease Prediction Using Machine Learning

## Project Overview

This project develops and compares machine learning classification models for predicting gallstone disease using demographic, bioimpedance, medical-history, and laboratory measurements.

Five classification algorithms were trained and optimized using GridSearchCV. Their performance was evaluated using accuracy, precision, recall, F1 score, confusion matrices, and comparisons between training, validation, and testing performance.

Support Vector Machine achieved the best overall test performance, with an accuracy of 87.5%.

## Problem Statement

Gallstones are a common hepatobiliary condition that may cause serious complications if they are not identified and treated.

Traditional diagnostic methods include:

- Ultrasonography
- Computed Tomography
- Magnetic Resonance Imaging

This project investigates whether non-invasive clinical measurements can support the early prediction of gallstone disease using machine learning.

The model is an academic predictive system and is not intended to replace professional medical diagnosis.

## Dataset

The project uses the Gallstone Dataset from the UCI Machine Learning Repository.

Dataset link:

[Gallstone Dataset – UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/1150/gallstone-1)

The dataset used in this implementation contains:

- 319 patient records
- 38 input features
- One binary target variable
- No missing values
- Approximately balanced target classes

## Target Variable

The target column is:

`Gallstone Status`

The target encoding is:

- `0` — Gallstones present
- `1` — Gallstones absent

## Feature Categories

The 38 predictive features are divided into four main categories.

### Demographic Features

- Age
- Gender
- Height
- Weight
- Body Mass Index

### Bioimpedance Features

- Total Body Water
- Extracellular Water
- Intracellular Water
- Lean Mass
- Body Fat Mass
- Protein
- Visceral Fat Area
- Hepatic Fat Accumulation

### Laboratory Features

- Glucose
- Total Cholesterol
- HDL
- LDL
- Triglycerides
- AST
- ALT
- ALP
- Creatinine
- Glomerular Filtration Rate
- C-Reactive Protein
- Haemoglobin
- Vitamin D

### Medical-History Features

- Comorbidity
- Coronary Artery Disease
- Hypothyroidism
- Hyperlipidaemia
- Diabetes Mellitus
- Obesity
- Other clinical conditions

## Project Workflow

The project followed these stages:

1. Loading and inspecting the dataset
2. Checking data types and dataset dimensions
3. Checking for missing values
4. Verifying feature encoding
5. Detecting outliers using the IQR method
6. Visualizing outliers using box plots
7. Handling outliers through clipping
8. Separating input features and target
9. Splitting the data into training and testing sets
10. Scaling features using StandardScaler
11. Training five classification algorithms
12. Applying GridSearchCV for hyperparameter tuning
13. Evaluating training, validation, and testing performance
14. Comparing bias and variance
15. Selecting the best-performing model

## Data Preprocessing

### Missing Values

The dataset was checked for missing values. No missing values were found, so imputation was not required.

### Categorical Encoding

The dataset features were already represented numerically, so additional encoding was not required.

### Outlier Detection

The Interquartile Range method was used to identify outliers.

The outlier boundaries were calculated using:

`Lower Bound = Q1 - 1.5 × IQR`

`Upper Bound = Q3 + 1.5 × IQR`

### Outlier Handling

Outliers were handled using clipping. Values below or above the calculated boundaries were replaced with the corresponding boundary values.

Clipping was selected to preserve all patient records because the dataset is relatively small.

### Train-Test Split

The dataset was divided into:

- 80% training data
- 20% testing data

A random state of 42 was used to make the split reproducible.

### Feature Scaling

StandardScaler was fitted using the training data and then applied to the training and testing features.

Feature scaling was particularly important for SVM because it is sensitive to differences in feature scales.

## Machine Learning Models

The following classification models were developed and compared:

- Support Vector Machine
- Random Forest
- XGBoost
- Gradient Boosting
- Decision Tree

## Hyperparameter Tuning

GridSearchCV with five-fold cross-validation was used to find the best hyperparameter combination for each model.

### Support Vector Machine

The tested hyperparameters included:

- C: `0.1`, `1`, `10`
- Kernel: `linear`, `rbf`
- Gamma: `scale`, `auto`

### Random Forest

The tested hyperparameters included:

- Number of trees: `50`, `100`, `150`
- Maximum depth: `5`, `10`, `20`
- Criterion: `gini`, `entropy`

### XGBoost

The tested hyperparameters included:

- Learning rate: `0.01`, `0.1`, `0.2`
- Maximum depth: `3`, `6`, `9`
- Number of estimators: `50`, `100`, `200`

### Gradient Boosting

The tested hyperparameters included:

- Learning rate: `0.01`, `0.1`, `0.2`
- Maximum depth: `3`, `5`, `7`
- Number of estimators: `50`, `100`, `200`

### Decision Tree

The tested hyperparameters included:

- Maximum depth: `5`, `10`, `20`
- Criterion: `gini`, `entropy`

## Model Evaluation

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1 score
- Confusion matrix
- Training performance
- Cross-validation performance
- Testing performance
- Bias and variance analysis

## Test Results

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---:|---:|---:|---:|
| Support Vector Machine | 87.50% | 89.66% | 83.87% | 86.67% |
| XGBoost | 84.38% | 83.87% | 83.87% | 83.87% |
| Gradient Boosting | 84.38% | 86.21% | 80.65% | 83.33% |
| Random Forest | 81.25% | 82.76% | 77.42% | 80.00% |
| Decision Tree | 76.56% | 78.57% | 70.97% | 74.58% |

## Best Model

Support Vector Machine achieved the best overall test performance.

The best SVM hyperparameters were:

```text
C = 0.1
Kernel = linear
Gamma = scale
