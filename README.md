# 🩺 Diabetes Prediction Using Machine Learning

## Overview

This project develops and compares several supervised machine learning models to predict whether a patient has diabetes using the **Pima Indians Diabetes Dataset**.

The project follows a complete machine learning workflow, including:

- Exploratory Data Analysis (EDA)
- Data Cleaning
- Missing Value Imputation
- Feature Scaling
- Handling Class Imbalance using SMOTE
- Hyperparameter Tuning with GridSearchCV
- Model Evaluation and Comparison

The goal is to determine which classification algorithm provides the best predictive performance for diabetes diagnosis.

---

## Research Question

**Which machine learning algorithm provides the most reliable prediction of diabetes based on patient medical measurements?**

---

## Dataset

**Dataset:** Pima Indians Diabetes Dataset

- **768 patient records**
- **8 predictor variables**
- **1 binary target variable (Outcome)**

Target:

- **0** → No Diabetes
- **1** → Diabetes

### Features

| Feature | Description |
|----------|-------------|
| Pregnancies | Number of pregnancies |
| Glucose | Plasma glucose concentration |
| BloodPressure | Diastolic blood pressure |
| SkinThickness | Triceps skinfold thickness |
| Insulin | 2-hour serum insulin |
| BMI | Body Mass Index |
| DiabetesPedigreeFunction | Diabetes family history score |
| Age | Age of the patient |

Dataset Source:

- https://archive.ics.uci.edu/ml/datasets/Pima+Indians+Diabetes

---

# Project Workflow

```
Load Dataset
      │
      ▼
Exploratory Data Analysis
      │
      ▼
Train/Test Split
      │
      ▼
Replace Invalid Zeros with NaN
      │
      ▼
Fit Imputer on Training Data
      │
      ▼
Transform Training and Test Data
      │
      ▼
StandardScaler
      │
      ▼
SMOTE (Training Data Only)
      │
      ▼
Model Training
      │
      ▼
GridSearchCV
      │
      ▼
Model Evaluation
```

---

# Exploratory Data Analysis

The notebook includes several visualizations to understand the dataset before model development.

### Data Exploration

- Dataset overview
- Feature statistics
- Class distribution
- Missing value inspection
- Histograms
- Boxplots
- Correlation heatmap
- Comparison between diabetic and non-diabetic patients

### Key Findings

- No official missing values
- Several medical variables contained unrealistic zero values
- Moderate class imbalance
- Some predictors showed strong relationships with the target variable, particularly **Glucose** and **BMI**

---

# Data Preprocessing

The following preprocessing steps were applied before model training.

## 1. Train-Test Split

The dataset was first divided (Rule of thumb) into:

- 80% Training
- 20% Testing

Splitting the data before preprocessing prevents **data leakage**, ensuring that information from the test set is not used during model training.

---

## 2. Handling Invalid Values

After splitting, the following variables in both the training and test sets were checked for physiologically impossible zero values:

- Glucose
- BloodPressure
- SkinThickness
- Insulin
- BMI

These zero values were treated as missing data and replaced with **NaN**.

---

## 3. Missing Value Imputation

Missing values were imputed using **SimpleImputer** fitted **only on the training data**. The same imputer was then applied to the test data to maintain consistency and prevent data leakage.

---

## 4. Feature Scaling

The predictor variables were standardized using **StandardScaler**, fitted on the training data and then applied to both the training and test sets.

Feature scaling was necessary because KNN, SVM, and Neural Networks are sensitive to differences in feature scales.

---

## 5. Handling Class Imbalance

The training dataset was balanced using **SMOTE (Synthetic Minority Over-sampling Technique)**. SMOTE generates synthetic samples for the minority class to improve model learning.

Importantly, SMOTE was applied **only to the training data**, while the test data remained untouched for unbiased evaluation.

---

# Machine Learning Models

The following supervised classification algorithms were implemented.

## K-Nearest Neighbors (KNN)

Hyperparameters tuned:

- Number of Neighbors
- Weight Function

---

## Support Vector Machine (SVM)

Hyperparameters tuned:

- Kernel
- Regularization Parameter (C)
- Gamma

---

## Neural Network (MLPClassifier)

Hyperparameters tuned:

- Hidden Layer Architecture
- Activation Function
- Learning Rate
- Alpha (L2 Regularization)

Early stopping was enabled to reduce overfitting.

---

## Random Forest

Hyperparameters tuned:

- Number of Trees
- Maximum Tree Depth

---

# Model Evaluation

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion Matrix
- Classification Report

GridSearchCV with **10-fold cross-validation** was used for hyperparameter optimization.

---

# Results

| Model | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|--------|----------|-----------|--------|----------|----------|
| KNN | 75.3% | 68.2% | 55.6% | 61.2% | 0.810 |
| SVM | 72.7% | 59.4% | **70.4%** | 64.4% | 0.807 |
| Neural Network | **77.3%** | **68.6%** | 64.8% | **66.7%** | **0.834** |
| Random Forest | 73.4% | 65.9% | 50.0% | 56.8% | 0.814 |

---

# Best Model

The **Neural Network** achieved the best overall performance.

**Performance**

- Accuracy: **77.3%**
- F1-score: **66.7%**
- ROC-AUC: **0.834**

Although the **SVM** achieved the **highest Recall (70.4%)**, the Neural Network provided the best overall balance between Precision, Recall, and ROC-AUC.

---

# Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Imbalanced-learn
- Jupyter Notebook

---

# Repository Structure

```
diabetes-prediction-machine-learning/
│
├── data/
│   └── diabetes.csv
│
├── notebooks/
│   └── diabetes_prediction.ipynb
│
├── images/
│   ├── dataset_distribution.png
│   ├── Confusion matirx (NN).png
│   ├── Correlation Heatmap.png
│   ├── histogram plot.png
│   ├── Correlation Heatmap.png
│   ├── Outcome balance.png
│   └── Model Comparison.png
│
├── README.md
├── requirements.txt
├── LICENSE
├── .gitignore
└── diabetes_prediction.pdf
```

## Report

A detailed project report is available here:

[Diabetes Prediction Report](diabetes_prediction.pdf)

---

# Installation

Clone the repository

```bash
git clone https://github.com/yourusername/diabetes-prediction.git
```

Move into the project folder

```bash
cd diabetes-prediction
```

Install dependencies

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook

```bash
jupyter notebook
```

Open

```
diabetes_prediction.ipynb
```

Run all cells from top to bottom.

---

# Skills Demonstrated

This project demonstrates practical experience with:

- Data Cleaning
- Exploratory Data Analysis (EDA)
- Missing Value Imputation
- Feature Scaling
- Class Imbalance Handling (SMOTE)
- Machine Learning Classification
- Hyperparameter Optimization
- Cross Validation
- Model Evaluation
- Data Visualization
- Python Programming

---

# Future Improvements

Possible future work includes:

- XGBoost
- LightGBM
- CatBoost
- Feature Selection
- SHAP Explainability
- Model Deployment using Streamlit or Flask

---

# Author

**Muhammad Reza Jafari**

- MSc Data Science Student
- Python | Machine Learning | Data Analysis

GitHub: https://github.com/mrezahh

LinkedIn: www.linkedin.com/in/m-reza-jafari

---

## License

This project is released under the **MIT License**.

---

⭐ If you found this project useful, consider giving it a star!