![download](https://github.com/bmjaron/dsc_phase1_project/assets/115658357/7c3ffb05-e420-43b4-999c-f225d5f8e81e)

# King County Housing Price Predictions

**Author**: [Benjamin Jaron](mailto:bmjaron@gmail.com)

## Overview 

This project analyzes the King County housing dataset and builds a linear regression model to predict housing prices. The stakeholder is a real estate investment firm that needs to understand accurate housing prices. The results of the model are positive overall, but should be used with caution.

## Business Problem

Our stakeholder is a real estate investment firm located in King County, which is in Washington State. Their business is to buy homes that are presumed to be at a discount, hold or rennovate them, with the aim to flip the homes at a later date for a profit. They have presented us with a data set, and want us to use the data to build a model that will be able to accurately predict the true value of a home.

## Data 

Our project makes use of only one dataset, which is officially titled the King County House Sales dataset. The dataset contains 30,155 entries, with very few null values. Additionally, there are 25 columns, 2 of which contain price and a unique id for each house. Since the target is price, and id is irrelevant to our modelling, this leaves us with 23 potential predictors. 

## Modeling

Our goal is to build a regression model that can most closely predict the price of a home. There are a few characteristics that will determine what's best, including R-squared (how much of the total variance in house price does our model capture), and whether or not our model and its variables are statistically significant. 

Below we're going to run a simple linear regression as a baseline. The success of any subsequent model is going to be judged by how much it improves the baseline. 

The standard practice for building the appropriate baseline is by using the variable most positively correlated with price as the predictor. We found that sqft_living was the single variable most positively correlated with price. We decided to use this as our baseline, shown below. 

![regression](https://github.com/bmjaron/phase_2_final_project/assets/115658357/09324cf5-5110-4492-b440-606cd2791105)


## Results 



## Conclusions 


