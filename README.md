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



