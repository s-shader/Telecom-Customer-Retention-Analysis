# Telecom-Customer-Retention-Analysis
## Increasing custimer retention via modeling 

# Scenario:
### As a consultant for a telecom company I am tasked with coming up with data driven solutions to increase customer retention and potentially attract new customer.

# Data:
### CSV table of cusmtomer churn (if they left) and deatures about their accounts.
### 3300 observations with 20 atributes (columns)
### Target variable: Churn
### https://www.kaggle.com/becksddf/churn-in-telecoms-dataset
### Columns:
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/data_columns.png" width="200" height="350">

# EDA
### I converted 'State' and 'area code' to dummies and I dropped 'phone number.' 
### 2,850 out of 3300 Churn observations are False
### None of the data is very correlated with Churn (aside from churn itself)
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/churn_corr.png" width="200" height="350">


