# House-Sales-Analysis

# Link to presentation
https://docs.google.com/presentation/d/16gbYZ3J0wil40tYnOJnxCsJNtXfCiLa-p68pINBCY-c/edit?usp=sharing

# Overview
In this project, we aimed to assist an insurance company in estimating potential payouts in the event of a total loss of a home, largely determined by the market value of the home. We utilized the King County House Sales dataset, which includes various features of houses. Our methods involved data cleaning, exploratory data analysis, and multiple linear regression modeling. Our models revealed that the condition, total square footage, view, and grade of a house are significant predictors of its price. Despite some limitations, such as potential multicollinearity and non-normal distribution of residuals, our models explained about 41.8% of the variation in house prices. We recommend that the insurance company consider these variables when estimating potential payouts. Future work could involve collecting more data, including additional variables, or trying different modeling techniques to improve the accuracy of the predictions.


# Business problem
An insurance company needs to identify the key features of a home that influence its market value. This information is crucial when estimating potential payouts in the event of a total loss. While the company understands that predicting the exact market value of a home based on its features is challenging, it aims to develop a model that can highlight the most significant features affecting home values.This is important to this company because it directly impacts the company's risk management and financial planning. By understanding the key features that influence home values, the company can make more informed estimates of potential payouts, helping it to manage risk and plan for financial contingencies. 

# Objectives
One objective for this analysis was to discover the features of a home that most significantly impact its market value.
Another was to predict home sales prices based on the other features in the dataset.

## Data Understanding 
The data used for this project is the King County House Sales dataset. The dataset contains house sale prices for King County in Washington State, which includes Seattle. It includes homes sold between May 2014 and May 2015.It was surced from kaggle and directly relates to our data analysis question as it contains information about various features of homes and their corresponding sale prices.The target variable for this analysis is price, which represents the sale price of each home. 
The following variables were used in analysis: condition, total_sqft (a new variable we created by adding sqft_living, sqft_above, and sqft_basement), view, and grade. These variables were chosen based on their potential to influence a home's market value. They are all numerical variables, although condition, view, and grade are categorical variables which were encoded with a specific range of possible values for easier analysis.

## EDA
After loading and describing the data, we plotted some historgrams and bar plots in order to better understand the data. A heatmap where the correlation coefficients between variable were represented by each cell was also visualised in order to better understand the statement. As for the data preparation methods to ensure the data was clean and ready for analysis , here were the steps that were taken:
 -Creating a copy of the original dataset: This was done to preserve the original data and ensure that any changes made during the cleaning process do not affect the original dataset.

    -Dropping the 'yr_renovated' column: This column was dropped because it had a lot of missing values and it was not considered crucial for the prediction of house prices in this analysis.

    -Filling missing values in 'waterfront' column: The missing values in the 'waterfront' column were filled with 'NO' because most houses are not waterfront properties. This assumption is based on the distribution of the data in this column.

    -Filling missing values in 'view' column: The missing values in the 'view' column were filled with the mode of the column. This was the most reasonable approach given that the data in this column is categorical and skewed.

    -Cleaning the 'sqft_basement' column: The '?' values in the 'sqft_basement' column were replaced with '0', and the column was converted to a numeric type. This is because a '?' is likely to represent a missing value, and it's reasonable to assume that a missing value in this context means that the house does not have a basement.

    -Converting the 'date' column to datetime type: This conversion was necessary just to ensure that the column could be used. A feature house_ag which was the difference between the year the house was built and when it was sold was created but very little correlation to prices was found and thus the feature was not utilised.  

    -Encoding categorical variables: The categorical variables 'condition', 'view', 'waterfront', and 'grade' were encoded to numerical values. This is necessary because machine learning algorithms work with numerical data.

    -Identifying and dealing with outliers: For each numerical column, the interquartile range (IQR) was calculated, and any values outside 1.5 times the IQR were considered outliers and removed. This step is important to ensure that the model is not badly influenced by extreme values.

 The choices made during the data preparation process were justified based on the characteristics of the data and the requirements of the analysis.


