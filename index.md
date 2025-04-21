---
layout: default
title: Venture Capital Funding Analysis
---

# Introduction



# Data Cleaning and Exploratory Data Analysis

The raw dataset contained data for over 6000 funds, which was cleaned by handling missing values and standardizing existing ones. Key steps included:

- The inital datatset contained a 'Fund Open Date' column, which was used to create the newer 'Fund Age' column that stores the number of years that the VC fund has been active for. This transformation was done so that 'Fund Age' could directly  better analyse the performance of the VC fund. 
- The inital dataset contained a 'Fund Invests in Multiple Rounds' coumn, which refers to when a fund invests more money in a company that has already received funding from them. This can be a strategic move to increase their stake, protect their ownership, or support the growth of a promising startup. However, on further analysis of this column, it had missing data for 5200/6200 firms. Hence, for the lack of complete data, this this column was dropped from the final dataset.
- I did some visual analysis to better understand the distribution of some columns, and this led me to find out that some of the data was highly skewed and contained significant outliers. An example of this can be seen with the 'AUM' column which stores the Assets Under Management of a fund in millions.
<img src="AUM-boxplot.png" alt="AUM Chart 1" width="400"/>
<img src="AUM-distribution.png" alt="AUM Chart 2" width="400"/>
-  To handle extreme outliers in the AUM (Assets Under Management) variable, I applied IQR-based filtering rather than the standard three-standard-deviation rule. The AUM distribution was highly right-skewed, with a small number of funds reporting exceptionally large values that inflated both the mean and standard deviation. Using the IQR method allowed for a more robust identification of outliers based on the interquartile range, rather than being distorted by extreme values. This filtering reduced the impact of unusually large AUM values and resulted in a dataset that more accurately reflects the central tendency of most funds, improving the quality of subsequent visualizations and analysis. After cleaning the data, the resulting distribution was a lot more symmetric, as can be seen below.
<img src="aum-cleaned-boxplot.png" alt="AUM Cleaned Chart 1" width="400"/>
<img src="aum-cleaned-dist.png" alt="AUM Cleaned Chart 2" width="400"/>
-  After data cleaning steps, the total number of oobservations dropped to 4820.



###  Insights from EDA:
Doing visual analysis showed a couple different insights. 
- Most funds are focused in the US, 2377. India is a far 2nd, with 213 firms. This makes intuitive sense beacuse most of VC money is present in the US. In fact, most of VC money goes to SF-based startups! [TODO]
![Plot showing country focus](fund-country-focus.png)

- Most funds in the dataset are Early Stage funds. There are some funds that invest in a couple different stages as well. This also makes inutive sense beacuse there are lessser am9unt of funds with more money to do later stage invsting, as the later you go into the investment roudns, the hgihest the investmenet number becomes and can reach upto billions of dollars. 
![Plot showing stage ](fund-type-value-counts.png)

– This scatter plot explores the relationship between the number of funds managed by a firm and its current assets under management (AUM). Each point represents a fund, color-coded by its age.

<p align="center">
  <img src="assets/aum_vs_funds_scatter.png" alt="Scatter plot of AUM vs Number of Funds with Fund Age coloring" width="700">
</p>

We observe a **slightly positive trend** — as the number of funds increases, the AUM tends to increase as well. However, the relationship is **weak and noisy**, with a wide spread of AUM values even among firms managing a similar number of funds.

The color gradient suggests that **fund age does not strongly influence AUM**, though older funds (in yellow) are scattered throughout the range. This implies that factors beyond longevity and fund count may be more significant in driving asset accumulation.



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



