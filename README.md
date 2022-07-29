# Fraudulent-Transactions-Prediction
The Dataset is to be identify about a transaction to predict whether it is Fraudulent or Not
# BUSINESS STATEMENT:
In recent times, the number of fraud transactions has increased drastically, due to which companies are facing a lot of challenges. For many banks, retaining high profitable customers is the most important business goal. Banking fraud, however, poses a significant threat to this goal. In this project, We are building a fraud detection model to help banks identify frauds and be vigilant enough to reduce losses incurred due to such unauthorised transactions by the fraudsters.

# DATASET DETAILS:

• step - maps a unit of time in the real world. In this case 1 step is 1 hour of time. Total steps 744 (30 days simulation).

• type - CASH-IN, CASH-OUT, DEBIT, PAYMENT and TRANSFER.

• amount - amount of the transaction in local currency.

• nameOrig - customer who started the transaction

• oldbalanceOrg - initial balance before the transaction 

• newbalanceOrig - new balance after the transaction 

• nameDest - customer who is the recipient of the transaction

• oldbalanceDest - initial balance recipient before the transaction. Note that there is not information for customers that start with M (Merchants).

• newbalanceDest - new balance recipient after the transaction. Note that there is not information for customers that start with M (Merchants). 

• isFraud - This is the transactions made by the fraudulent agents inside the simulation. In this specific dataset the fraudulent behavior of the agents aims to profit by taking control or customers accounts and try to empty the funds by transferring to another account and then cashing out of the system. 

• isFlaggedFraud - The business model aims to control massive transfers from one account to another and flags illegal attempts. An illegal attempt in this dataset is an attempt to transfer more than 200.000 in a single transaction.

![image](https://user-images.githubusercontent.com/103564871/181810444-67f25fe3-9f0c-4128-9244-d5f5fc800a58.png)

# EDA/DATA VISUALIZATION
NULL VALUES AND DUPLICATE VALUES: 
There is no null values and no duplicate values present in dataset. Hence, Dataset is cleaned,but we still need to perform data analysis since the data contains huge variations in the value in different columns. Normalization will also improve the overall accuracy of the machine learning model.
![image](https://user-images.githubusercontent.com/103564871/181812152-474289ab-e42a-47b1-9002-69ad929996d5.png)
![image](https://user-images.githubusercontent.com/103564871/181812174-2ea69127-4383-4b7c-8dca-57042bdd3b9a.png)

# Relation between the Fraud Transaction and the Transactions Flagged by the system
![image](https://user-images.githubusercontent.com/103564871/181812310-261fbadd-a313-4d72-b60a-f1966ea081c2.png)

# Fraud Transactions and Transaction types
INFERENCES:
From the above graph we can see that the Fraudulent transfers are from TRANSFER(4097) and CASH_OUT(4116), transaction types.
![image](https://user-images.githubusercontent.com/103564871/181812542-40b4d679-6437-4001-b08c-8c3057113204.png)

# Flagged As Fraud per transaction
Inferences:
From the above graph we can see that the money transfers that are flagged fraud are from TRANSFER Transaction type. So out of 4097 only 16 were Flagged Fraud by the system.
However, only 16 out of 6 million transactions were flagged by the system. It is safe to say that the system uses an unreasonable parameter to detect fraud transactions.

![image](https://user-images.githubusercontent.com/103564871/181812827-323b6be1-eb1c-4861-91ba-b29dc8250a3c.png)

# Data Cleaning

As We know Dataset is totally Biased, 8231 are fraud transactions(minority class) where as remaining are non fraud transactions(majority class). However We are trying to make content small so that we could balanced the dataset. Hence we are going to take 12000 data from each type(Payment, Transfer, Cash_out, Debit ,Cash_in) which is non fraud and will make one dataframe of fraud data i.e. 8231 and we will combine all the dataframe to perform further steps.

We do not get any beneficial information from the nameOrig or nameDest, so we'll be dropping these columns.

# Feature Engineering

Taking note of the balances before and after transactions
As most of the transactions has errors in showing the account balances before and after transaction, we calculate the error:

Number of transactions where oldbalanceorig & newbalanceorig is zero but amount of transaction is not zero : 17098
Number of recipients who have newbalanceDest and oldbalanceDest is zero: 16831 


Taking note of the balances before and after transactions
As most of the transactions has errors in showing the account balances before and after transaction, we calculate the error by adding two columns 'origin_bal_change’ and 'dest_bal_increase’
'origin_bal_change' = 'oldbalanceOrg'] - 'newbalanceOrig'
'dest_bal_increase' = 'newbalanceDest' - 'oldbalanceDest'

# Heat Map
![image](https://user-images.githubusercontent.com/103564871/181813621-29269533-b80c-47d5-8a31-0d5c7b2f81a4.png)











