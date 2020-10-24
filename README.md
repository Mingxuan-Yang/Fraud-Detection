# Fraud Detection in Financial Services

## Introduction

This project is to solve the fraud detection problem in financial payment services, which is a binary classification problem. It is aimed to find whether a transaction is made by the fraudulent agents or the genuine agents. The fraudulent agents intends to take control of the customers' accounts and transfer all the funds to another account and cash out of the system. Thus correctly detecting these actions is meaningful and can better protect the customers' property.

## Structure

The whole analyse in the jupyter notebook includes three parts:

- [Exploratory Data Analysis]()
- [Data Cleaning]()
- [Models]()

## Dataset

This dataset is a synthetic dataset generated from PaySim, which is a simulator to generate data that resembles the data pattern of a private and practical dataset and insert malicious samples that represent actions by fraudulent agents. This dataset includes the following features:

- `step`: Maps a unit of time in the real world. In this case 1 step is 1 hour of time.
- `type`: CASH_IN, CASH_OUT, DEBIT, PAYMENT and TRANSFER.
- `amount`: Amount of the transaction in local currency.
- `nameOrig`: Customer who started the transaction.
- `oldbalanceOrg`: Initial balance before the transaction.
- `newbalanceOrig`: Customer's balance after the transaction.
- `nameDest`: Recipient ID of the transaction.
- `oldbalanceDest`: Initial recipient balance before the transaction.
- `newbalanceDest`: Recipient's balance after the transaction.
- `isFraud`: Identifies a fraudulent transaction (1) and non fraudulent (0).

## Models

Since this dataset is highly imbalanced, indicators that are sensitive to imbalance like accuracy should be abandoned. In this project, F1 score is applied as the evaluation metric to measure the model performance. The models that are tested in this project contains:

- CatBoost Classifier
- Light Gradient Boosting Machine
- Decision Tree Classifier
- Random Forest Classifier
- Extreme Gradient Boosting

## Results

The F1 score results are shown below.

|Model|F1 Score|
|:---:|:------:|
|CatBoost Classifier|0.9829|
|Light Gradient Boosting Machine|0.9855|
|Decision Tree Classifier|0.9971|
|Random Forest Classifier|1.0|
|Extreme Gradient Boosting|1.0|

Among these 5 models, Random Forest Classifier and Extreme Gradient Boosting have the best performance in terms of F1 score. The relative importance of features within these two models can be ranked from the most important (1) to the least important (5) as:

|Feature|RF Rank|XGBoost Rank|
|:-----:|:-----:|:----------:|
|type_TRANSFER|5|5|
|step|4|4|
|amount|3|3|
|errorbalanceOrig|1|2|
|newbalanceOrig|2|1|