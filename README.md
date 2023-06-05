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

This model has an R-squared of 0.75, which means that it captures roughly 75% of the total variance in house price. Additionally, the predictors were statistically significant. The interpretation of our model is the following: a house with no square feet has a price of $0, while every subsequent square foot added increases the price by $531.

Our next step was to add multiple variables to the model, and see if we could achieve a higher R-squared than the baseline model. The numerical variables that we chose were: bedrooms, floors, sqft_garage, sqft_patio, and year_built (in addition to sqft_living). These numerics were those that did not have high positive correlation with sqft_living. These were carefully chosen to eliminate multicolinearity, the fact that highly correlated variables move together. A regression model has to be able to predict changes associated with one variable while holding all else constant, if variables move together this becomes harder to do. 

We also added 2 categorical variables: grade and view. Grade is the overall grade of the house that is calculated based on the quality of construction. This is determined based on the quality of materials used and quality of worksmanship (higher quality materials/worksmanship means it cost more to build). View is self-explanatory, whether or not the home has any view of greenery or bodies of water that are prevelant in King County. In order to use these categorical variables in our model, we broke them into samller subcategories and used ordinal encodig to convert words to numbers. 

Additionally, in order to better capture some curvature in sqft_living, we exponentially transformed this variable. 

## Results 
![regression_equation](https://github.com/bmjaron/phase_2_final_project/assets/115658357/634449c8-ddc6-4885-8fb8-adb7412cc852)

![regression_equation_table](https://github.com/bmjaron/phase_2_final_project/assets/115658357/d61412d2-37e6-4a9c-b9ca-953c45fcfcd4)


The adjusted R-squared of our model is 0.779, meaning that our model captures about 78% of the variance of house price. This is certainly an improvement from our baseline, and even some of the other multiple regressions we ran.

Our model is also statistically significant, and all of our coefficients are statistically significant. Before we explain what our model is *saying*, let's first check some of our assumptions of linearity:


1.   **Linearity:** Since we're running multiple regression, we can't visualize linearity. Instead, we'll rely on the rainbow test which was run above. The very low p-value indicates that we must reject the null hypothesis that the model is linear in favor of the alternative hypothesis that the model is **not** linear.
2.  **Multicolinearity:** This should not be a problem for us, as we worked hard to eliminate this problem earlier.
3. **Normality:** Looking at the p-value of the Jarque-Bera test, which checks for residual normality, we can see a value of 0. This means that we can reject the null hypothesis that our model residuals are not normal in favor of the alternative hypothesis that our model residuals are normal. In short, we've met the normality assumption with statistical significance. 
4. **Homoscedasticity:** A look above at the Goldfeld-Quandt test we ran shows a p-value of 0.99, which means we fail to reject the null hypothesis, and conclude that our data is homoscedastic.

Although we may be tempted to revert to our baseline model because of the failed linearity assumption, we'll show below that each model we ran, even the linear baseline, failed this assumption. So despite the lack of linearity, we're going to rely on our new model, but very cautiously. 


## Conclusions 


