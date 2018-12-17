# Lending-Club-Loan-Status
https://www.kaggle.com/wendykan/lending-club-loan-data/home

### Dataset
These files contain complete loan data for all loans issued through the 2007-2015, including the current loan status (Current, Late, Fully Paid, etc.) and latest payment information. 
The file containing loan data through the "present" contains complete loan data for all loans issued through the previous completed calendar quarter. 
Additional features include credit scores, number of finance inquiries, address including zip codes, and state, and collections among others. 
The file is a matrix of about 890 thousand observations and 75 variables. A data dictionary is provided in a separate file. k

### Target
Build models to predict the chance of default for a loan.

### Ideal Scenario
The dataset has over 100 features, but some of them have too many NA values, and some are not suposed to be available at the beginning of the loan. 
For example, it is not meaningful to predict the status of a loan if we knew the date/amount of the last payment of that loan. 
So I focus on the following features (5 features in each row and 30 features in total including the response 'loan_status')

Lending club keeps receiving the monthly installment payment from the borrower, and eventually the loan is paid off and the loan status becomes "Fully Paid."
Signs of trouble: loan is past due with 15 days (In Grace Period), late for 15­30 days, or late for 31­120 days.
Once a loan is past due for more than 120 days, its status will be "Default" or "Charged­off". Lending Club explains the difference between these two [Here]. 
For this project, we will treat them the same.
We focus on closed loans, i.e., loan status being one of the following:
- Class 1 (bad loans): 'Default' or 'Charged Off'; Class 0 (good loans): 'Fully Paid'.

### Main File
Save my main file as mymain.ipynb

### Data Preprocessing 
Based on Project3_test_id.csv to split the train/test data. Convert loan status to 0/1 charge-off indicator. 
Also, I change the response variable loan_status to a 0/1 variable, where 0 indicates fully paid and 1 indicates charge-off or Default.
Process the missing value and categorial variable. Create dummy variables for the categorical variables. Then I replace the missing value by mean.

### Exploratory data analysis
- ['term'] About 76% of the completed loans have three-year periods, and the rest have five-year periods. Loans with five-year periods are more than twice as likely to charge-off as loans with three- year periods.
- ['loan_amnt'] Charged-off loans tend to have higher loan amounts.
- ['int_rate'] Charged-off loans tend to have much higher interest rates.
- ['annual_inc'] individuals with higher income are more likely to pay off their loans.
- ['pub_rec_bankruptcies'] Individuals who pay off their loans are more likely to have several mortgage accounts.
- ['purpose'] Notice that only 12% of completed loans for weddings have charged-off, but 30% of completed small business loans have charged-off.
- ['addr_state'] The charge-off rate ranges from 13.0% in Washington, DC to 27.6% in Mississippi.

### Model Prediction 
I used three different models KNN, RF, and SGD to predict the result. For hyperparameter turning, I used grid search to automatically find the optimal parameter for me.

### Result 

![alt text](https://github.com/hyestt/Walmart-Recruiting---Store-Sales-Forecasting/blob/master/Result.png)
