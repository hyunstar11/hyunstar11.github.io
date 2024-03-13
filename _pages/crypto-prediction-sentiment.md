---
layout: custom
title: Twitter as a Crypto Barometer - Predictive Analysis of Bitcoin Price Movements 
permalink: /crypto-prediction-sentiment/
---

# Twitter as a Crypto Barometer - Predictive Analysis of Bitcoin Price Movements

[Click Here for the EDA Code](https://github.com/hyunstar11/Portfolio/blob/main/ML%26DL/DL/%EC%95%94%ED%98%B8%ED%99%94%ED%8F%90%20%ED%8A%B8%EC%9C%84%ED%84%B0%20%EA%B0%90%EC%84%B1%20%EB%B6%84%EC%84%9D%20%EB%AA%A8%EB%8D%B8/CP1_EDA.ipynb)

[Click Here for the Model Code](https://github.com/hyunstar11/Portfolio/blob/main/ML%26DL/DL/%EC%95%94%ED%98%B8%ED%99%94%ED%8F%90%20%ED%8A%B8%EC%9C%84%ED%84%B0%20%EA%B0%90%EC%84%B1%20%EB%B6%84%EC%84%9D%20%EB%AA%A8%EB%8D%B8/CP1_MODELING.ipynb)

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


**REVISING** 

# Project Outline

#### 1. Introduction
 - 1.1. Problem Statement 
 - 1.2. Description of Dataset 

#### 2. Project Methodology
- 2.1. Data EDA & Preprocessing 
- 2.2. Modeling & Results 

#### 3. Limitations and Next Steps 

# 1. Introduction 
### 1.1. Problem Statement
Unlike the models from a previous project that used price data, this iteration incorporates cryptocurrency-related Twitter data to capture market sentiment, hypothesizing its influence on price movements. This "human indicator" concept, derived from market humor, raises the question: Can quantified sentiment data from social media predict investment trends?

Aiming to develop a TradingView-like indicator, this project explores the viability of using sentiment analysis to establish algorithmic trading signals.
 
### 1.2. Description of the dataset 
- **Bitcoin Price Data**: Sourced from Alpha Vantage's API, identical to the data used in the previous project.
- **Bitcoin Tweets from Kaggle**: A collection of 300,000 tweets featuring 13 different attributes, including user information and tweet content, all related to cryptocurrency.
![Screenshot 2022-08-25 10:01:33 PM](https://user-images.githubusercontent.com/90128775/186672838-1fcdb885-b793-4d3c-8155-0bce7e38ef71.png)

# 2. Project Methodology
### 2.1. Data Exploration and Preprocessing
- **Timeframe Selection**: Focused on the period from February 2021 to April 2022, reflecting when cryptocurrency discussions peaked, reducing the dataset to around 10,000 tweets.
- **Text Analysis**: Implemented word tokenization and stemming to parse through common terminologies in Bitcoin-related tweets.
- **Sentiment Analysis with VADER**: Applied to categorize tweet sentiments, aiming to correlate this data with Bitcoin's price direction.
![Screenshot 2022-08-25 9:53 28 PM](https://user-images.githubusercontent.com/90128775/186670076-76a8163b-67c2-45d0-97b4-1c24a779ac1f.png)

### 2.2. Modeling 
The modeling stage involved:

Sentiment Scores as Predictors: Using sentiment analysis scores to predict Bitcoin price movements.
Binary Classification: The model treats the prediction task as a binary classification problem, with the Bitcoin price direction labeled as '1' for an increase and '0' for a decrease on a given day.
<img width="1097" alt="Screenshot 2022-10-14 10:49 43 am" src="https://user-images.githubusercontent.com/90128775/195744411-6ca219c3-e6eb-4c2c-8eb1-93e4c67f748d.png">

### 2.3. Results 
The sentiment-based model achieved an accuracy of 50-52% in predicting Bitcoin's price direction, indicating no better than random chance. However, analysis suggests that sentiment volume is correlated with price volatility, informing potential trading strategies for periods of high sentiment activity.

![스크린샷 2022-08-25 오후 9 37 25](https://user-images.githubusercontent.com/90128775/186669746-5486a81b-00ff-419b-8012-b93da63f81c5.png)
   
# 3. Limitations and Next Steps 
The project encountered practical limitations, such as the initial ambition to create a query platform which was set aside due to the complexity of implementation. Future work will explore:

- Diverse Sentiment Analysis Tools: To expand beyond the capabilities of VADER.
- Broader Sentiment Sources: Including news articles and other media.
- Advanced Modeling Techniques: Investigating alternatives to LSTM, such as ARIMA.
- Sentiment-Price Relationship Quantification: To improve interpretability for non-experts.
- Model Optimization: Through hyperparameter tuning and validation.
- Real-Time Application Consideration: To enhance practicality in live market conditions.
 


