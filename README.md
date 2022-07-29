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

# DATASET ANALYSIS
The target feature is isFraud which is binary feature with 0(NON FRAUD) and 1 (FRAUD). There are 63,54,407 NON-FRAUD TRANSACTIONS (99.88%) and  8213 FRAUDULENT TRANSACTIONS (0.13%)
As expected, most transactions are non-fraudulent. The following visualization underlines this significant contrast.
![image](https://user-images.githubusercontent.com/103564871/181835189-d9fa30d2-6970-43a6-bbd7-5c22d9430ba5.png)


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
Finally, it would be interesting to know if there are any significant correlations between our predictors, especially with regards to our class variable (isFraud). One of the most visually appealing ways to determine that is by using a heatmap


It turned out that the features with positive correlation are amount, type, And the negative correlation are: All the other features.

![image](https://user-images.githubusercontent.com/103564871/181813621-29269533-b80c-47d5-8a31-0d5c7b2f81a4.png)

# DATA PREPROCESSING
We have used the 68231 dataset  (unbalanced). We have split dataset into two dataset: Train and Test. The ratio of splitting was 80 x 20. 
The shape of train and test splitting:
Shape of train: 54,570
Shape of test: 13,643
We have trained and tested each model and recorded the results Accuracy!

![image](https://user-images.githubusercontent.com/103564871/181835656-01cf69fb-5ca5-47cb-bf0e-ca0a11057492.png)

# RANDOM OVERSAMPLING

This dataset is severely imbalanced (most of the transactions are non-fraud). So the algorithms are much more likely to classify new observations to the majority class and high accuracy won't tell us anything. To address the problem of imbalanced dataset we can use oversampling data approach techniques. Oversampling increases the number of minority class members in the training set. The advantage of oversampling is that no information from the original training set is lost, as all observations from the minority and majority classes are kept. 
We have balanced the dataset using RANDOM OVERSAMPLING technique. The class feature (isFraud) now is balanced (50% for fraud transaction and 50% for non-fraud transaction) as in figure below. Then we have split the dataset into two  dataset: Training dataset and Testing dataset. The ratio of splitting was (70x30).

Shape of dataset after resampling : 1,20,00

The Shape of Train and Test splitting:
Shape of Train: 84,000
Shape of Test: 36,000

![image](https://user-images.githubusercontent.com/103564871/181835908-93ca212a-9128-4690-9305-26061a35ac94.png)

# We have trained and tested each model and recorded the results Accuracy:
![image](https://user-images.githubusercontent.com/103564871/181836441-40fa3c5f-c098-4305-9783-366d9152a19e.png)
From above Accuracy Comparison, We got good accuracy in all Algorithms except Logistic Regression, Gaussian Naïve Bayes, K-Fold Cross Validation.
As RANDOM FOREST accuracy is very close to 100% however we finalized random forest as our Final Model.

# DEPLOYMENT IS DONE IN Streamlit
![image](https://user-images.githubusercontent.com/103564871/181836639-8854c631-6f0d-4b47-a46b-979e269ffd22.png)


# CONCLUSION
Good prediction results can be achieved with imbalanced datasets as well as with balanced ones. Decision Tree Classifier, Random Forest Classifier, XG Boost, Light GBM classifier, Ada Boost, and Bagging Classifier gave us the best results being able to detect more than 99.50% fraud transactions and at the same time not classifying some of non-fraud transactions as fraud. There is no perfect model It is up to the company and its objectives to decide which approach is the best in each particular situation.


# GITHUB PROFILE LINK OF GROUP MEMBERS




# THANK YOU




















