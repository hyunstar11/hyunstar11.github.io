---
layout: custom
title: Cryptocurrency Price Direction Prediction Model 
permalink: /crypto-direction-prediction/
---

# Cryptocurrency Price Direction Prediction Model

[Click Here for the EDA Code](https://github.com/hyunstar11/Portfolio/tree/main/ML%26DL/DL/%EC%95%94%ED%98%B8%ED%99%94%ED%8F%90%20%EA%B0%80%EA%B2%A9%20%EB%B0%A9%ED%96%A5%EC%84%B1%20%EC%98%88%EC%B8%A1%20%EB%AA%A8%EB%8D%B8)

# Project Outline 

#### 1. Introduction
 - 1.1. Problem Statement
 - 1.2. Description of the dataset 

#### 2. Project Steps  
- 2.1. Data EDA & Preprocessing 
- 2.2. Modeling & Results 

#### 3. Reflection 

# 1. Introduction 
### 1.1. Problem Statement
- Purpose: To create a model that predicts the price direction (up or down) of bitcoin, which is an index in the cryptocurrency market
  - Stock price/bitcoin prediction models commonly found on the internet are prone to summation of processes 
    - Why?: Because they use non-stationary data instead of stationary data 
  - Problem : Can we create a model that helps us with trading/investment decisions based on data (price) to minimize FOMO and make data-driven decisions? 

### 1.2. Description of the dataset 
- I used Alpha Vantage's API to get daily Bitcoin price data (Open, Low, Close, Volume) 

# 2. Project Steps 
### 2.1. Data EDA & Preprocessing 
- Time period: Data from January 2021 to April 2022, when I was working on the project. 
  - Rationale for the Time period selection: Significant institutional buying of Bitcoin starting in 2021 (e.g. Tesla, Fidelity Investments, Nexon, etc.) 
- Preprocessed closing prices for binary classification models: changed to 1 for positive closes and 0 for negative closes   
- Converting data from non-stationary to stationary (today's price - previous day's price) 
  - Why Stationary data? - Data with constant mean, covariance -> better for creating predictive models
- Preprocessing of Closing Prices for Binary Classification Models: For simplicity, closing prices were processed into a binary format, where a **positive** close is represented as 1 and a **negative** close as 0. This binary representation is aimed at facilitating the classification task in the predictive models.
- Converting Data from Non-Stationary to Stationary: I transformed the data to a stationary format by calculating the difference between the current day’s price and the previous day’s price.
- Importance of Stationary Data: Stationarity in time series data, characterized by constant statistical properties like mean and covariance, is crucial for the effectiveness of many predictive models. Stationary data tends to be more predictable and its consistency allows for more reliable statistical inference. This is particularly important for models that are based on the assumption of stationarity, such as ARIMA. While not all models require stationary data, converting to a stationary format often simplifies the analysis and helps in avoiding misleading results due to spurious correlations in non-stationary data. However, it’s important to approach this transformation judiciously, as it can sometimes lead to the loss of important information or introduce other complexities.

### 2.2. Modeling & Results 

- To predict the price direction of Bitcoin 1). Develop a price prediction model with stationary data 2). Developed a price prediction model using binary classification 
- Normalized the data (converted to 0~1) to increase the performance of the model 
  - View several days of data and set a window 
- Use LSTM by default
  - What is LSTM: Passing on some of the previous data information to the next analysis 
  - Why use it?: Appropriate for time series data 

- 2.2.1. The first model 
  - LSTM model for stationary data 
<img width="770" alt="screenshot 2022-07-23 1 04 33 am" src="https://user-images.githubusercontent.com/90128775/180481895-59407c17-86bf-44d1-882f-815d62fb18d0.png">

- 2.2.2. Second Model 
  - Proceed to binary classification
<img width="783" alt="Screenshot taken on 2022-07-23 at 1 04 55" src="https://user-images.githubusercontent.com/90128775/180481910-f4445f92-2529-4824-97dd-0680f5d10e18.png">

- 2.2.3. Evaluation 
<img width="1294" alt="Screenshot 2022-07-23 AM 1 26 47" src="https://user-images.githubusercontent.com/90128775/180483039-9f4dde5a-e5ea-43cb-b154-2b73949e5a53.png">

- After evaluation, we concluded that the binary classification model performed better (0.644 accuracy) 


# 3. Retrospective and future development  
- If we had more time, we could pay more attention to the design of the deep learning model and expect better performance. 
- Additional model validation and hyper-parameter tuning 
- Try modeling with other models other than LSTM, such as ARIMA and ETS, which are known to be suitable for time series data.


