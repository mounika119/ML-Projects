# Machine Learning Project: Customer Churn Analysis

## Overview
This project aims to analyze customer churn data, preprocess the dataset, and visualize key insights using Python. The workflow includes handling missing values, encoding categorical features, and creating visualizations.

## Requirements
Ensure you have the following Python libraries installed:

```bash
pip install pandas numpy seaborn matplotlib
```

## Dataset
The dataset includes customer-related features such as tenure, monthly charges, and churn-related details.

## Steps
### 1. Load the Data
```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv('customer_churn.csv')
```

### 2. Check for Missing Values
```python
# Display missing values
print(df.isnull().sum())
```

### 3. Handle Missing Values
#### For Numeric Columns:
```python
numeric_cols = df.select_dtypes(include=['number']).columns
df[numeric_cols] = df[numeric_cols].fillna(df[numeric_cols].mean())
```

#### For Categorical Columns:
```python
non_numeric_cols = df.select_dtypes(exclude=['number']).columns
for col in non_numeric_cols:
    df[col].fillna(df[col].mode()[0], inplace=True)
```

### 4. Verify Column Names
```python
print(df.columns)
```
Ensure the target variable exists. If `Churn Value` is the correct column, use it for analysis.

### 5. Transform Churn Column
```python
df['Churn Value'] = df['Churn Value'].map({1: 'Churned', 0: 'Stayed'})
```

### 6. Visualize Churn Distribution
```python
sns.countplot(x='Churn Value', data=df)
plt.show()
```

## Expected Output
- The missing values should be replaced with mean (numeric) or mode (categorical).
- The `Churn Value` column should be converted to `Churned` or `Stayed`.
- A count plot of `Churn Value` should display the number of churned and non-churned customers.

## Conclusion
This README provides a step-by-step guide to preprocessing and visualizing customer churn data for further ML analysis.
