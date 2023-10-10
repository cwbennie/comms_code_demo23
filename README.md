# Linear Regression in Python: A Case Study

## Overview

This project serves as an introduction to Linear Regression, focusing on creating simple and multiple linear regression models using popular Python packages. Linear regression is a fundamental concept in data science and has broad applicability. It allows us to predict outcomes based on input variables, making it accessible to a wide range of interests and industries.

### When to use linear regression?

Linear regression is a core concept of data science. When we first think about data science, we often think about fitting a model to predict some outcome. The beauty of this is that it is accessible to everyone. Everyone has something that they are interested in and can use linear regression to gain some insight on that topic. Where one person may be interested in predicting sports teams records, another might be interested in when a pharmacy runs out of a drug. Even if you have never heard of linear regression, you probably use the same logic in your everyday life. For example, when you are planning what time to leave to get to work, what you are really doing is predicting commute time based on some factors (day of the week, weather, time of day, yesterday’s commute time, etc).

Linear regression is a great starting point when exploring how variables are related to each other. It is also relatively simple so it can be explained to someone who might not be as familiar with data science. It also serves as a baseline for more complex models. If a more complicated model doesn’t significantly outperform linear regression, then it is likely not a good fit.  However, linear regression does have its drawbacks as well. It does not perform well when the relationship is non-linear. It also can suffer from multicollinearity when our predictors are highly correlated. Lastly, it is very sensitive to outliers which can drastically change how one interprets the model. 

## Data Description

The data used in this project is sourced from the [Life Expectancy dataset](https://www.kaggle.com/datasets/kumarajarshi/life-expectancy-who/) on Kaggle, with modifications on several variables. Here are brief descriptions of the variables:

| Variable         | Description                                             |
|------------------|---------------------------------------------------------|
| Country          | Country of origin for observation                      |
| Year_Cohort      | Years that the observations are recorded               |
| Status           | Developing or Developed                                 |
| Life Expectancy  | Age                                                     |
| Adult Mortality  | Probability of dying between age 15-60 per 1000 population |
| Infant deaths    | Number of infant deaths per 1000 population            |
| Alcohol          | Consumption (liters of pure alcohol) per capita (ages 15+) |
| Hepatitis B      | % HepB immunization coverage among 1-year-olds         |
| Measles          | Number of reported cases per 1000 population           |
| BMI              | Average BMI of the entire population                   |
| Polio            | % polio immunization coverage among 1-year-olds         |
| Total expenditure | Number of under-five deaths per 1000 population        |
| Diphtheria       | % tetanus/pertussis immunization coverage among 1-year-olds |
| HIV/AIDS         | Deaths per 1000 live births (0-4 years)                |
| GDP              | Gross domestic product per capita                      |
| Population       | Population of the country                               |
| Schooling        | Number of years of schooling                            |
| Region           | Geographic region in the world                          |
| Sub_region       | Sub-geographic region in the world                      |

## Simple Linear Regression Model

### Interview Question One

Given this dataset, let's choose one predictor and fit a simple linear regression model to predict life expectancy. Here are the steps:

**Step 1:** We use a heatmap to examine the relationships between life expectancy and potential predictors, and we find that Life Expectancy has a high correlation with Adult Mortality.

**Step 2:** Fit the regression model using the packages in Python:

**Step 3:** Check the output for the R-squared ($R^2$) value, which is 0.650. This indicates that the model accounts for 65% of the variance explained.

**Step 4:** Check the summary output for the significance of the predictors. At an alpha level of 0.05, a p-value of 0.00 signifies that Adult Mortality is a significant predictor for life expectancy.

**Final Model Equation:** Life Expectancy = 80.9243 - 0.0706 * Adult Mortality

## Multiple Linear Regression Model

### Interview Question Two

Given this dataset with multiple predictors and our dependent variable "Life Expectancy," let's write code to fit a multiple linear regression model and interpret the results.

**Step 1:** Calculate the VIF (Variance Inflation Factor) scores for all potential predictors to check for multicollinearity.

**Step 2:** Fit the regression model in Python:

**Step 3:** Check the output for the R-squared and adjusted R-squared values, which are 0.879 and 0.876, respectively. This means that the model accounts for about 87-88% of the variance explained.

**Step 4:** Check for the output and significance of the predictors. Some predictors may have p-values above the alpha level of 0.05, indicating they are not significant. Additionally, categorical variables like "Year_Cohort" may not have any significant levels.

**Final Model Equation:** Life Expectancy = 53.4228 + 0.0472 * Year_Cohort2004-2007 + 0.3139 * Year_Cohort2008-2011 + ... + 0.8390 * Schooling

## Multiple Linear Regression Model Diagnostic Checks

Model diagnostic checks are crucial to assess the validity of multiple linear regression models. Key assumptions to check include linearity, independence of errors, homoscedasticity, and normality of residuals. Here are some potential problems and solutions:

### Heteroscedasticity

**Potential Problems:** Misleading t-test results, unreliable confidence and prediction intervals.

**Check Methods:**
- Breusch-Pagan Test
- Fitted values vs. residual plot

**Solutions:** Natural-log transformation, Weighted Least Squares regression, or robust standard errors.

### Influential Points

**Potential Problems:** Some observations could significantly impact model estimates.

**Identify Influential Points:**
- Externally Studentized Residuals > t_alpha/2, df = n - 1 - p
- Cook’s Distance (Di) > 4/n

**Solutions:** Record and report influential points, fit models with and without them.

### Violation of Normality

**Potential Problems:** Misleading t-test results, unreliable confidence and prediction intervals.

**Check Methods:**
- Jarque-Bera test
- Q-Q Plot
- Omnibus test

**Solutions:** Natural-log transformation or Box-Cox transformation.
