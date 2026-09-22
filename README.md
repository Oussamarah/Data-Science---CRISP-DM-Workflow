# Customer Churn Analysis

A data science project analyzing customer churn for a subscription-based service. The project performs data cleaning, exploratory data analysis (EDA), and statistical hypothesis testing to identify factors associated with customer churn.

## Project Overview

This project analyzes a customer dataset to understand churn patterns. The goal is to identify which customer and business characteristics are significantly associated with churn, providing actionable insights for retention strategies.

## Dataset

The project uses a `churn.csv` file containing customer subscription data. Each row represents a unique customer with the following attributes:

### Personal Characteristics
- `customerID` - Unique identifier for each customer
- `gender` - Customer's gender
- `SeniorCitizen` - Whether the customer is a senior citizen (encoded: 0 = No, 1 = Yes)
- `Partner` - Whether the customer has a partner
- `Dependents` - Whether the customer has dependents

### Service Characteristics
- `PhoneService` - Whether the customer has phone service
- `InternetService` - Type of internet service (DSL, Fiber optic, None)
- `TypeOfContract` - Type of contract (Month-to-month, One year, Two year)

### Billing & Charges
- `MonthlyCharges` - Monthly charges for the customer
- `TotalCharges` - Total charges to date
- `tenure` - Number of months the customer has been with the company

### Target Variable
- `Churn` - Whether the customer churned (Yes/No)

## Project Structure

The project is organized across two Jupyter notebooks:

### 1. `Untitled-1.ipynb`
- Data loading and initial inspection
- Data cleaning:
  - Handling missing values in `MonthlyCharges` and `TotalCharges`
  - Removing duplicate rows
  - Detecting and removing outliers using Z-score and IQR methods
- Visualizations of distributions and categorical variables

### 2. `Analysis.ipynb`
- Exploratory data analysis
- Visual analysis of categorical variables
- Chi-square tests of independence to identify statistically significant associations with churn
- Heatmaps showing churn rates by customer segment

## Data Cleaning Steps

1. **Missing Values**: 
   - Rows with both `MonthlyCharges` and `TotalCharges` missing were dropped (6 rows)
   - Missing `TotalCharges` were imputed using `MonthlyCharges * tenure`
   - Missing `MonthlyCharges` were imputed using `TotalCharges / tenure`
   - Remaining missing values in `MonthlyCharges` were dropped

2. **Duplicates**: 31 duplicate rows were identified and removed

3. **Outlier Detection**:
   - `MonthlyCharges`: Z-score method (|z| > 3) removed 24 outliers
   - `TotalCharges`: IQR method removed 426 outliers

## Statistical Analysis

Chi-square tests of independence were performed between `Churn` and each categorical variable to determine which factors are significantly associated with churn (p < 0.05).

## Requirements

- Python 3.x
- pandas
- matplotlib
- seaborn
- scipy

## Usage

Run the notebooks in sequence to reproduce the analysis:

1. `Untitled-1.ipynb` - Data cleaning and preprocessing
2. `Analysis.ipynb` - Exploratory analysis and statistical testing

## Key Findings

The analysis identifies which customer segments have significantly different churn rates, helping the business focus retention efforts on high-risk segments.

## Notes

- This project is for learning purposes
- The dataset is a sample customer dataset
- Business interpretations should consider data limitations (e.g., imputed values, outlier removal)