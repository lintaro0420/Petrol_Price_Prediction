# About the Petrol Hourly Price Dataset

## Overview
Petrol prices move up and down following certain patterns. Estimation of petrol prices can guide buying decisions for families and companies in order to reduce their regular expenses. The Petrol Hourly Price dataset is designed to offer insights into hourly fluctuations in petrol prices throughout the year 2022, specifically in Italy. Your goal is to build regression models on historical records to forecast future petrol prices.

## Input Variables
- **id**: the ID of the records.
- **self_service**: A binary flag indicating whether the data pertains to self-service fuel stations (1) or not (0).
- **date**: The timestamp representing the date and time of each recorded gasoline price.
- **manager**: The identity of the manager responsible for the fuel station.
- **company**: The name of the petrol company associated with the fuel station.
- **station_category**: The type or category of the fuel station, either "on urban street" or "on highway".
- **station_name**: The name of the fuel station.
- **latitude**: The latitude coordinate of the fuel station's location.
- **longitude**: The longitude coordinate of the fuel station's location.
- **price**: The recorded price of gasoline in euros (€) at the specified date and time.

# Model Development and Selection

## Splitting the Target Variable from the Features

The dataset was split into training and validation sets. The target variable `price` was separated from the features.

## Preprocessing Pipeline

Two preprocessing pipelines were defined:

1. **StandardScaler** for numerical features and **OneHotEncoder** for categorical features.
2. **RobustScaler** for numerical features and **OneHotEncoder** for categorical features.

## Model Setup

### Kernel Ridge Regression

A Kernel Ridge regression model was set up with a hyperparameter search space defined for alpha, kernel, degree, and coef0. A pipeline was constructed with the preprocessing steps followed by the Kernel Ridge regression model.

### XGBoost

An XGBoost regression model was set up with a hyperparameter search space defined for learning rate, max depth, number of estimators, and number of threads. A pipeline was constructed with the preprocessing steps followed by the XGBoost regression model.

## Evaluation Metric

The evaluation metric chosen for the models was Root Mean Squared Error (RMSE).

## Experiment Tracking

Experiments were tracked by storing each iteration as a distinct experiment with details such as experiment ID, timestamp, comments, model, hyperparameters, train RMSE, and validation RMSE.

## Function to Create ID and Timestamp for Each Experiment

A function was defined to generate a current timestamp and its MD5 hash for unique experiment identification.

## Function to Log Each Experiment

A function was defined to log experiment details into a JSON file.

## Model Training and Validation

GridSearchCV was used to train and validate both the Kernel Ridge regression and XGBoost models using 5-fold cross-validation.

## Experiment Results

The results of the experiments were logged, and the best model was identified based on the lowest validation RMSE.

## Generating the Prediction File

Predictions were generated using the best model, and the results were saved into CSV files for further analysis.

