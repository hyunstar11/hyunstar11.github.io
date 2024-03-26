---
layout: custom
title: Twitter as a Crypto Barometer - Predictive Analysis of Bitcoin Price Movements 
permalink: /crypto-prediction-sentiment/
---

# Twitter as a Crypto Barometer - Predictive Analysis of Bitcoin Price Movements

[Click Here for the EDA Code](https://github.com/hyunstar11/Portfolio/blob/main/ML%26DL/DL/%EC%95%94%ED%98%B8%ED%99%94%ED%8F%90%20%ED%8A%B8%EC%9C%84%ED%84%B0%20%EA%B0%90%EC%84%B1%20%EB%B6%84%EC%84%9D%20%EB%AA%A8%EB%8D%B8/CP1_EDA.ipynb)

[Click Here for the Model Code](https://github.com/hyunstar11/Portfolio/blob/main/ML%26DL/DL/%EC%95%94%ED%98%B8%ED%99%94%ED%8F%90%20%ED%8A%B8%EC%9C%84%ED%84%B0%20%EA%B0%90%EC%84%B1%20%EB%B6%84%EC%84%9D%20%EB%AA%A8%EB%8D%B8/CP1_MODELING.ipynb)

### Executive Summary
This project explores the potential of cryptocurrency-related Twitter data as a predictor for Bitcoin price movements. By integrating sentiment analysis of Twitter discussions into the model, the study aims to develop a TradingView-like indicator that uses the "human indicator" concept to establish algorithmic trading signals. Despite the innovative approach, the model achieved an accuracy of 50-52%, suggesting that sentiment volume is correlated with price volatility but not directly predictive of price direction. The findings open avenues for future exploration in leveraging social media sentiment as a component of trading strategies.

### Introduction
**Background:** The volatile nature of the cryptocurrency market has prompted investigations into various predictors of price movements. Recent approaches have considered the potential of social media sentiment as an indicator, reflecting the broader market sentiment.

**Objective:** To evaluate the predictive power of cryptocurrency-related Twitter data on Bitcoin price movements, with a focus on developing algorithmic trading signals based on sentiment analysis.

**Significance:** Understanding the impact of market sentiment, as expressed through social media, on cryptocurrency prices could enhance trading strategies and market analysis, offering insights into the collective market psychology.

### Data Description
- **Bitcoin Price Data:** This dataset is identical to the one used in a previous project, consisting of daily Bitcoin metrics from Alpha Vantage's API.
- **Bitcoin Tweets from Kaggle:** A curated collection of 300,000 tweets related to cryptocurrency, featuring a range of attributes including content and user information.

![Screenshot 2022-08-25 10:01:33 PM](https://user-images.githubusercontent.com/90128775/186672838-1fcdb885-b793-4d3c-8155-0bce7e38ef71.png)

### Exploratory Data Analysis (EDA)
A targeted exploration of the data was conducted for the period from February 2021 to April 2022, aligning with peak cryptocurrency discussions. This analysis included word tokenization, stemming of Bitcoin-related terminologies, and sentiment analysis using the VADER tool to prepare the dataset for modeling.

### Preprocessing
- **Timeframe Selection:** The analysis was narrowed down to a dataset of approximately 10,000 tweets from a peak discussion period.
- **Text and Sentiment Analysis:** Techniques like tokenization and stemming parsed tweet content, with sentiment scores calculated using VADER to correlate with Bitcoin price movements.

![Screenshot 2022-08-25 9:53 28 PM](https://user-images.githubusercontent.com/90128775/186670076-76a8163b-67c2-45d0-97b4-1c24a779ac1f.png)

### Models
The modeling stage used sentiment analysis scores as predictors for Bitcoin price direction, treating the task as a binary classification problem. This approach sought to determine whether social media sentiment could accurately predict price increases or decreases.

<img width="1097" alt="Screenshot 2022-10-14 10:49 43 am" src="https://user-images.githubusercontent.com/90128775/195744411-6ca219c3-e6eb-4c2c-8eb1-93e4c67f748d.png">

### Model Comparison
- **Sentiment-Based Model Performance:** The model achieved an accuracy of 50-52%, indicating its predictions were no better than random chance.
- **Sentiment Volume and Price Volatility:** Analysis suggested a correlation between the volume of sentiment and price volatility, pointing towards potential trading strategies during periods of high sentiment activity.

### Key Findings
The primary finding is the correlation between sentiment volume and Bitcoin price volatility, suggesting a potential strategy for trading during high sentiment periods despite the model's inability to accurately predict price direction.

![스크린샷 2022-08-25 오후 9 37 25](https://user-images.githubusercontent.com/90128775/186669746-5486a81b-00ff-419b-8012-b93da63f81c5.png)

### Conclusions and Next Steps
Despite the initial results, the project lays the groundwork for further exploration into the use of social media sentiment in cryptocurrency trading strategies. Future work will include:

- Exploring diverse sentiment analysis tools and sources.
- Investigating advanced modeling techniques.
- Quantifying the sentiment-price relationship.
- Optimizing the model for better performance.
- Considering real-time applications for live market conditions.

This project highlights the complexities and potential of integrating social media sentiment into cryptocurrency market analysis, marking a step towards more sophisticated trading indicators.





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
Unlike the models from the previous project that used price data, this iteration incorporates cryptocurrency-related Twitter data to capture market sentiment, hypothesizing its influence on price movements. This "human indicator" concept, derived from market humor, raises the question: Can quantified sentiment data from social media predict investment trends?

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
 