## Data Modelling
The data modeling process for this project involved several steps, each of which was carefully chosen and justified based on the data and the business problem. Here's a summary of the steps taken and the reasons behind them:

    -Simple Linear Regression: Before diving into multiple linear regression, simple linear regression models were built to understand the relationship between some predictor variables and the target variable individually. This helped to identify which variables had a strong linear relationship with the target variable and were likely to be good predictors in the multiple regression model.

    -Feature Engineering: During the analysis, a new feature, 'total_sqft', was created by adding 'sqft_above' and 'sqft_basement'. This was done based on the understanding that the total square footage of a house, including both above ground and basement square footage, could be a better predictor of house price than these two features separately. This new feature was then included in the multiple regression model.

    -Multiple Linear Regression: Given the nature of the business problem, which is to predict a continuous outcome (house prices), a regression model was chosen. Specifically, multiple linear regression was used because we had multiple predictor variables that we wanted to use to predict house prices.

    -Feature Selection: The initial model included all available features. However, through iterative modeling and analysis of model performance, some features were dropped while others were kept based on their statistical significance and their contribution to the model's predictive power.

    -Iterative Modeling: The modeling process was iterative. After each model was built, its performance was evaluated using metrics such as R-squared and the F-statistic. Based on these evaluations, decisions were made about whether to keep certain features in the model or not. This iterative process helped to improve the model's performance.

    -Interpreting the Model: Once the final model was built, the coefficients of the model were interpreted to understand the relationship between the predictor variables and the target variable. This interpretation is crucial for understanding which features are most important in predicting house prices.

## Evaluation

##### Interpretation of Results: 
The results of the multiple linear regression models show that the variables 'grade', 'view', 'condition', and 'total_sqft' are statistically significant predictors of the price of a house. For each unit increase in these variables, the price of the house increases by a certain amount, holding all other variables constant. This aligns with our intuition that higher quality houses (higher grade and condition), houses with better views, and larger houses (more total square footage) tend to be more expensive.

##### Model Fit:
The R-squared value of the model is 0.418, which means that about 41.8% of the variation in house prices can be explained by these variables. While this isn't a particularly high R-squared value, it's a significant improvement over a baseline model that doesn't include these variables. The F-statistic and its associated p-value also indicate that at least one of the independent variables is statistically significant in the model.

##### Generalizability:
While the model seems to fit the current data reasonably well, it's important to note that it might not generalize perfectly to new data. This is because the model is based on a specific dataset from King County and might not account for all factors that influence house prices in other locations or at different times. However, the variables included in the model are generally considered important factors in determining house prices, so the model is likely to provide a useful template. 

##### Business Benefit: 
Despite its limitations, this model could be very beneficial for the insurance company. It provides a way to estimate the market value of a house based on its features, which is crucial for determining potential payouts in the event of a total loss. By understanding which features have the most impact on house prices, the company can also better assess the risk associated with insuring a particular house. This could help the company make more informed decisions and potentially reduce its financial risk.

## Conclusions
The analysis conducted in this project provides valuable insights into the factors that influence house prices in King County. The multiple linear regression models developed show that the variables 'grade', 'view', 'condition', and 'total_sqft' are statistically significant predictors of the price of a house.

#### Recommendations:

Based on the results of this project, the insurance company should consider these variables when estimating potential payouts in the event of a total loss. Understanding which features have the most impact on house prices can help the company better assess the risk associated with insuring a particular house. This could lead to more informed decisions and potentially reduce financial risk.

#### Limitations:

While the models developed in this project provide useful insights, they do have some limitations. Firstly, the models are based on a specific dataset from King County and might not account for all factors that influence house prices in other locations or at different times. Secondly, the models explain about 41.8% of the variation in house prices, which means that there are other factors not included in the models that also influence house prices. Lastly, the presence of multicollinearity and non-normal distribution of residuals in some models indicate that the models donot fully meet the assumptions of linear regression and perhaps different modelling techniques could work better.

##### Next Steps:

To improve this project in the future, additional data could be collected to include more variables that might influence house prices, such as proximity to amenities, crime rate, or school district quality. Different modeling techniques could also be explored to improve the accuracy of the predictions. Furthermore, techniques to handle multicollinearity and non-normal distribution of residuals could be applied to improve the models. Finally, the models could be validated on new data to assess their generalizability.




