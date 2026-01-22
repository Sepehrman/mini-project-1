# Bike Sharing Demand Prediction

Build a complete regression system to predict continuous outcomes using real-world data. 

## Problem Description and Motivation
The purpose of this project is to predict the hourly number of bike rentals using the data provided. In this case, not every data is useful so accurate EDA is needed. Accurate prediction of bike rental demand is important for bike-sharing systems to manage bike availability efficiently, reduce shortages during peak hours, and improve overall user experience. By understanding the factors that influence bike rental behaviour, this project aims to build a reliable and interpretable prediction pipeline.

---

## Dataset Description
**Source:** Kaggle – Bike Sharing Demand Dataset

The dataset contains hourly bike rental records spanning two years. The task is to predict the total number of bike rentals for each hour in the test dataset using only information available prior to the rental period.

### Features
- **datetime** - hourly date + timestamp  
- **season** -  1 = spring, 2 = summer, 3 = fall, 4 = winter
- **holiday** - whether the day is considered a holiday
- **workingday** - whether the day is neither a weekend nor holiday
- **weather** -
  
1: Clear, Few clouds, Partly cloudy, Partly cloudy

2: Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist

3: Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain + Scattered clouds

4: Heavy Rain + Ice Pallets + Thunderstorm + Mist, Snow + Fog

- **temp** - temperature in Celsius
- **atemp** - "feels like" temperature in Celsius
- **humidity** - relative humidity
- **windspeed** - wind speed
- **casual** - number of non-registered user rentals initiated
- **registereds**- number of registered user rentals initiated
- **count** - number of total rentals

### Dropped Features after EDA

1.   ***casual and registered*** = Does not influence real world prediction, it is only known after the rental. Casual and Registered also indicates how many are rented, therefore cannot be included in the prediction. It gives the model the answer already
2.   ***atemp*** = about the same as temp, unecessary and redundant feature
3.  ***humidity*** = weak predictive power, there is no correlation between humidity and the number of rentals
4. ***windspeed*** = closely associated with weather, redundant
5. ***datetime*** = changed to hour, weekday, month

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
```

## Member Contributions
- Bryan: EDA, Analysis
- Sepehr: Modelling, Analysis

## Results Summary

Model performance was evaluated using a validation split of the training data. Multiple regression models were compared to assess their ability to predict hourly bike rental demand. The polynomial regression model achieved the best overall performance, as it was able to capture the non-linear relationships between time-based features, weather conditions, and rental demand that were identified during exploratory data analysis.

### Model Comparison (Validation Set)

| Model                     | RMSE     | MAE      | R²      |
|---------------------------|----------|----------|---------|
| Polynomial (degree = 3)   | 124.83   | 88.26    | 0.528   |
| Polynomial (degree = 2)   | 133.58   | 99.39    | 0.459   |
| Lasso (α = 0.1)           | 152.12   | 111.95   | 0.299   |
| Linear Regression         | 152.12   | 111.95   | 0.299   |
| Lasso (α = 1.0)           | 152.15   | 111.91   | 0.299   |
| Lasso (α = 10.0)          | 153.21   | 113.01   | 0.289   |

These results indicate that incorporating non-linear and interaction effects improves predictive accuracy compared to simpler linear models. Time-related features such as hour of day and working day status were the strongest contributors to model performance.

