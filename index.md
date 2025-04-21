---
layout: default
title: Venture Capital Funding Analysis
---

# Introduction



# Data Cleaning and Exploratory Data Analysis

The raw dataset contained data for over 6000 funds, which was cleaned by handling missing values and standardizing existing ones. Key steps included:

- The inital datatset contained a 'Fund Open Date' column, which was used to create the newer 'Fund Age' column that stores the number of years that the VC fund has been active for. This transformation was done so that 'Fund Age' could directly  better analyse the performance of the VC fund. 
- The inital dataset contained a 'Fund Invests in Multiple Rounds' coumn, which refers to when a fund invests more money in a company that has already received funding from them. This can be a strategic move to increase their stake, protect their ownership, or support the growth of a promising startup. However, on further analysis of this column, it had missing data for 5200/6200 firms. Hence, for the lack of complete data, this this column was dropped from the final dataset.
- The initial dataset contained a 'Fund Status' column, which had 4 possible values, "Investing", "Divesting", "Raising" or "Liquidated". In fund management, investing means acquiring assets, divesting means selling existing assets, raising refers to acquiring new capital from investors and liquidating means shutting down the fund and selling all remaining assets. I created a numerical mapping for each of their 4 values for ease of analysis later in the project.
- I did some visual analysis to better understand the distribution of some columns, and this led me to find out that some of the data was highly skewed and contained significant outliers. An example of this can be seen with the 'AUM' column which stores the Assets Under Management of a fund in millions.
<img src="AUM-boxplot.png" alt="AUM Chart 1" width="400"/>
<img src="AUM-distribution.png" alt="AUM Chart 2" width="400"/>
-  To handle extreme outliers in the AUM (Assets Under Management) variable, I applied IQR-based filtering rather than the standard three-standard-deviation rule. The AUM distribution was highly right-skewed, with a small number of funds reporting exceptionally large values that inflated both the mean and standard deviation. Using the IQR method allowed for a more robust identification of outliers based on the interquartile range, rather than being distorted by extreme values. This filtering reduced the impact of unusually large AUM values and resulted in a dataset that more accurately reflects the central tendency of most funds, improving the quality of subsequent visualizations and analysis. After cleaning the data, the resulting distribution was a lot symmetric, as can be seen below. ![AUM Cleaned boxplot](aum-cleaned-boxplot.png)  ![AUM Cleaned distribution](aum-cleaned-dist.png)



###  Insights from EDA:
![AUM boxplot showing industry focus](AUM-boxplot.png)


- Most funds are concentrated in the US and Europe.
- Women-focused funds manage more funds per firm but raise less capital on average.
- Industry focus is skewed towards healthcare, fintech, and consumer sectors.

# Framing a Prediction Problem

We posed the following question:  
**Can we predict how much capital a fund will raise based on its characteristics (industry, type, region, etc.)?**

We treated this as a **regression problem**, where the target variable is `Fund Amount Raised`, and predictors include:

- Fund Type
- Number of Funds per Firm
- Industry Focus
- Region
- Gender/Impact Focus

# Baseline Model

Our baseline model was a simple **mean predictor**, where every fund was assumed to raise the same amount — the overall average. This allowed us to benchmark performance.

### Baseline RMSE:
`$XX.XX million`  
*(Fill this in with your value)*

# Final Model

Our final model used a **Random Forest Regressor** trained on engineered features such as log-transformed fund size and encoded industry focus. We tuned hyperparameters using cross-validation and reduced overfitting through pruning and feature selection.

### Final RMSE:
`$XX.XX million`  
*(Add your model performance here)*

### Feature Importance:
- `Industry` and `Fund Type` had the strongest predictive power
- Gender-focused funds had slightly lower predicted outcomes, matching real-world disparities

---

You can add images or charts in each section like this:


![EDA chart showing industry focus](AUM-boxplot.png)
![AUM boxplot showing industry focus](AUM-distribution.png)
<img src="AUM-boxplot.png" alt="AUM Chart 1" width="600"/>
<img src="AUM-distribution.png" alt="AUM Chart 2" width="600"/>



