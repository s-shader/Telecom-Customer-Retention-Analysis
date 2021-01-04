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
* I converted 'State' and 'area code' to dummies and I dropped 'phone number' 
* 2,850 out of 3300 Churn observations are False
* None of the data is very correlated with Churn (aside from churn itself)
* Some of the X variable are highly correlated with eachother (I dropped the most correlated variables) 
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/churn_corr.png" width="550" height="350">

<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/correlation_graph.png" width="450" height="950">

# Initial Models
## I built a base function to calculate all of the initial models and output the results in a dataframe. 
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/init_models.png" width="700" height="450">

* Focusing on accuracy and recall Gradient boost and XG Boost performed the best
* I focused on these two because false negatives were not very concerning
* Aditionally, KNN and Decision Tree did not test well and look to have overtrained 

## Looking at it visually:
### I constructed a faux confusion matrix with each model and its metric train and test scores 
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/fake_con_matrix.png" width="800" height="880">
### Focusing more on the test results, I constructed a more focused table
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/fake_con_matrix_test.png" width="550" height="700">

# Final Models
## Given the prior results I chose to focus on Gradient boost and XG Boost models.

## Gradient Boost: 
### Using gridsearch I tested a few ranges across a few parramaters resulting in some improvments
### I, again, built a table comparing this new gradient boost model to the initial one, as well as, to a baseline (KNN)
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/gradient_boost_tunedTable.png" width="700" height="450">






