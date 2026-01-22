# Bike Sharing Demand Prediction

## Problem Description and Motivation
The purpose of this project is to predict the hourly number of bike rentals using the data provided. In this case, not every data is useful so accurate EDA is needed. Accurate prediction of bike rental demand is important for bike-sharing systems to manage bike availability efficiently, reduce shortages during peak hours, and improve overall user experience. By understanding the factors that influence bike rental behaviour, this project aims to build a reliable and interpretable prediction pipeline.

---

## Dataset Description
**Source:** Kaggle – Bike Sharing Demand Dataset

The dataset contains hourly bike rental records spanning two years. The task is to predict the total number of bike rentals for each hour in the test dataset using only information available prior to the rental period.

### Features
- `datetime`: Hourly timestamp  -->  Expanded into day, month, hour
- `season`: Season indicator (1 = spring, 2 = summer, 3 = fall, 4 = winter)  
- `holiday`: Whether the day is a public holiday  
- `workingday`: Whether the day is a non-holiday weekday  
- `weather`: Weather condition category  
- `temp`: Temperature in Celsius  
- `humidity`: Relative humidity  
- `windspeed`: Wind speed  

### Target Variable
- `count`: Total number of bike rentals per hour  

### Data Cleaning and Feature Engineering
- The variables `casual` and `registered` were removed to prevent data leakage, as they directly determine the target variable and are not available at prediction time.
- Redundant and weak predictors were reviewed and removed based on exploratory data analysis.
- The `datetime` feature was transformed into meaningful time-based variables including `hour`, `weekday`, and `month`.
- All preprocessing and feature engineering steps applied to the training data were consistently applied to the test data.

---

## Setup Instructions

### Requirements
- Python 3.x
- Google Colab or a local Python environment

### Required Libraries
```bash
pip install pandas numpy matplotlib scikit-learn
