# Telecom-Customer-Retention-Analysis
## Increasing customer retention via modeling 

# Scenario:
### As a consultant for a telecom company I am tasked with coming up with data driven solutions to increase customer retention and potentially attract new customer.

# Data:
### CSV table of customer churn (if they left) and features about their accounts.
### 3300 observations with 20 attributes (columns)
### Target variable: Churn
### https://www.kaggle.com/becksddf/churn-in-telecoms-dataset
### Columns:
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/data_columns.png" width="200" height="350">

# EDA
* I converted 'State' and 'area code' to dummies and I dropped 'phone number' 
* 2,850 out of 3300 Churn observations are False
* None of the data is very correlated with Churn (aside from churn itself)
* Some of the X variable are highly correlated with each other (I dropped the most correlated variables) 
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/churn_corr.png" width="550" height="350">

<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/correlation_graph.png" width="450" height="950">

# Initial Models
## I built a base function to calculate all of the initial models and output the results in a dataframe. 
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/init_models.png" width="700" height="450">

* Focusing on accuracy and recall Gradient boost and XG Boost performed the best
* I focused on these two because false negatives were not very concerning
* Additionally, KNN and Decision Tree did not test well and look to have overtrained 

## Looking at it visually:
### I constructed a faux confusion matrix with each model and its metric train and test scores 
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/fake_con_matrix.png" width="800" height="880">
### Focusing more on the test results, I constructed a more focused table
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/fake_con_matrix_test.png" width="550" height="700">

# Final Models
## Given the prior results I chose to focus on Gradient boost and XG Boost models.

## Gradient Boost: 
### Using gridsearch I tested a few ranges across a few parameters resulting in some improvements
### I built a table comparing this new gradient boost model to the initial one, as well as, to a baseline (KNN)
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/gradient_boost_tunedTable.png" width="700" height="450">

### Additionally, visualizations of the accuracy and recall tests are below

<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/gradBoost_tuned graph_acc.png" width="600" height="450">
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/gradBoost_tuned graph_recc.png" width="600" height="450">

### The new Gradient Boost model outperforms the initial in all metrics between 0.06 and 0.13 and gets closer to its training data metrics

#### Looking at the features below it appears that customer service calls, day charge, and international plan have the biggest impact

<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/GB_features_graph.png" width="950" height="750">





## XG Boost: 
### Same as above, I tested a few ranges across a few parameters resulting in some small improvements
### I built a table comparing this new XG boost model to the initial one, as well as, to the same baseline (KNN)
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/xgBoost_tuned_table.png" width="700" height="450">

### Additionally, visualizations of the accuracy and recall tests are below

<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/xgBoost_tuned_graph_acc.png" width="600" height="450">
<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/xgBoost_tuned_graph_recall.png" width="600" height="450">

### The new XG Boost model outperforms the initial in all metrics between 0.03 and 0.12 and gets closer to its training data metrics

#### Looking at the features below it appears that international plan, voicemail plan, and Tennessee have the biggest impact

<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/xgBoost_tuned_feature_graph.png" width="950" height="750">

# Secondary Analysis 
## Account Length modeling

### Since the presumed goal, in analyzing churn data is to keep customers, I ran a short secondary analysis looking at if customer left early or later than the average customer

### I started by creating a new binary variable: 1 if the customer stayed longer than average, 0 if they didn't
### Since this only works for customers with a defined account length I could only test closed accounts
### As can bee seen below there were no strong correlations with any of the other variables

<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/account_leng_corrTable.png" width="550" height="350">

### When graphing it, however, some states appear to only have accounts longer than average, or the opposite (see below)

<img src="https://github.com/s-shader/Telecom-Customer-Retention-Analysis/blob/main/Images_telecomAnalysis/IA_lenght.png" width="550" height="350">

# Conclusion

### My final final 2 models predict outcomes with an accuracy of 0.95 and 0.96 hinting that they should be taken at least somewhat seriously. They also have recall scores of 0.82 and 0.85 which is important since falls negatives mean a customer left when we expected them to stay. On the other hand false positives are much less significant i.e. bottom line the customer stays.

### In interpreting the models number of customer service calls, international plan, and voicemail plan, all rank in the top 5 features both.

### Given this, the telecom company should portably invest in their customer services. Interaction plans are also slightly correlated with customers leaving and customers in Tennessee are the most significant location so they should focus domestically. It is also worth improving and pushing their voicemail plans.

### Additionally, my secondary analysis, although limited, showed that they do best in RI, NM, LA and worst in IA.

### It is worth noting that some of these conclusions are using a limited sample size and should be reevaluated if implemented.


# Future work

### Additional tuning could help increase the accuracy of my models and increase confidence in my conclusions. There was also limited data for customers that left so getting more information on customers who left. It would also be potentially helpful to get more information on the customers i.e. potentially more specific demographic data.







