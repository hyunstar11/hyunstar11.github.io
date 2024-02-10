---
layout: custom
title: Cryptocurrency Price Direction Prediction Model 
permalink: /crypto-direction-prediction/
---

# Cryptocurrency Price Direction Prediction Model

[Click Here for the Code](https://github.com/hyunstar11/Portfolio/blob/main/ML%26DL/DL/%EC%95%94%ED%98%B8%ED%99%94%ED%8F%90%20%EA%B0%80%EA%B2%A9%20%EB%B0%A9%ED%96%A5%EC%84%B1%20%EC%98%88%EC%B8%A1%20%EB%AA%A8%EB%8D%B8/BTC%20Price%20Direction%20Prediction%20(Price%20Driven%20Model).ipynb)

# Project Outline 

#### 1. Introduction
 - 1.1. Problem Statement
 - 1.2. Description of the dataset 

#### 2. Project Methodology
- 2.1. Data EDA & Preprocessing 
- 2.2. Modeling & Results 

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
- Developed a simple LSTM model for stationary data. 
<img width="770" alt="screenshot 2022-07-23 1 04 33 am" src="https://user-images.githubusercontent.com/90128775/180481895-59407c17-86bf-44d1-882f-815d62fb18d0.png">

#### 2.2.2.2. Second Model
- Proceeded to develop a binary clasification model.
<img width="783" alt="Screenshot taken on 2022-07-23 at 1 04 55" src="https://user-images.githubusercontent.com/90128775/180481910-f4445f92-2529-4824-97dd-0680f5d10e18.png">

### 2.2.3. Evaluation
- Through evaluation, the binary classification model demonstrated superior performance, achieving an accuracy of 0.644. Future evaluations will aim to incorporate additional metrics such as precision, recall, and F1-score for a more rounded assessment.
  
<img width="1294" alt="Screenshot 2022-07-23 AM 1 26 47" src="https://user-images.githubusercontent.com/90128775/180483039-9f4dde5a-e5ea-43cb-b154-2b73949e5a53.png">

# 3. Retrospective and Future Directions
- Reflecting on the project, further attention to the design of the deep learning model could potentially enhance its performance. Future work will explore additional model validation techniques, hyper-parameter tuning, and the potential integration of other time series modeling approaches, such as ARIMA and ETS, to compare their efficacy against LSTM models.




