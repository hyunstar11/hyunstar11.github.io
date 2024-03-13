---
layout: custom
title: Cryptocurrency Price Direction Prediction Model 
permalink: /crypto-direction-prediction/
---

# Cryptocurrency Price Direction Prediction Model

[Click Here for the Code](https://github.com/hyunstar11/Portfolio/blob/main/ML%26DL/DL/%EC%95%94%ED%98%B8%ED%99%94%ED%8F%90%20%EA%B0%80%EA%B2%A9%20%EB%B0%A9%ED%96%A5%EC%84%B1%20%EC%98%88%EC%B8%A1%20%EB%AA%A8%EB%8D%B8/BTC%20Price%20Direction%20Prediction%20(Price%20Driven%20Model).ipynb)

*REVISING*

# Executive Summary 
This project focuses on developing a predictive model for Bitcoin price movements, specifically aiming to forecast the directional change (up or down) of Bitcoin prices. By utilizing stationary data, which maintains consistent statistical properties over time, the project seeks to overcome the common challenge of inaccurate forecasts due to non-stationary data in cryptocurrency prediction models. The methodology involves data preprocessing to ensure stationarity, followed by the development of LSTM models for both price prediction and directional movement classification. The evaluation of these models revealed that the first model, which predicts actual prices, performs better, offering lower losses and more accurate predictions. This research aims to contribute to the field by demonstrating the potential for more reliable cryptocurrency trading strategies that minimize the influence of market sentiments like FOMO.

# Introduction
Background: Cryptocurrency markets are notoriously volatile, making accurate price prediction a challenging but critical task. Traditional examples that can be found on the web often struggle due to the non-stationary nature of data, which can lead to unreliable forecasts.

# Objective
The primary goal is to develop a predictive model that accurately forecasts the directional movement of Bitcoin prices using stationary data, aiming to improve investment and trading decisions in the cryptocurrency market.

# Significance
This project is significant as it attempts to address the challenges of predicting cryptocurrency prices with a novel approach, potentially serving as a more reliable guide for traders and investors to navigate the volatile Bitcoin market.

# Data Description
The dataset for this project includes daily Bitcoin price metrics (Open, Low, Close, Volume) obtained from Alpha Vantage's API, covering the period from January 2021 to April 2022. This period was selected due to significant institutional investments in Bitcoin, enhancing the dataset's relevance for predictive modeling purposes.

# Exploratory Data Analysis (EDA)
Initial exploration of the Bitcoin price dataset was conducted to understand the data's characteristics, including trends, patterns, and potential anomalies. This phase aimed to identify key features that could influence the predictive models' accuracy.

# Preprocessing
The preprocessing phase involved several critical steps to prepare the data for modeling:

- Binary Classification Preparation: The closing prices were categorized into 1 (positive close) or 0 (negative close) to enable binary classification.
- Stationarity Transformation: The dataset was converted to a stationary format by calculating daily price changes. This transformation was essential for enhancing the models' predictability by ensuring consistent statistical properties over time.

<img width="801" alt="스크린샷 2022-07-23 오전 1 47 29" src="https://user-images.githubusercontent.com/90128775/180486557-abb9ddaa-c830-42a5-a495-9cfd80ee41b6.png">

# Models
**Model Development:**
- The modeling process began with the development of a simple LSTM model to predict actual Bitcoin prices based on stationary data.
Subsequently, a binary classification LSTM model was developed to forecast the direction of Bitcoin price movements.

<img width="770" alt="screenshot 2022-07-23 1 04 33 am" src="https://user-images.githubusercontent.com/90128775/180481895-59407c17-86bf-44d1-882f-815d62fb18d0.png">

<img width="783" alt="Screenshot taken on 2022-07-23 at 1 04 55" src="https://user-images.githubusercontent.com/90128775/180481910-f4445f92-2529-4824-97dd-0680f5d10e18.png">

**Model Evaluation:**
- The models were evaluated based on their performance metrics, with the first model showing superiority through lower losses and better accuracy in predicting Bitcoin prices.

<img width="1294" alt="Screenshot 2022-07-23 AM 1 26 47" src="https://user-images.githubusercontent.com/90128775/180483039-9f4dde5a-e5ea-43cb-b154-2b73949e5a53.png">

# Model Comparison
The comparison between the two developed models highlighted the first model's effectiveness in accurately predicting Bitcoin prices, demonstrating its potential utility for trading strategies that rely on price forecasts.

# Key Findings
The main finding from this project is the effectiveness of using stationary data in improving the accuracy of predictive models for Bitcoin price movements. The LSTM model that predicts actual prices outperforms the binary classification model, suggesting that focusing on price predictions might be more beneficial for traders and investors.

# Conclusions and Next Steps
This project demonstrates the potential of using stationary data and LSTM models for predicting Bitcoin prices. While the first model showed promising results, there is room for further exploration and improvement. Future directions could include refining the LSTM models, exploring additional data preprocessing techniques, and incorporating other forms of stationary data to enhance model performance. Additionally, extending the research to include other cryptocurrencies and comparing the effectiveness of different modeling approaches would provide valuable insights into the broader applicability of the methodology.

# Project Outline 

#### 1. Introduction
 - 1.1. Problem Statement
 - 1.2. Description of the dataset 

#### 2. Project Methodology
- 2.1. Data EDA & Preprocessing 
- 2.2. Modeling and Evaluation

#### 3. Retrospective and Future Directions

# 1. Introduction 
### 1.1. Problem Statement
- The goal of this project is to develop a model that accurately predicts the directional movement (up or down) of Bitcoin prices, addressing a common issue in stock and cryptocurrency prediction models: their reliance on non-stationary data, which often leads to inaccurate forecasts. By focusing on stationary data, this project aims to create a more reliable model that supports trading and investment decisions, helping to minimize the influence of FOMO (Fear Of Missing Out) and encouraging data-driven strategies.

### 1.2. Description of the dataset 
- The dataset comprises daily Bitcoin price metrics (Open, Low, Close, Volume), sourced from Alpha Vantage's API. This dataset spans from January 2021 to April 2022, a period chosen due to significant institutional investments in Bitcoin, enhancing the dataset's relevance for predictive modeling.

# 2. Project Methodology
### 2.1. Data Exploration and Preprocessing
The data preprocessing stage involved:

- Binary Classification Preparation: Closing prices were categorized into 1 (positive close) or 0 (negative close) to facilitate binary classification in the predictive models.
- Stationarity Transformation: To ensure model accuracy, the dataset was converted to a stationary format by calculating daily price changes (current day’s price minus previous day’s price). This approach was crucial for maintaining consistent statistical properties, such as mean and covariance, in the dataset, thereby enhancing the predictability required for effective modeling.

<img width="801" alt="스크린샷 2022-07-23 오전 1 47 29" src="https://user-images.githubusercontent.com/90128775/180486557-abb9ddaa-c830-42a5-a495-9cfd80ee41b6.png">

### 2.2. Modeling and Evaluation

#### 2.2.1. Approach 
The modeling process involved two primary steps: 
- 1. Developing a model based on stationary data
- 2. Implementing a binary classification model to predict price direction

### 2.2.2. Model Details
- Normalization: Data was normalized to a 0-1 range to optimize model performance
- LSTM Usage: Given its efficacy in handling time series data, LSTM (Long Short-Term Memory) was chosen as the primary modeling technique. LSTM models are particularly adept at preserving historical information, making them ideal for our predictive task.

#### 2.2.2.1. First Model 
- Developed a simple LSTM model for stationary data to predict the actual price.
<img width="770" alt="screenshot 2022-07-23 1 04 33 am" src="https://user-images.githubusercontent.com/90128775/180481895-59407c17-86bf-44d1-882f-815d62fb18d0.png">

#### 2.2.2.2. Second Model
- Instead of predicitng the actual price, I proceeded to develop a binary clasification model to predict the direction of the Bitcoin Price. 
<img width="783" alt="Screenshot taken on 2022-07-23 at 1 04 55" src="https://user-images.githubusercontent.com/90128775/180481910-f4445f92-2529-4824-97dd-0680f5d10e18.png">

### 2.2.3. Evaluation
- The **first** model appears to be the better performing model as it has much **lower losses** in both training and validation. The evaluation metrics further support this conclusion with a lower loss and MSE.
<img width="1294" alt="Screenshot 2022-07-23 AM 1 26 47" src="https://user-images.githubusercontent.com/90128775/180483039-9f4dde5a-e5ea-43cb-b154-2b73949e5a53.png">

# 3. Retrospective and Future Directions
- Reflecting on the project, further attention to the design of the deep learning model could potentially enhance its performance. Future work will explore additional model validation techniques, hyper-parameter tuning, and the potential integration of other time series modeling approaches, such as ARIMA and ETS, to compare their efficacy against LSTM models.




