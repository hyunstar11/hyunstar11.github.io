---
layout: custom
title: Sneaker Resell Price Prediction Model
permalink: /sneaker-resell-model/
---

# Sneaker Resell Price Prediction Model
Revised in November 2023

[Click Here for the Code](https://github.com/hyunstar11/Portfolio/blob/main/ML%26DL/ML/%ED%95%9C%EC%A0%95%ED%8C%90%20%EC%8B%A0%EB%B0%9C%20%EB%A6%AC%EC%85%80%EA%B0%80%20%EC%98%88%EC%B8%A1%20%EB%AA%A8%EB%8D%B8/Sneaker_ResellPred_Model_Edit.ipynb)

### Executive Summary
This project aims to predict sneaker resale prices within the burgeoning sneaker resale market, leveraging a dataset of 100,000 transactions from StockX, a resale platform in the United States. The dataset encompasses 53 limited edition models from Adidas Yeezy and Nike Off-White. Through exploratory data analysis (EDA), feature engineering, and various modeling techniques, this personal project evaluates the impact of factors such as sneaker model, release day, and color on resale prices. The ensemble model emerged as the most effective, demonstrating strong predictive capability with a focus on feature importance to guide future pricing strategies in the sneaker resale market.

### Introduction
**Background:** The sneaker resale market has experienced exponential growth, with limited edition models from brands like Adidas and Nike at the center of this phenomenon. Understanding the drivers of resale prices can offer insights for collectors, resellers, and enthusiasts.

**Objective:** To analyze and predict the resale prices of limited edition sneakers using transaction data from StockX, focusing on the influence of various features such as model, release date, and color.

**Significance:** This analysis provides a foundation for making informed decisions in the sneaker resale market, potentially benefiting buyers and sellers with data-driven insights into pricing trends.

### Data Description
The dataset comprises 100,000 transactions from StockX, including 53 limited edition sneaker models from Adidas Yeezy and Nike Off-White. The data encapsulate a wealth of information, including transaction prices, sneaker models, release dates, and buyer regions, enabling a comprehensive analysis of pricing trends.

![StockX Data](https://user-images.githubusercontent.com/90128775/184078928-c0470835-e453-448e-b325-7afa42aeeb9d.png)

### Exploratory Data Analysis (EDA) and Data Analysis
- **Data Processing Pipeline:** The dataset underwent extensive preprocessing, including date standardization, feature engineering (e.g., sneaker color, type, and region-based features), normalization of shoe size data, and conversion of price fields from strings to numerical values.
- **Analytical Insights:**
  - Price Premium Over Time: Analysis revealed an increasing trend in resale premiums over time.
  - Shoe Size Impact on Resale Value: Contrary to expectations, shoe size showed little correlation with resale value, underscoring the minimal influence of size on pricing.

### Modeling & Selection
- **Model Development:** The study progressed from a baseline model to more sophisticated models like Linear Regression, Random Forest, XGBoost, LightGBM, and an Ensemble Model, focusing on model performance and generalization capability.
- **Model Performance:** The Ensemble Model outperformed others, showcasing strong predictive accuracy and generalization, evidenced by lower mean absolute error (MAE) in cross-validation.

![스크린샷 2023-11-12 오후 11 58 40](https://github.com/hyunstar11/Portfolio/assets/90128775/b74de6d6-297d-4114-8a1f-671854fa879e)

### Feature Importance
Analysis highlighted 'airjordan', 'Release Day', and 'yeezy350' as significant predictors of resale prices, indicating the critical role of sneaker model and release timing in determining market value.

![Feature Importance](https://github.com/hyunstar11/hyunstar11.github.io/assets/90128775/acd3c069-f267-49bc-9ac6-cc59f2b90be2)

### Interpreting Coefficients (PDP Plot)
Partial Dependence Plots (PDP) further elucidated the relationship between key features and resale prices, offering nuanced insights into how specific attributes influence pricing in the resale market.

![PDP Plot_Jordan](https://github.com/hyunstar11/hyunstar11.github.io/assets/90128775/1a6abc97-50a4-4ada-a733-a35cba9c2a1d)

![PDP_ReleaseDate](https://github.com/hyunstar11/hyunstar11.github.io/assets/90128775/f86ffcb7-8ae3-41ec-a53b-2c6c20bd3dd0)

### Conclusions and Next Steps
The project provides valuable insights into the sneaker resale market, identifying key factors that influence resale prices. The successful application of an Ensemble Model demonstrates the potential of machine learning in predicting market trends. Future work could explore:

- Integration of additional data sources for a more holistic analysis.
- Deployment of the predictive model for real-time price forecasting.
- Exploration of other limited edition items to generalize the model's applicability.

This study not only advances the understanding of the sneaker resale market but also opens avenues for applying similar methodologies to other markets, enhancing the predictive capabilities of economic models in various domains.
