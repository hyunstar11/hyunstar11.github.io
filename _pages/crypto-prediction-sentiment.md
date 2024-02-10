---
layout: custom
title: Twitter as a Crypto Barometer - Predictive Analysis of Bitcoin Price Movements 
permalink: /crypto-prediction-sentiment/
---

# Twitter as a Crypto Barometer - Predictive Analysis of Bitcoin Price Movements

[Click Here for the EDA Code](https://github.com/hyunstar11/Portfolio/blob/main/ML%26DL/DL/%EC%95%94%ED%98%B8%ED%99%94%ED%8F%90%20%ED%8A%B8%EC%9C%84%ED%84%B0%20%EA%B0%90%EC%84%B1%20%EB%B6%84%EC%84%9D%20%EB%AA%A8%EB%8D%B8/CP1_EDA.ipynb)

[Click Here for the Model Code](https://github.com/hyunstar11/Portfolio/blob/main/ML%26DL/DL/%EC%95%94%ED%98%B8%ED%99%94%ED%8F%90%20%ED%8A%B8%EC%9C%84%ED%84%B0%20%EA%B0%90%EC%84%B1%20%EB%B6%84%EC%84%9D%20%EB%AA%A8%EB%8D%B8/CP1_MODELING.ipynb)

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
- Predicting Bitcoin Direction via Sentiment Analysis Score 
  - Usinged
  - Proceeded with the same interval as the price-based directional prediction model performed previously (for comparison between models) 
    - Set the timeframe to February 5, 2021 - April 22, 2022 (when the project was conducted) 
    - Added a price direction (price_updown) column 
      - Set the value to '1' if the price closes higher on that date and '0' if it closes lower 
  - Approached as a binary classification problem (Activation= Sigmoid, Loss='binary_crossentropy')
    - Predicted Bitcoin price direction (price_updown) based on Sentiment (VADER_neg, neu, pos, comp, class)    
<img width="1097" alt="Screenshot 2022-10-14 10:49 43 am" src="https://user-images.githubusercontent.com/90128775/195744411-6ca219c3-e6eb-4c2c-8eb1-93e4c67f748d.png">

### 2.3. Results 
- 0.5 accuracy when predicting the direction of the Bitcoin price using market sentiment  
  - This is not a significant result as it is a 50/50 chance of predicting up or down  
- However, when we observe the graph of Sentiment vs. BTC Price (based on the results of the VADER model), 	
![스크린샷 2022-08-25 오후 9 37 25](https://user-images.githubusercontent.com/90128775/186669746-5486a81b-00ff-419b-8012-b93da63f81c5.png)
  - High volume of sentiment from multiple market participants (whether positive or negative) leads to high price volatility (the more reactions, the more positive/negative/neutral).
    - This means that during periods of sentiment spikes, people who are not used to volatility / investors who are heavily leveraged in a particular direction may want to reduce their leverage. 
      - E.g. Leveraged products (like 3X), derivatives (Futures, Options, etc.)
   
# 3. Limitations and Next Steps 
- There were many things I wanted to do, but I had difficulty implementing them (early in the project, I had service development in mind - considered some kind of price query platform using DASH, but changed direction when debugging became too time-consuming)
- Future Development 
  - Consider other sentiment analysis tools besides VADER 
  - Analyze sentiment outside of Twitter (news articles, etc.. I've seen traders on twitter using news to trade) 
  - Use more modern models other than LSTM? 
    - ARIMA (good for time series prediction) 
  - Quantify the Sentiment ~ Price / Price Direction relationship
    - Make changes to make results easier to understand for people who are not familiar with DL  
  - Improve model performance 
    - Need to tune hyperparameters 
- Need to think about Real Time Application 
 


