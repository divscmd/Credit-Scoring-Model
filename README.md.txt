# CodeAlpha Credit Scoring Model

## Project Overview

This project was developed as part of the CodeAlpha Machine Learning Internship.

The objective of this project is to build a machine learning model that predicts whether a loan application will be approved based on financial and credit-related information.

The project uses the Financial Risk for Loan Approval dataset from Kaggle.

## Dataset

The dataset contains 20,000 loan applications with 36 original columns.

The target variable is:

- `LoanApproved = 0` → Not Approved
- `LoanApproved = 1` → Approved

The dataset includes features related to:

- Age
- Annual Income
- Credit Score
- Employment Status
- Education Level
- Loan Amount
- Loan Duration
- Debt-to-Income Ratio
- Payment History
- Previous Loan Defaults
- Credit History
- Savings and Checking Account Balance
- Total Assets and Liabilities
- Monthly Income
- Net Worth

## Data Preprocessing

The following preprocessing steps were performed:

1. Selected relevant features for model training.
2. Removed potentially problematic derived features.
3. Separated numerical and categorical features.
4. Applied `StandardScaler` to numerical features.
5. Applied `OneHotEncoder` to categorical features.
6. Split the data into 80% training and 20% testing sets.
7. Used stratified splitting to preserve the target class distribution.

## Target Leakage Prevention

`RiskScore` was excluded from the model because the dataset generation process uses `LoanApproved` when calculating `RiskScore`.

The following derived or potentially problematic columns were also excluded:

- ApplicationDate
- BaseInterestRate
- InterestRate
- MonthlyLoanPayment
- TotalDebtToIncomeRatio
- RiskScore

## Machine Learning Models

Three classification algorithms were trained and evaluated:

1. Logistic Regression
2. Decision Tree
3. Random Forest

## Evaluation Metrics

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC

## Model Results

| Model | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 92.25% | 85.81% | 80.96% | 83.32% | 97.34% |
| Decision Tree | 87.90% | 77.44% | 69.67% | 73.35% | 91.07% |
| Random Forest | 90.55% | 86.68% | 71.44% | 78.33% | 95.82% |

## Visualizations

### Confusion Matrices

![Confusion Matrices](images/confusion_matrix.png)

### ROC Curve

![ROC Curve](images/roc_curve.png)

### Logistic Regression Feature Importance

![Feature Importance](images/feature_importance.png)

## Saved Model

The trained Logistic Regression pipeline was saved as:

`credit_scoring_logistic_regression.pkl`

The saved pipeline contains both the preprocessing steps and the trained classifier.

## Example Prediction

An example test application was evaluated using the saved model.

- Actual: Not Approved
- Predicted: Not Approved
- Approval Probability: 0.00%

## Project Structure

```text
CodeAlpha_CreditScoringModel/
│
├── CREDIT_SCORE_MODEL.ipynb
├── credit_scoring_logistic_regression.pkl
├── model_comparison.csv
├── README.md
│
└── images/
    ├── confusion_matrix.png
    ├── roc_curve.png
    └── feature_importance.png