# Sales Prediction Model

## Overview
This repository contains the codebase for developing and deploying a sales prediction model using machine learning algorithms, namely Linear Regression and Random Forest Regressor.

## Dependencies
- pandas
- numpy
- sklearn
- Flask
- joblib

##You can install them using pip:
-pip install pandas 
-numpy scikit-learn 
-Flask joblib


##Dataset
The dataset used in this project includes the following files:

sales_train.csv: Training data for sales prediction.
calendar.csv: Contains information about dates.
items_weekly_sell_prices.csv: Contains weekly selling prices of items.
calendar_events.csv: Contains information about different events.
Feature Engineering
The notebook/code performs extensive feature engineering including:

##Merging multiple datasets
Creating lag features
Extracting time-based features
Handling events and special occasions
and much moreModel Training and Validation

##Two models are trained and validated using Mean Absolute Error (MAE) as the evaluation metric:

Linear Regression
Random Forest Regressor

##Model Deployment
The trained model can be deployed using Flask. See app.py for the implementation of the Flask API.
 To run the API:
 -python app.py









