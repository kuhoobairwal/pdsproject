---
layout: default
title: Venture Capital Funding Analysis
---

# Introduction

Venture capital plays a vital role in fueling innovation, but who gets funded — and how much — remains an unequal game. This project investigates trends in VC fundraising across industries, firm types, and gender-focused funds using a dataset compiled from various sources. We explore whether company or firm characteristics can predict fundraising success.

# Data Cleaning and Exploratory Data Analysis

The raw dataset contained over 20,000 entries, which we cleaned by removing duplicate records, standardizing industry tags, and handling missing values. Key steps included:

- Dropping records with no fundraising outcome
- Standardizing fund type and gender tags
- Converting dollar values to consistent formats

### Key Insights from EDA:
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

```markdown
![EDA chart showing industry focus](assets/industry_chart.png)
