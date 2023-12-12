---
layout: custom
title: Twitter as a Crypto Barometer - Predictive Analysis of Bitcoin Price Movements 
permalink: /crypto-prediction-sentiment/
---

[Click Here for the EDA Code](https://github.com/hyunstar11/Portfolio/blob/main/ML%26DL/DL/%EC%95%94%ED%98%B8%ED%99%94%ED%8F%90%20%ED%8A%B8%EC%9C%84%ED%84%B0%20%EA%B0%90%EC%84%B1%20%EB%B6%84%EC%84%9D%20%EB%AA%A8%EB%8D%B8/CP1_EDA.ipynb)

[Click Here for the Model Code](https://github.com/hyunstar11/Portfolio/blob/main/ML%26DL/DL/%EC%95%94%ED%98%B8%ED%99%94%ED%8F%90%20%ED%8A%B8%EC%9C%84%ED%84%B0%20%EA%B0%90%EC%84%B1%20%EB%B6%84%EC%84%9D%20%EB%AA%A8%EB%8D%B8/CP1_MODELING.ipynb)


# Twitter as a Crypto Barometer - Predictive Analysis of Bitcoin Price Movements

# Table of Contents 

#### 1. Introduction
 - 1.1. Problem Statement 
 - 1.2. Description of Dataset 

#### 2. Steps 
- 2.1. Data EDA & Preprocessing 
- 2.2. Modeling & Results 

#### 3. Limitations and Next Steps 

# 1. Introduction 
### 1.1. Problem Statement
- Objective: To create a deep learning model that predicts the price direction of Bitcoin, which is like an index in the cryptocurrency market (up or down). 
  - In the previous project (Bitcoin Price Direction Prediction Model), I predicted the direction of the price based on the Bitcoin price, but this time I used cryptocurrency-related Twitter data found on Kaggle 
  - Why Twitter data? : You can often hear the term "human indicator" in the asset market; when a person buys a stock or crypto, the price of the stock or cryptocurrency drops, and this person is called a human indicator (sort of a meme). So, how can we quantify these "human indicators"? Can human metrics provide insights in investing? A thought experiment.
- I started the project with the eventual goal of creating a kind of TradingView indicator using Twitter sentiment analysis.
  - Ex). Algorithmic entry points for long/short trades based on Wave Trend, Super Trend, etc. that can be found in TradingView.  

### 1.2. Description of the dataset 
- Used **Bitcoin Tweets** data from Kaggle 
  - 300,000 tweets * 13 columns with information about the tweets (information about the user who tweeted, what they tweeted about, etc)
  - A lot of raw text data, which required some EDA & preprocessing later   
![Screenshot 2022-08-25 10:01:33 PM](https://user-images.githubusercontent.com/90128775/186672838-1fcdb885-b793-4d3c-8155-0bce7e38ef71.png)
- Used Alpha Vantage's API to get the Bitcoin price (same as in the previous project) 

# 2. Project progress 
### 2.1. Data EDA & Preprocessing 
- Setting the time period
  - Feb 2021 ~ April 2022 -> Reduced to about 10,000 Twitter data 
- Word distribution analysis after text tokenization 
  - Word tokenization to understand what is commonly mentioned in Bitcoin-related tweets
  - Stemming to remove similar words that occur repeatedly (e.g. btc, $btc, bitcoins)  
  <img width="609" alt="스크린샷 2022-08-26 오전 12 28 40" src="https://user-images.githubusercontent.com/90128775/186708844-ac81f2b9-78a4-4780-bd3b-88383bd70734.png">

- Some frequently used words include **`#bitcoin`**, **`#crypto`**, **`buy`**, **`price`**, **`@elonmusk`**,**`#eth`**, etc. 
  - In the case of Bitcoin and eth, they are categorized as big names in the crypto space, and in the case of Elon Musk, he was frequently mentioned in the crypto space due to the 'Doge Coin' and the news of Tesla's purchase of Bitcoin.  
- Applying Sentiment Analysis using VADER (Valence Aware Dictionary and sEntiment Reasoner) to Twitter data for tweet content
  - Purpose: To identify the positive, negative, and neutral stance of each individual tweet using Vader.
  - So, what is ``Vader`**?
    - A sentiment analyzer in the Natural Language Toolkit (NLTK)
    - Categorizes the content in a tweet as positive (1), negative (-1), or neutral (0). 
- What the dataset looks like after applying VADER (you can see the rating of the tweet through the 'Class' column) 
![Screenshot 2022-08-25 9:53 28 PM](https://user-images.githubusercontent.com/90128775/186670076-76a8163b-67c2-45d0-97b4-1c24a779ac1f.png)


### 2.2. Modeling 
- Predicting Bitcoin Direction via Sentiment Analysis Score 
  - Usinged
  - Proceeded with the same interval as the price-based directional prediction model performed previously (for comparison between models) 
    - Set the timeframe to February 5, 2021 - April 22, 2022 (when the project was conducted) 
    - Added a price direction (price_updown) column 
      - Set the value to '1' if the price closes higher on that date and '0' if it closes lower 
  - Approached as a binary classification problem (Activation= Sigmoid, Loss='binary_crossentropy')
    - Predicted Bitcoin price direction (price_updown) based on Sentiment (vader_neg, neu, pos, comp, class)    
<img width="1097" alt="Screenshot 2022-10-14 10:49 43 am" src="https://user-images.githubusercontent.com/90128775/195744411-6ca219c3-e6eb-4c2c-8eb1-93e4c67f748d.png">

### 2.3. Results 
- 0.5 accuracy when predicting the direction of the Bitcoin price using market sentiment  
  - This is not a significant result as it is a 50/50 chance of predicting up or down  
- However, when we observe the graph of Sentiment vs. BTC Price (based on the results of the Vader model), 	
![스크린샷 2022-08-25 오후 9 37 25](https://user-images.githubusercontent.com/90128775/186669746-5486a81b-00ff-419b-8012-b93da63f81c5.png)
  - High volume of sentiment from multiple market participants (whether positive or negative) leads to high price volatility (the more reactions, the more positive/negative/neutral).
    - This means that during periods of sentiment spikes, people who are not used to volatility / investors who are heavily leveraged in a particular direction may want to reduce their leverage. 
      - E.g. Leveraged products (like 3X), derivatives (Futures, Options, etc.)
   
# 3. Limitations and Next Steps 
- There were many things I wanted to do, but I had difficulty implementing them (early in the project, I had service development in mind - considered some kind of price query platform using DASH, but changed direction when debugging became too time-consuming)
- Future Development 
  - Consider other sentiment analysis tools besides Vader 
  - Analyze sentiment outside of Twitter (news articles, etc.. I've seen traders on twitter using news to trade) 
  - Use more modern models other than LSTM? 
    - ARIMA (good for time series prediction) 
  - Quantify the Sentiment ~ Price / Price Direction relationship
    - Make changes to make results easier to understand for people who are not familiar with DL  
  - Improve model performance 
    - Need to tune hyperparameters 
- Need to think about Real Time Application 
 


