# Neonatal Weight Prediction Using Inferential Statistics

## Project Overview

This project uses **inferential statistics** to analyze and predict **newborn weight** based on maternal, gestational, and anthropometric factors.

The project combines:

* Exploratory Data Analysis (EDA)
* Descriptive statistics and visualization
* Outlier detection and data cleaning
* Hypothesis testing (t-tests, chi-squared tests)
* Linear regression modeling
* Model selection using Adjusted R², AIC/BIC, and stepwise regression
* Residuals and multicollinearity analysis
* Prediction and visualization of results

The workflow goes beyond simple modeling, providing insights on **which variables significantly influence newborn weight** and how to predict it effectively.


## Business Objective

The main goal is to **forecast newborn weight** before birth to:

* Anticipate healthcare resource needs
* Identify potentially vulnerable newborns (low birth weight)
* Understand maternal and gestational factors affecting weight

Key practical considerations:

* Gestational age and sex are the strongest predictors
* Anthropometric measurements (length, cranium diameter) are used as control variables
* Maternal smoking and age show limited influence in this dataset


## Dataset

The dataset contains **2,500 observations** and **10 variables**:

| Variable       | Type                     | Description |
|----------------|--------------------------|-------------|
| Anni.madre     | Continuous               | Mother's age |
| N.gravidanze   | Discrete                 | Number of previous pregnancies |
| Fumatrice      | Factor (0/1)            | Mother smoking status |
| Gestazione     | Continuous               | Weeks of gestation |
| Peso           | Continuous               | Newborn weight (response variable) |
| Lunghezza      | Continuous               | Newborn length |
| Cranio         | Continuous               | Cranium diameter |
| Tipo.parto     | Nominal                  | Delivery type ("Ces", "Nat") |
| Ospedale       | Nominal                  | Hospital ("osp1", "osp2", "osp3") |
| Sesso          | Nominal                  | Newborn sex ("F", "M") |

After cleaning:

* Removed outliers (e.g., unrealistic maternal ages 0–1)
* Corrected atypical observations affecting model accuracy


## Exploratory Data Analysis

Key findings:

* No significant missing data
* Distributions examined for continuous variables (weight, length, cranium diameter)
* Histograms, density plots, and boxplots highlight trends and outliers
* Qualitative variables analyzed using frequencies and barplots
* Outlier removal ensures accurate regression modeling


## Inferential Statistics

Hypothesis testing performed:

* **Chi-squared test** for independence between hospital and delivery type → No significant relationship
* **One-sample t-tests** comparing weight and length to population means → Significant difference observed
* **T-tests** for differences by sex or maternal smoking → Only sex shows a significant effect


## Regression Model Development

Linear regression models were built incrementally:

1. **Full model** with all predictors  
2. **Reduced model** excluding non-significant predictors (maternal age, smoking, previous pregnancies)
3. **Quadratic terms** for gestation and cranium diameter tested
4. **Interaction terms** (length × gestation) explored

**Final model (mod2)** selected based on:

* Simplicity
* Adjusted R² (~0.73)
* Stepwise regression (stepAIC)
* Consistency of beta coefficients


## Model Validation

Model quality checked using:

* **Residuals analysis**: mean ~0, non-normal distribution at extremes
* **Cook distance**: identified influential points removed
* **Homoscedasticity**: Breusch-Pagan test showed heteroscedasticity
* **Residual autocorrelation**: Durbin-Watson test passed
* **Multicollinearity**: VIF < 5 for all predictors

**RMSE:** ~275 g (average prediction error)


## Prediction & Visualization

Predicted weight example:

* Female newborn, 2 previous pregnancies, 39 weeks gestation  
* Predicted weight: **3245 g**

Visualizations highlight:

* Weight trends with gestation weeks
* Differences by sex and maternal smoking


## Tech Stack

* R / RStudio
* Packages: `ggplot2`, `dplyr`, `DT`, `moments`, `RColorBrewer`, `lmtest`, `car`, `MASS`


## Conclusion

This project demonstrates how **inferential statistics** can be applied to:

* Identify variables that significantly influence neonatal weight
* Build predictive regression models
* Provide actionable insights for prenatal care planning

**Key predictors:** gestation weeks, sex, length, cranium diameter  
**Non-significant predictors:** maternal age, smoking, delivery type, hospital
