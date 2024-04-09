# Goals

The objective of this hackathon is to develop a machine learning model to predict what a tourist will spend when visiting Tanzania.The model can be used by different tour operators and the Tanzania Tourism Board to automatically help tourists across the world estimate their expenditure before visiting Tanzania.

# Key Points
Given data (test.csv) for a tourist traveling to Tanzania,  this can be used as input for the necessary features. Our model would then try to predict the total cost of this individual tourist.

* Machine Learning Model
    * Predict Total Cost of Tourists

* Evaluation Metric MAE (Mean Absolute Error)
    * It is a measure used in statistics to quantify how close predictions or estimates are to the actual values.
* Alternative Metrics for Regression:
    * R^2
    * Adjusted R^2
    * MSE (Value) & RMSE (Original Value)
    * MAPE (Percentage of MAE)

* Models
    * Linear Regression
    * KNearest Neighbor
    * Decision Trees
    * Random Forest
    * Support Vector Machine

* Data
    Currency
    Total group size

# EDA Insights
- There are entries missing in 
    - travel_with (23%)
    - most_impressing (6.5%)
    - total_female (0.06%)
    - total_male (0.1%)
- There is at least one observation that can be considered as an outlier
    -  value for total_female and total_male is way beyond all the other values
- There are 15 observations where there is no value for both total_female and total_male
    - df[(df.total_female == 0) & (df.total_male == 0)]
## Thoughts & questions
- How to impute missing values?
    - travel_with: 
        - 1085 travelled alone
            -  df[(df.travel_with.isna()) & (df[['total_male', 'total_female']].sum(axis=1) == 1)]
        - 27 did not travel alone
        - for 2 we don't know
    - most_impressing: no_answer
## Results
* Imput : df[(df.travel_with.isna()) & (df[['total_male', 'total_female']].sum(axis=1) == 1)]
    * Value for Imputing: 'Alone'
* Drop 29 : df[(df.travel_with.isna()) & (df[['total_male', 'total_female']].sum(axis=1) != 1)]

# Baseline Model
    * Linear Regression
    * Focus on 1 or 2 Columns
    * Take the mean of the cost